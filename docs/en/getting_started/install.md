# Installation

### 1. Deploy the Workflow Orchestration Engine  
OmAgent utilizes [Conductor](https://github.com/conductor-oss/conductor) as its workflow orchestration engine. Conductor is an open-source, distributed, and scalable workflow engine that supports a variety of programming languages and frameworks. By default, it uses Redis for persistence and Elasticsearch (7.x) as the indexing backend.  
It is recommended to deploy Conductor using Docker:
```bash
docker-compose -f docker/conductor/docker-compose.yml up -d
```
- Once deployed, you can access the Conductor UI at `http://localhost:5001`. (Note: Mac system will occupy port 5000 by default, so we use 5001 here. You can specify other ports when deploying Conductor.)
- The Conductor API can be accessed via `http://localhost:8080`.
- More details about the deployment can be found [here](docker/README.md).

### 2. Install OmAgent  
- **Python Version**: Ensure Python 3.10 or higher is installed.
- **Install `omagent_core`**:
  ```bash
  pip install -e omagent-core
  ```
- **Install dependencies for the sample project**:
  ```bash
  pip install -r requirements.txt
  ```

- **Install Optional Components**: 
  - Install Milvus VectorDB for enhanced support of long-term memory.
OmAgent uses Milvus Lite as the default vector database for storing vector data related to long-term memory. To utilize the full Milvus service, you may deploy the [Milvus vector database](https://milvus.io/docs/install_standalone-docker.md) via Docker.
  - Pull git lfs files.
We provide sample image files for our examples in the `examples/step4_outfit_with_ltm/wardrobe_images` directory. To use them, ensure Git LFS is installed. You can install it with the following command:
      ```bash
      git lfs install
      ```
      Then, pull the files by executing:
      ```bash
      git lfs pull
      ```
  


### 3. Connect Devices  
If you wish to use smart devices to access your agents, we provide a smartphone app and corresponding backend, allowing you to focus on agent functionality without worrying about complex device connection issues.  
- **Deploy the app backend**   
    The APP backend comprises the backend program, along with two middleware components: the MySQL database and MinIO object storage. For installation and deployment instructions, please refer to [this link](https://github.com/om-ai-lab/OmAgent/blob/main/docker/README.md).
- **Download, install, and debug the smartphone app**  
  At present, we offer an Android APP available for download and testing. For detailed instructions on acquiring and using it, please refer to [here](../core_concepts/Clients/app.md). The iOS version is currently under development and will be available soon.