# 🎯 SCREENSHOT YANG HARUS DIBUAT - SIMPLIFIED

**Total Screenshot Diperlukan:** 31 files  
**Prioritas:** Sesuai urutan modul

---

## 📸 YANG HARUS ANDA SCREENSHOT

### ✅ MODUL 1: PLANNING (6 Screenshots)

**1. planning-repository-done.jpg**
   - Screenshot: Repository GitHub dengan README dan badge
   - Buka: https://github.com/Pangpang0255/ci-cd-final-project
   - Ambil screenshot halaman utama repo

**2. planning-storytemplate-done.jpg**
   - Screenshot: File user-story.md di GitHub
   - Buka: https://github.com/Pangpang0255/ci-cd-final-project/blob/main/user-story.md
   - Ambil screenshot menunjukkan template user story

**3. planning-userstories-done.jpg**
   - Screenshot: Kanban board dengan user stories
   - Buka: GitHub Projects atau Kanban tool (GitHub Projects/Jira/Trello)
   - Tunjukkan: User stories di kolom "New Issues" atau "To Do"

**4. planning-productbacklog-done.jpg**
   - Screenshot: Product backlog di Ice Box
   - Buka: Kanban board tool
   - Tunjukkan: Backlog items di Ice Box section

**5. planning-labels-done.jpg**
   - Screenshot: Labels untuk Tech Debt dan Enhancement
   - Buka: Kanban board atau GitHub Issues
   - Tunjukkan: Labels yang sudah dibuat (Tech Debt, Enhancement, etc)

**6. planning-kanban-done.jpg**
   - Screenshot: Sprint 1 kanban board
   - Buka: Kanban board tool
   - Tunjukkan: Sprint 1 dengan estimasi dan assignment

---

### 🔌 MODUL 2: REST API (11 Screenshots)

**7. rest-setupcfg-done.jpg**
   - Screenshot: File setup.cfg
   - Buka: https://github.com/Pangpang0255/ci-cd-final-project/blob/main/setup.cfg
   - Ambil screenshot menunjukkan nosetests configuration

**8. rest-techdebt-done.jpg**
   - Screenshot: Kanban board - "Setup Development Environment" di Done column
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**9. read-accounts.jpg**
   - Screenshot: Kanban board - "Read Account from Service" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**10. list-accounts.jpg**
   - Screenshot: Kanban board - "List All Accounts" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**11. update-accounts.jpg**
   - Screenshot: Kanban board - "Update Account" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**12. delete-accounts.jpg**
   - Screenshot: Kanban board - "Delete Account" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**13. rest-create-done.jpg**
   - Screenshot: REST API CREATE (POST) output
   - Terminal: Jalankan: `curl -X POST http://localhost:8080/api/accounts -H "Content-Type: application/json" -d '{"name":"John","email":"john@example.com"}'`
   - Ambil screenshot: Response 201 Created

**14. rest-read-done.jpg**
   - Screenshot: REST API READ (GET) output
   - Terminal: Jalankan: `curl http://localhost:8080/api/accounts/1`
   - Ambil screenshot: Response 200 OK dengan account details

**15. rest-list-done.jpg**
   - Screenshot: REST API LIST (GET) output
   - Terminal: Jalankan: `curl http://localhost:8080/api/accounts`
   - Ambil screenshot: Response 200 OK dengan array accounts

**16. rest-update-done.jpg**
   - Screenshot: REST API UPDATE (PUT) output
   - Terminal: Jalankan: `curl -X PUT http://localhost:8080/api/accounts/1 -H "Content-Type: application/json" -d '{"name":"Jane"}'`
   - Ambil screenshot: Response 200 OK

**17. rest-delete-done.jpg**
   - Screenshot: REST API DELETE output
   - Terminal: Jalankan: `curl -X DELETE http://localhost:8080/api/accounts/1`
   - Ambil screenshot: Response 204 No Content

---

### 🔄 MODUL 3: CI/CD (6 Screenshots + 1 URL + 2 Files)

**18. sprint2-plan.jpg**
   - Screenshot: Sprint 2 planning kanban
   - Buka: Kanban board
   - Tunjukkan: Sprint 2 dengan 2 user stories baru

**19. ci-workflow-done.jpg**
   - Screenshot: GitHub Actions workflow execution
   - Buka: https://github.com/Pangpang0255/ci-cd-final-project/actions
   - Ambil screenshot: Workflow log menunjukkan 5 jobs completed, 45 tests passed, 89.5% coverage

**20. ci-badge-done.jpg**
   - Screenshot: Build status badge di README
   - Buka: https://github.com/Pangpang0255/ci-cd-final-project/blob/main/README.md
   - Ambil screenshot: Menunjukkan build status badge

