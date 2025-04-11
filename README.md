
# 🔧 AWS Auto Scaling Test using `stress`

This project helps simulate high CPU and memory usage using the [`stress`](https://linux.die.net/man/1/stress) tool to validate if your AWS Auto Scaling configuration is working as expected.

## 📦 Prerequisites

- EC2 instance (Amazon Linux / Ubuntu)
- `stress` tool installed
- Auto Scaling Group (ASG) configured with scaling policies based on CPU/Memory

---

## ⚙️ Installation

### Amazon Linux:
```bash
sudo yum install -y epel-release
sudo yum install -y stress
```

### Ubuntu:
```bash
sudo apt-get update
sudo apt-get install -y stress
```

---

## 🚀 Running the Stress Test

```bash
stress -c <CPU_CORES> --vm <MEMORY_WORKERS> -t <DURATION>
```

### Parameters:
- `-c`: Number of CPU workers (simulates CPU load)
- `--vm`: Number of virtual memory workers (simulates memory load)
- `-t`: Time to run the test (e.g., `60s`, `2m`)

### Example:
```bash
stress -c 4 --vm 2 -t 120s
```
This command will:
- Use 4 CPU cores
- Spawn 2 memory workers
- Run the test for 2 minutes

---

## 📈 Use Case

This test is useful for:
- Triggering Auto Scaling Group scale-out/in actions
- Validating CloudWatch alarms
- Testing load-based infrastructure resilience

---

## 📌 Notes

- Monitor metrics via **CloudWatch** during the test.
- Ensure your instance type has enough resources to reflect the stress.
- Combine this with **load testing tools** for comprehensive scaling validation.

---

## 🛑 Disclaimer

Use this script **only in test environments**. Running stress tests in production can lead to downtime or unexpected scaling behavior.

---
