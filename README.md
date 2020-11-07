# Setup GCP image for running Minecraft Bedrock edition on Ubuntu

* download and install packer from https://www.packer.io/downloads
* Checkout code and save to local directory
* download latest Ubuntu edition from Minecraft https://www.minecraft.net/en-us/download/server/bedrock, save in this directory.  E.g bedrock-server-1.16.40.02.zip
* Setup GCP account and create project & service account
* download service account credentials json file to this directory
* run validation code
```bash
packer validate bedrock.json
```
* run build, this will overwrite any existing ami with this name
```bash
packer build \
    -var 'gcp_credentials_file=<path_to_credentials_file>.json' \
    -var 'gcp_project_id=<GCP_PROJECT_ID>' \
    -var 'bedrock_zip_file=bedrock-server-1.16.40.02.zip' \
    bedrock.json
```

#### Optional parameters to packer are:
* gcp_image_name=minecraft-bedrock-1-16-40-02 , defaults to minecraft-bedrock
* gcp_image_base_image_name=ubuntu-1804-bionic-v20191211, defaults to ubuntu-1804-bionic-v20191211