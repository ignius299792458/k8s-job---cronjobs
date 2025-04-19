# k8s-job---cronjobs
Kubernetes jobs and cron jobs


# Kubernetes Jobs and CronJobs

## Jobs

A Job in Kubernetes creates one or more pods and ensures they successfully terminate. Jobs are useful for batch processing, where work needs to be completed once rather than running continuously.

**Key concepts in Jobs:**
- Creates pods that run until completion
- Tracks successful completions
- Can run multiple pods in parallel
- Can retry failed pods based on configuration
- Once the specified number of completions is reached, the Job is considered complete

**Job Diagram**
```
                        +---------------+
                        |     Job       |
                        +-------+-------+
                                |
                                | creates
                                v
                        +---------------+
                        |     Pods      |
                        +-------+-------+
                                |
                                | run to completion
                                v
                        +---------------+
                        |   Success or  |
                        |    Failure    |
                        +---------------+
```

## CronJobs

A CronJob is a Job that runs on a schedule, defined using cron syntax. It creates Jobs repeatedly at specified times.

**Key concepts in CronJobs:**
- Scheduled using cron expression syntax (e.g., `* * * * *` for every minute)
- Creates Job objects at scheduled times
- Can specify concurrency policy (Allow, Forbid, Replace)
- Controls history of completed/failed Jobs

**Cron Job Diagram:**
```
                 +---------------------+
                 |      CronJob        |
                 | (with schedule)     |
                 +----------+----------+
                            |
                            | creates at scheduled times
                            v
                 +---------------------+
                 |        Job          |
                 +----------+----------+
                            |
                            | creates
                            v
                 +---------------------+
                 |        Pods         |
                 +----------+----------+
                            |
                            | run to completion
                            v
                 +---------------------+
                 |   Success/Failure   |
                 +---------------------+
```

The primary difference is that Jobs run once and complete, while CronJobs continuously create new Jobs based on a schedule, similar to how cron works in Linux systems.
