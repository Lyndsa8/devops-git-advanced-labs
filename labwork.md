# Week 2 — Advanced Git & Version Control Labs

## 1. Multi-Branch Feature Integration Challenge

### Scenario
A development team is building an enterprise cloud cost optimization dashboard. To maintain production stability and follow DevOps best practices, features must be developed in completely isolated parallel streams, integrated into a shared development branch, and ultimately promoted to production.

### My Technical Execution
I configured a standard enterprise Git architecture by establishing a primary integration branch (`develop`) and branching out three separate, parallel feature timelines:

1. **`feature/login` (Authentication Infrastructure):Handles system authentication policies.**
   * Built `login_service.conf` to set maximum login attempts.
   * Updated `login_service.conf` to implement secure session timeouts.
   * Created `login_banner.txt` to serve system access warning banners.
2. **`feature/dashboard` (Metrics & Analytics Layer):Manages cloud cost performance metrics and alerts.**
   * Built `dashboard_metrics.conf` to control monitoring intervals.
   * Updated `dashboard_metrics.conf` to establish cloud budget thresholds.
   * Created `dashboard_layout.txt` to arrange frontend widget blueprints.
3. **`feature/reports` (Automated Reporting Engine):Controls weekly cron report compilation and distribution.**
   * Built `report_scheduler.conf` to initialize a weekly cron report scheduler.
   * Updated `report_scheduler.conf` to lock the data export output format to CSV.
   * Created `report_distribution.txt` to map internal stakeholder distribution emails.

###  Requirements Followed
* **Branching Strategy:** Maintained complete isolation between features by branching directly from `develop` and tracking parallel timelines.
* **Commit History Rules:** Logged exactly 3 unique, sequential commits per branch containing distinct configuration assets.
* **Meaningful Log Messaging:** Leveraged standardized prefix tracking (`config:`, `doc:`, `layout:`) for granular audit trails.

###  Verification: Parallel Branch Infrastructure
The terminal snippet below confirms the generation and cloud-tracking of the parallel branch streams:

![Feature Branches Verification](images/task1_branches.png)

### Skills Gained & Demonstrated
* **Git Architecture Design:** Understanding how to safeguard production (`main`) code from raw feature code using an intermediate deployment buffer (`develop`).
* **Granular Version Tracking:** Mastering micro-commits to capture incremental system changes instead of monolithic, bulk saves.
* **Linux Workspace Command:** Utilizing standard text output manipulations and system file builders to layout application blueprints entirely from the CLI.
### 🔄 Integration & Merge Workflow Execution
Once the parallel feature phases were concluded, I integrated all distinct development streams back into the centralized consolidation hub (`develop`) using an enterprise Git merge workflow:
1. Merged `feature/login` via a fast-forward progression.
2. Merged `feature/dashboard` utilizing Git's automatic three-way merge engine, generating a dedicated merge commit.
3. Merged `feature/reports` to complete the full dashboard subsystem integration.

#### ⚙️ Verification: Unified Git Timeline Graph
The complete version history topology map below demonstrates the parallel branch divergence and the successful convergence back into the development baseline:

![Unified Integration Graph](images/task1_merge_graph.png)

## 2. Multi-Student Merge Conflict Challenge

### 📋 Scenario
In a collaborative DevOps environment, two engineers ('Student A' and 'Student B') simultaneously updated the core application environment configuration file (`config/app.env`) from the same baseline. Student A modified the parameter to `APP_MODE=development` on branch `student-a`, while Student B altered the exact same line to `APP_MODE=production` on branch `student-b`. Integrating both branches into `develop` forced an intentional merge conflict.

### 🛠️ My Technical Execution & Resolution Strategy
1. **Divergence Setup:** Established two separate branches (`student-a` and `student-b`) originating from the identical `develop` base commit.
2. **Conflict Trigger:** Merged `student-a` cleanly into `develop`. Attempting to merge `student-b` immediately caused a file-content collision, halting the automatic Git merge engine.
3. **Manual Resolution:** Opened `config/app.env` via `nano`. Analyzed the conflict architecture:
   * `<<<<<<< HEAD` captured Student A's development changes.
   * `=======` isolated the competing edits.
   * `>>>>>>> student-b` captured Student B's production inputs.
4. **The Fix:** Deleted all Git conflict markers and aligned the configuration line cleanly to favor the team's production standard: `APP_MODE=production`.

### 📌 Requirements Followed
* **Authentic Conflict Generation:** Manipulated identical file lines across parallel tracks to block automatic merging.
* **Targeted File Selection:** Isolated conflict environments inside a dedicated `config/` path structure.
* **Clean History Commit:** Staged the manual resolution using a detailed, explanatory commit message.

### ⚙️ Verification: Triggered Merge Conflict Warning
Below is the terminal capture showing the exact moment the version engine flagged the structural merge collision:

![Merge Conflict Verification](images/task2_conflict_triggered.png)

### 🚀 Skills Gained & Demonstrated
* **Conflict Marker Literacy:** Understanding how to accurately interpret `<<<<<<<`, `=======`, and `>>>>>>>` blocks inside code structures.
* **Team Synergy Practices:** Simulating multi-engineer intersection workflows and standardizing manual mitigation steps.
* **Local Workspace Stability:** Learning how to safely intercept version failures, patch dependencies from the CLI, and re-stage assets without losing project data.
