project:
  name: terraform-docker-container 🚀🐳
  description: >
    Provision a local Docker container running NGINX using Terraform — 
    Infrastructure as Code made simple and fun! 🎉🛠️
  prerequisites:
    - Docker 🐳
    - Terraform 🧙‍♂️
    - Code Editor (e.g., VS Code) 💻
    - GitHub account (optional) 🌐
  files:
    main.tf: |
      terraform {
        required_providers {
          docker = {
            source  = "kreuzwerker/docker"
            version = "~> 2.13.0"
          }
        }
      }

      provider "docker" {
        host = "unix:///var/run/docker.sock"
      }

      resource "docker_image" "nginx_image" {
        name = "nginx:latest"
      }

      resource "docker_container" "nginx_container" {
        name  = "nginx_server"
        image = docker_image.nginx_image.latest

        ports {
          internal = 80
          external = 8080
        }
      }

  readme: |
    # Terraform Docker NGINX Container 🐳 + 🧙‍♂️

    Welcome to your **Terraform-powered Docker NGINX** setup! Let's get your web server up and running in a few simple steps. 🚀

    ## 🛠 Prerequisites Checklist ✅

    - **Docker** installed and running 🐳
    - **Terraform** installed and ready to go 🧙‍♂️
    - A friendly **code editor** like VS Code 💻
    - (Optional) A **GitHub account** for sharing 🌍

    ## 📂 Project Setup

    Create your project folder and navigate into it:

    ```bash
    mkdir terraform-docker-container
    cd terraform-docker-container
    ```

    Create a file called `main.tf` and paste in the Terraform code above.

    ## 🚀 Running the Project

    Initialize Terraform, preview the changes, and apply them:

    ```bash
    terraform init
    terraform plan
    terraform apply
    ```

    When prompted, type `yes` to confirm.

    Now open your favorite browser and visit 👉 [http://localhost:8080](http://localhost:8080)  
    You should see the classic NGINX welcome page! 🎉🎉🎉

    ## 👀 Verify Container is Running

    Check Docker containers with:

    ```bash
    docker ps
    ```

    ## 🧹 Cleanup Time

    When you're done, destroy all created resources by running:

    ```bash
    terraform destroy
    ```

    Confirm with `yes` and you're all cleaned up! 🧽✨

    ## 📚 Notes & Tips

    - Make sure Docker daemon is running before starting Terraform 🐳🔥
    - This project uses the awesome [kreuzwerker/docker](https://registry.terraform.io/providers/kreuzwerker/docker/latest) provider
    - Have fun learning Infrastructure as Code! 🎉👨‍💻

    ## 📜 License

    This project is licensed under the MIT License — use it, share it, learn from it! ❤️
