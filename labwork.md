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

## 3. Disaster Recovery: Rollback Strategies (Reset vs Revert)

### 📋 Scenario
An unstable deployment script containing a broken database connection payload string was introduced into the core timeline. To mitigate service downtime, a DevOps specialist must deploy targeted version recovery workflows—evaluating the architectural differences between forward-facing rollbacks (`revert`) and destructive history rewrites (`reset`).

### 🛠️ My Technical Execution
1. **History Pipeline Construction:** Built a sequential 5-commit infrastructure timeline inside `config/deploy.conf`, culminating in a deliberate production bug tracking payload.
2. **Forward-Facing Remediation (`git revert`):** Executed `git revert HEAD` to dynamically parse the target anomaly and auto-generate a new inverse patch commit, neutralizing the error while preserving the complete audit trail.
3. **Staged State Evaluation (`git reset --soft`):** Tested isolated rollback arrays by shifting the branch pointer back one node while keeping the code changes staged, allowing for hot-fix re-authoring.
4. **Destructive Baseline Purge (`git reset --hard`):** Applied an absolute environment reset to scrub all local file changes and working tree modifications, instantly aligning the environment with the last-known stable deployment state.

### 📌 Requirements Followed
* **Comprehensive Command Execution:** Successfully simulated and analyzed all three standard undo paradigms.
* **History Preservation Rules:** Utilized forward-facing overrides for public remote tracking safety, reserving hard resets for private branch cleansing.

### ⚙️ Verification: Forward-Facing Revert Timeline Log
The log snippet below verifies the creation of a non-destructive recovery path, adding a new correction node while keeping the historical timeline transparent:

![Git Revert Verification Flow](images/task3_revert_log.png)

### 📊 Strategic Command Comparison Table
The technical variations between each tested disaster recovery mechanism are outlined below:

| Command Parameters | Target Pointer Impact | Working Tree (Local Files) | Remote Safety Profile | Optimal Operational Use-Case |
| :--- | :--- | :--- | :--- | :--- |
| `git revert` | Moves forward by adding a new commit | Untouched (receives inverse changes) | 100% Safe for Shared Branches | Undoing bugs pushed to shared production environments |
| `git reset --soft` | Moves backward to target commit | Untouched (changes remain staged) | Dangerous (Requires Force Push) | Grouping work or rewriting a local commit message |
| `git reset --hard` | Moves backward to target commit | Instantly wiped to match target commit | High Risk (Destroys uncommitted code) | Complete local abandonment of broken feature experiments |

### 🚀 Skills Gained & Demonstrated
* **Production Rollback Literacy:** Decoupling safe, public-facing restoration mechanics from volatile local timeline shifts.
* **Working Tree State Control:** Precision isolation of staged, unstaged, and committed assets during infrastructure emergency events.
* **History Integrity Auditing:** Managing clean version structures required to meet strict compliance and enterprise rollback metrics.
