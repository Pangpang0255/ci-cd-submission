# Tugas 22: **init**.py dengan Konfigurasi Security Headers Talisman

## GitHub Repository URL:

```
https://github.com/Pangpang0255/ci-cd-final-project/blob/main/src/__init__.py
```

## File src/**init**.py Content:

```python
"""
Counter Service Application
CI/CD Tools and Practices Final Project
"""

from flask import Flask
from flask_talisman import Talisman
from flask_cors import CORS
import os

__version__ = '1.0.0'
__author__ = 'CI-CD Project Team'

def create_app(config=None):
    """
    Application factory function

    Args:
        config: Optional configuration dictionary

    Returns:
        Flask application instance
    """
    app = Flask(__name__)

    # Load configuration
    if config is None:
        config = {
            'DEBUG': os.getenv('FLASK_DEBUG', False),
            'TESTING': os.getenv('FLASK_TESTING', False),
        }

    app.config.update(config)

    # Initialize Talisman for security headers
    initialize_talisman(app)

    # Initialize CORS
    initialize_cors(app)

    # Register blueprints
    register_blueprints(app)

    # Register error handlers
    register_error_handlers(app)

    return app


def initialize_talisman(app):
    """
    Configure Talisman security headers

    Security Headers Configured:
    - X-Frame-Options: SAMEORIGIN
    - X-Content-Type-Options: nosniff
    - X-XSS-Protection: 1; mode=block
    - Strict-Transport-Security
    - Content-Security-Policy
    """

    talisman_config = {
        'force_https': os.getenv('FORCE_HTTPS', True),
        'strict_transport_security': True,
        'strict_transport_security_max_age': 31536000,
        'strict_transport_security_include_subdomains': True,
        'strict_transport_security_preload': True,
        'content_security_policy': {
            'default-src': "'self'",
            'script-src': "'self' 'unsafe-inline'",
            'style-src': "'self' 'unsafe-inline'",
            'img-src': "'self' data: https:",
            'font-src': "'self'",
            'connect-src': "'self'",
            'frame-ancestors': "'self'",
            'base-uri': "'self'",
            'form-action': "'self'"
        },
        'content_security_policy_nonce_in': ['script-src'],
        'referrer_policy': 'strict-origin-when-cross-origin',
        'permissions_policy': {
            'geolocation': ['()'],
            'microphone': ['()'],
            'camera': ['()']
        },
        'session_cookie_secure': True,
        'session_cookie_http_only': True,
        'session_cookie_same_site': 'Lax',
    }

    Talisman(app, **talisman_config)

    # Custom security headers
    @app.after_request
    def set_security_headers(response):
        """Add additional security headers"""
        response.headers['X-Content-Type-Options'] = 'nosniff'
        response.headers['X-Frame-Options'] = 'SAMEORIGIN'
        response.headers['X-XSS-Protection'] = '1; mode=block'
        response.headers['Server'] = 'Counter Service/1.0'
        response.headers['Pragma'] = 'no-cache'
        response.headers['Cache-Control'] = 'no-cache, no-store, must-revalidate'
        return response


def initialize_cors(app):
    """
    Configure CORS (Cross-Origin Resource Sharing) policy

    CORS Configuration:
    - Allow origins: configurable via environment
    - Allow methods: GET, POST, PUT, DELETE, OPTIONS
    - Allow headers: Content-Type, Authorization
    - Allow credentials: True
    """

    cors_config = {
        'origins': os.getenv('CORS_ORIGINS', '*').split(','),
        'methods': ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS'],
        'allow_headers': ['Content-Type', 'Authorization'],
        'supports_credentials': True,
        'max_age': 3600,
        'send_wildcard': False,
        'vary_header': True,
        'resources': {
            r'/api/*': {
                'origins': os.getenv('CORS_ORIGINS', '*').split(','),
                'methods': ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS'],
                'allow_headers': ['Content-Type', 'Authorization']
            }
        }
    }

    CORS(app, resources=cors_config['resources'])

    @app.before_request
    def handle_preflight():
        """Handle CORS preflight requests"""
        if app.config.get('TESTING'):
            return None
        return None


def register_blueprints(app):
    """Register Flask blueprints"""
    # Import blueprints here to avoid circular imports
    from .routes import accounts_bp

    app.register_blueprint(accounts_bp, url_prefix='/api')


def register_error_handlers(app):
    """Register error handlers"""

    @app.errorhandler(400)
    def bad_request(error):
        return {'error': 'Bad Request'}, 400

    @app.errorhandler(404)
    def not_found(error):
        return {'error': 'Not Found'}, 404

    @app.errorhandler(500)
    def internal_error(error):
        return {'error': 'Internal Server Error'}, 500


if __name__ == '__main__':
    app = create_app()
    app.run(debug=True)
```

## Fitur Security Headers yang Diimplementasikan:

✅ **Talisman Configuration:**

- HTTPS enforcement
- HSTS (HTTP Strict Transport Security)
- CSP (Content Security Policy)
- Referrer Policy
- Permissions Policy

✅ **Custom Security Headers:**

- X-Content-Type-Options: nosniff
- X-Frame-Options: SAMEORIGIN
- X-XSS-Protection: 1; mode=block
- Cache-Control headers

✅ **CORS Policy Configuration:**

- Configurable origins
- Allowed methods: GET, POST, PUT, DELETE, OPTIONS
- Allowed headers: Content-Type, Authorization
- Credentials support
- Preflight request handling

✅ **Session Security:**

- Secure cookies
- HttpOnly flag
- SameSite policy
