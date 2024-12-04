# Quick Start

## 1、Configuration

The container.yaml file is a configuration file that manages dependencies and settings for different components of the system. To set up your configuration:

1. Generate the container.yaml file:
   ```bash
   cd examples/step2_outfit_with_switch
   python compile_container.py
   ```
   This will create a container.yaml file with default settings under `examples/step2_outfit_with_switch`.



2. Configure your LLM settings in `configs/llms/gpt.yml` and `configs/llms/text_res.yml`:

   - Set your OpenAI API key or compatible endpoint through environment variable or by directly modifying the yml file
   ```bash
   export custom_openai_key="your_openai_api_key"
   export custom_openai_endpoint="your_openai_endpoint"
   ```

3. Update settings in the generated `container.yaml`:
      - Configure Redis connection settings, including host, port, credentials, and both `redis_stream_client` and `redis_stm_client` sections.
   - Update the Conductor server URL under conductor_config section
   - Adjust any other component settings as needed

4. Websearch uses duckduckgo by default. For better results, it is recommended to configure [Bing Search](https://www.microsoft.com/en-us/bing/apis/pricing) by modifying the `configs/tools/websearch.yml` file and setting the `bing_api_key`.

For more information about the container.yaml configuration, please refer to the [container module](../core_concepts/container.md)

## 2、Running the Example

1. Run the outfit with switch example:

   For terminal/CLI usage: Input and output are in the terminal window
   ```bash
   cd examples/step2_outfit_with_switch
   python run_cli.py
   ```

   For app/GUI usage: Input and output are in the app
   ```bash
   cd examples/step2_outfit_with_switch
   python run_app.py
   ```
   For app backend deployment, please refer to [here]([docker/README.md](https://github.com/om-ai-lab/OmAgent/blob/main/docker/README.md))  
   For the connection and usage of the OmAgent app, please check [app usage documentation](../core_concepts/Clients/app.md)