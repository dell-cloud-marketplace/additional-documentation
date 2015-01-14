# docker-{image_name}
This image installs [{image_name}]({image_official_website}), {image_description}

## Components
The software stack comprises the following components:

Name         | Version     | Description
-------------|-------------|------------------
Component_1  | {version}   | {description}
Component_2  | {version}   | {description}
...          | {version}   | {description}
Component_N  | {version}   | {description}

## Usage

### Start the Container
If you wish to create data volumes, which will survive a restart or recreation of the container, please follow the instructions in [Advanced Usage](#advanced-usage).

#### Basic Usage
Start your container with:

 - A named container (**{image_name}**).
 - Ports {ports_number} ({application_name}) exposed.

As follows:

```no-highlight
sudo docker run -d -p {ports} --name {image_name} dell/{image_name}
```

<a name="advanced-usage"></a>
#### Advanced Usage
Start your container with:

- A named container (**{image_name}**).
- Ports {ports_number} ({application_name}) exposed.
- {N} data volumes (which will survive a restart or recreation of the container). The {volume_1} is available in **{volume_1_path}** on the host. The {volume_N} is available in **{volume_N_path}** on the host. 
- {variables_exposed} 

As follows:

```no-highlight
sudo docker run -d -p {ports} -v {volumes} -e {variables} {image_name} dell/{image_name}
```

## Reference

### Image Details

Based on (or Inspired by) [{based_image_name}]({based_image_github})

Pre-built Image | [https://registry.hub.docker.com/u/dell/{image_name}](https://registry.hub.docker.com/u/dell/{image_name}) 


## Verification/Testing Phase

Make sure the Docker container has been deployed correctly by checking if the following criteria are met: 
 
* The applications/websites URL mentioned in the documentation are accessible from a browser/cURL
* HTTPS is enabled for web-based applications 
** From the browser, the end-user is asked to accept a self-signed certificate "CN=www.dell.com, OU=MarketPlace, O=Dell, C=US"
* Processes started from the application are listening on ports listed in the Docker file
* When using volumes, mapped directories are correctly created on the local environment
** Any files located under mapped directories such as logs, configuration files can be accessed or/and updated locally
* If the docker container uses a database, this latter is accessible by passing a randomly-generated or predefined password
