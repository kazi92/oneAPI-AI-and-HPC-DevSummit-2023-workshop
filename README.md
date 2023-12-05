# oneAPI-AI-and-HPC-DevSummit-2023-workshop
# LLM Custom Chatbot development with Huggingface opensource Mistral 7B model with Intel Developer Cloud (IDC)

Developing a custom Language Learning Model (LLM) chatbot on Intel Xeon processors using the Intel Developer Cloud (IDC) involves leveraging the advanced capabilities of these processors and the robust tools provided by Intel Developer Cloud (IDC).

Intel Xeon processors are known for their high performance and are widely used in servers and workstations. They are particularly suited for AI and machine learning tasks due to their ability to handle large amounts of data and perform complex computations efficiently. This makes them an excellent choice for developing and running a custom LLM chatbot.

The # Intel Developer Cloud (IDC) # is a cloud-based platform that provides developers with access to a variety of Intel hardware and software resources. It includes tools for developing, testing, and optimizing applications, and supports a wide range of programming languages and frameworks. Using IDC, you can easily deploy your LLM chatbot and scale it as needed.

In this setup, you would develop your LLM chatbot application, then deploy it on the IDC. This allows you to take full advantage of the capabilities of these processors and the flexibility and scalability of cloud computing.

Steps to execute:

# a. Register in Intel Developer Cloud
  1.Go to Intel Developer Cloud: https://cloud.intel.com/
  2.Click Get Started
  3.Subscribe to “Standard” service tier and complete cloud registration
  4.Select “Cloud Credits”
  5.Select “Redeem coupon”
  6.Enter your Intel Developer Cloud code provided to setup a bare metal server instance.

# b. Setup an instance 
  ## 1. Setup a conda environment after you access the instance 

    mkdir -p ~/miniconda3
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
    bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
    rm -rf ~/miniconda3/miniconda.sh

    ~/miniconda3/bin/conda init bash

  ## 2. Install the dependencies and library packages required to run the application

  Command:  pip install huggingface_hub gradio 

  ## 3. Open a .py file and copy the code or upload the .py file

  ## 4. Use the following command below :

    curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null && echo \
    "deb https://ngrok-agent.s3.amazonaws.com buster main" | sudo tee /etc/apt/sources.list.d/ngrok.list && sudo apt update && sudo apt install ngrok

  This command is a one-liner that installs `ngrok` on a Linux system. It's a sequence of commands combined using `&&` operator, which means 
  the next command will only run if the previous command succeeds. Let's break it down:
  `curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null`

   This command downloads the GPG key for the ngrok package from the ngrok-agent S3 bucket using `curl`. The `-s` option makes curl silent, 
   so it doesn't show progress or error messages. The downloaded key is then piped (`|`) into the `sudo tee 
   /etc/apt/trusted.gpg.d/ngrok.asc` command, which writes the key into the `/etc/apt/trusted.gpg.d/ngrok.asc` file. The `>/dev/null` part 
  discards the standard output of the `tee` command, so it doesn't clutter your terminal.

  `echo "deb https://ngrok-agent.s3.amazonaws.com buster main" | sudo tee /etc/apt/sources.list.d/ngrok.list`

   This command adds the ngrok repository to your APT sources. The `echo` command prints the string, which is then piped into `sudo tee 
  /etc/apt/sources.list.d/ngrok.list`, creating a new file `ngrok.list` in the `/etc/apt/sources.list.d/` directory with the ngrok 
  repository information.

  `sudo apt update`

   This command updates the package lists for upgrades and new package installations from the repositories defined in your system, including 
   the ngrok repository we just added.

   `sudo apt install ngrok`

   This command installs the ngrok package.

   In summary, this command sequence is adding the ngrok repository to your system's package manager, updating the package list, and then 
   installing ngrok.

  ## 5. Use the following command:

    ngrok config add-authtoken <authtoken>

    Example :

    ngrok config add-authtoken 219XW8KAr0Dbi5PVkTlS4HUkM5B_77YQKUJ7e1AgtThaEBYPo

    Please note that the authtoken provided in the command is just an example and should be replaced with your actual ngrok authtoken. 
    You canfind your authtoken in your ngrok dashboard after signing in to your account.

  ## 6. Open another terminal 
  
    Use the following command 

    ngrok http 7860 

    The command `ngrok http 7860` is used to expose a local web server to the internet. Here's what each part of the command does:

    `7860`: This is the port number on your local machine that `ngrok` will expose to the internet. In this case, `ngrok` will tunnel       
     traffic from the public internet to your local machine's port 7860.

    When you run this command, `ngrok` will provide a public URL (like `http://<random-subdomain>.ngrok.io`) that you can use to access 
    your local web server from anywhere on the internet. Any HTTP requests made to this public URL will be forwarded to your local 
    machine on port 7860.