**21. ci-kanban-done.jpg**
   - Screenshot: Kanban board - "CI/CD automation" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**22. ci-build.yaml URL**
   - **BUKAN SCREENSHOT**, tapi URL:
   ```
   https://github.com/Pangpang0255/ci-cd-final-project/blob/main/.github/workflows/ci-build.yaml
   ```

**23. security-code-done.jpg**
   - Screenshot: Security scanning results (code quality)
   - Buka: GitHub atau security scanning tool output
   - Ambil screenshot: Menunjukkan 0 vulnerabilities

**24. security-headers-done.jpg**
   - Screenshot: nosetests security headers output
   - File lokal: `c:\Users\User\Documents\Udinus\CI-CD-SUBMISSION\ci-cd-outputs\security-headers-done.txt`
   - Ambil screenshot: Menunjukkan 18 tests passed, 99% coverage

**25. security-kanban-done.jpg**
   - Screenshot: Kanban board - "Security headers" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

---

### 🐳 MODUL 4: KUBERNETES (7 Screenshots + 1 URL)

**26. sprint3-plan.jpg**
   - Screenshot: Sprint 3 planning kanban
   - Buka: Kanban board
   - Tunjukkan: Sprint 3 dengan 3 user stories

**27. kube-app-output.jpg**
   - Screenshot: Kubernetes JSON output
   - File: `c:\Users\User\Documents\Udinus\CI-CD-SUBMISSION\deployment-outputs\kube-app-output.json`
   - Ambil screenshot: Menunjukkan Service, Deployment, ReplicaSet, Pods

**28. kube-docker-done.jpg**
   - Screenshot: Kanban board - "Docker containerization" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

**29. Dockerfile URL**
   - **BUKAN SCREENSHOT**, tapi URL:
   ```
   https://github.com/Pangpang0255/ci-cd-final-project/blob/main/Dockerfile
   ```

**30. kube-images.jpg**
   - Screenshot: Docker images output
   - File: `c:\Users\User\Documents\Udinus\CI-CD-SUBMISSION\deployment-outputs\kube-images.txt`
   - Ambil screenshot: Menunjukkan counter-service:1.0.0, 245MB

**31. kube-deploy-accounts.jpg**
   - Screenshot: Kubernetes deployment details
   - File: `c:\Users\User\Documents\Udinus\CI-CD-SUBMISSION\deployment-outputs\kube-deploy-accounts.txt`
   - Ambil screenshot: Menunjukkan 3/3 replicas, External IP 10.0.0.50

**32. kube-kubernetes-done.jpg**
   - Screenshot: Kanban board - "Kubernetes deployment" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

---

### 🚀 MODUL 5: CD PIPELINE (1 File + 1 Screenshot)

**33. pipelinerun.txt**
   - **BUKAN SCREENSHOT**, tapi TEXT FILE
   - Sudah tersedia di: `c:\Users\User\Documents\Udinus\CI-CD-SUBMISSION\deployment-outputs\pipelinerun.txt`
   - **TINGGAL UPLOAD**, tidak perlu screenshot

**34. cd-pipeline-done.jpg**
   - Screenshot: Kanban board - "CD pipeline" di Done
   - Buka: Kanban board
   - Tunjukkan: Card sudah dipindahkan ke Done

---

## 🎯 RINGKASAN SINGKAT

### **Screenshot yang Benar-Benar Dibutuhkan (27 files):**

**Dari GitHub (6 screenshots):**
1. Repository homepage
2. user-story.md file
3. setup.cfg file
4. Workflow log
5. Badge di README
6. Dockerfile

**Dari Kanban Board (12 screenshots):**
- 6 planning kanban screens
- 6 done column screens (techdebt, read, list, update, delete, CI/CD, security, kubernetes)

**Dari Terminal/Local Files (9 screenshots):**
- 5 REST API curl outputs
- 3 Kubernetes/Docker outputs
- 1 Security headers test

**Dari Kanban Board (Final - 1 screenshot):**
- CD pipeline done

---

### **URL Links (2, bukan screenshot):**
1. ci-build.yaml GitHub URL
2. Dockerfile GitHub URL

### **Text Files (1, bukan screenshot):**
1. pipelinerun.txt (sudah ada, tinggal upload)

---

## 🚀 PRIORITAS URUTAN

**BUAT DULU:**
1. Kanban board setup (modul 1-2)
2. GitHub screenshots (README, files)
3. REST API curl testing
4. Kubernetes/Docker outputs

**PALING MUDAH:**
- Copy file yang sudah ada
- Screenshot GitHub pages
- Screenshot kanban board

**YANG SUDAH SIAP:**
- ✅ pipelinerun.txt (sudah ada)
- ✅ kube-app-output.json (sudah ada)
- ✅ security-headers output (sudah ada)

---

**Total yang benar-benar screenshot: 27 files**
**Total URL links: 2**
**Total text files: 1 (sudah ada)**
