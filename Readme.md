# Installing Node Exporter on EC2 Instance using Ansible

This guide provides step-by-step instructions on how to install the Node Exporter on an EC2 instance using Ansible.

## Prerequisites

Before proceeding, ensure you have the following prerequisites:

- Ansible installed on your local machine.
- SSH access to the EC2 instance(s) you want to install the Node Exporter on.

## Instructions

1. Clone the repository:

   ```bash
   git clone <repository_url>
    ```

2. Navigate to the cloned repository:

    ```
    cd <repository_directory>
    ```

3. Open the inventory.ini file and replace your_ec2_instance_hostname_or_ip_address with the hostname or IP address of your EC2 instance(s). If you have multiple EC2 instances, add additional lines under the [all] group, each specifying the hostname or IP address of a separate EC2 instance.

4. Edit the Ansible playbook file install_node_exporter.yaml to customize any variables or settings as per your requirements.

5. Run the Ansible playbook to install Node Export

    ```
    ansible-playbook -i inventory.ini install_node_exporter.yaml
    ```
    The playbook will connect to the EC2 instance(s) and install the Node Exporter. It will download the necessary dependencies, download the Node Exporter binary, extract the files, configure the systemd service unit, and start the Node Exporter service.

6. Verify the installation:

After the playbook execution is complete, SSH into your EC2 instance and run the following command to check if the Node Exporter is running:

    ```
    curl http://<IP>:9100/metrics
    ```