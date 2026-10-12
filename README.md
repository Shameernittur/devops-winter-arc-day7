# DevOps Winter Arc - Mini Production Repository ❄️

## 📖 Project Purpose
This repository serves as a practical sandbox for mastering foundational DevOps engineering skills, specifically version control with Git and GitHub, branching strategies, and system health tracking. It was built during Day 07 of the 90 Days DevOps Winter Arc.

## ⚙️ Setup and Testing
To view the application state and health checks, you do not need any complex dependencies. 
1. Clone the repository: `git clone <your-repo-url>`
2. View the core application config: `cat app.txt`
3. Verify the system status: `cat status.txt`
4. Check the application health: `cat health.txt`

## 🌿 Git Workflow Followed
This project adheres to a standard trunk-based development and feature-branching workflow:
* **Main Branch Stability:** Direct commits to `master`/`main` are minimized.
* **Feature Branches:** New features (like the health check) are developed on isolated branches (e.g., `feature/health-check`).
* **Pull Requests:** Code is integrated back into the primary branch via GitHub Pull Requests to simulate code review and automated checks.
* **Environment Protection:** A `.gitignore` file is strictly enforced to prevent sensitive `.env` files, `node_modules/`, and `*.log` files from polluting the repository.

## 🚨 Production Challenge: Ghost Files & Disk Space
During this arc, we tackled a critical production incident: **Filesystem usage at 100%**. 
A common trap is deleting massive log files, only to see disk space remain unchanged. We proved that if a running process still has a deleted file open, the kernel will not release the storage blocks. 

**Our resolution framework:**
1. Checked space and inode utilization (`df -h` and `df -i`).
2. Identified high-growth areas (`du`).
3. Used `lsof +L1` to find "ghost" files (deleted files still held open by active processes).
4. Restarted or reloaded the holding processes to safely free the disk space.
