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
