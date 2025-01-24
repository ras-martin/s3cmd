# s3cmd + GnuGPG
This is a Docker multi-arch image (amd64, arm/v7, arm64) for a simple [s3cmd](https://s3tools.org/s3cmd) S3 client and [GnuGPG](https://gnupg.org/) purely installed on the latest Alpine container

Useful with any S3 compatible object storage system.

## Docker Image
```
docker pull ghcr.io/ras-martin/s3cmd
```

The Docker Image is build on each change in this repository and periodically to ensure the latest available version of Alpine, s3cmd and GnuGPG (including security fixes) is used.

## Usage

### Settings
It basically uses the `.s3cfg` configuration file. If you are already using s3cmd locally you can provide this configuration to the Docker Container. In case you are not using s3cmd locally or don't want to use your local `.s3cfg` settings, you can use the s3cmd client to help you to generate your .s3cfg config file by using the following command.

```
mkdir .s3
docker run --rm -ti -v $(pwd)/data:/s3 -v $(pwd)/.s3:/root ghcr.io/ras-martin/s3cmd --configure
```

### Basic usage
```
docker run --rm -v $(pwd):/s3 -v $HOME/.s3:/root ghcr.io/ras-martin/s3cmd <command> s3://bucket-name
```
* The `.s3cfg` file has to be mounted to `/root`.
* Your data directory has to be mounted to `/s3`.

### s3cmd documentation
See [s3cmd usage](http://s3tools.org/usage) for further information.

## License

The content of this [repository](https://github.com/ras-martin/s3cmd) is provided under **MIT** licence
[![GitHub license](https://img.shields.io/github/license/ras-martin/s3cmd)](https://github.com/ras-martin/s3cmd/blob/master/LICENSE). For **s3cmd** license, please see [s3cmd repository](https://github.com/s3tools/s3cmd)
