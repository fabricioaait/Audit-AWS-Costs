# AWS Cost Audit Scripts

A collection of Bash scripts to help audit AWS accounts for common sources of unnecessary costs and best practices. Run in a read-only policy context.  

## Directory Structure

```
aws-cost-audit/
  scripts/
    check_budgets.sh
    check_data_transfer_risks.sh
    check_forgotten_ebs.sh
    check_idle_ec2.sh
    check_idle_load_balancers.sh
    check_old_rds_snapshots.sh
    check_on_demand_instances.sh
    check_s3_lifecycle.sh
    check_untagged_resources.sh
    main.sh
    utils.sh
README.md
```

## What Each Script Does

- **check_untagged_resources.sh**: Finds AWS resources without tags for better cost allocation.
- **check_idle_ec2.sh**: Flags underutilized or idle EC2 instances.
- **check_budgets.sh**: Checks for the presence of AWS Budgets and alerts.
- **check_s3_lifecycle.sh**: Finds S3 buckets lacking lifecycle policies.
- **check_old_rds_snapshots.sh**: Detects RDS snapshots older than 30 days.
- **check_forgotten_ebs.sh**: Lists unattached EBS volumes.
- **check_data_transfer_risks.sh**: Audits for public IPs, unused Elastic IPs, subnet/AZ design, and VPC endpoints.
- **check_on_demand_instances.sh**: Counts on-demand EC2 instances to encourage cost savings.
- **check_idle_load_balancers.sh**: Flags load balancers with no recent traffic.
- **utils.sh**: Helper functions used by the other scripts.
- **main.sh**: Orchestrates the execution of all checks and logs the results.

## Usage

1. **Configure AWS CLI**  
   Ensure your AWS CLI is configured and you have the necessary IAM permissions for each check.

2. **Run the Audit**  
   From the `scripts/` directory, run:

   ```bash
   ./main.sh
   ```

3. **View Results**  
   The results will be displayed in the terminal and saved to a log file named:

   ```
   audit_aws_YYYYMMDD_HHMMSS.log
   ```

   (with the current date and time in the filename)

## Notes

- These scripts operate on a single AWS account and region at a time.
- Make sure you have the required permissions for all AWS services being checked.
- Review and customize the scripts as needed for your environment.

## Example Output

You should get the output `audit_aws_YYYYMMDD_HHMMSS.log` file and see the check progress in the terminal.

---

**Contributions and suggestions are welcome!**
