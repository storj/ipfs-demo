The IPFS demo box implemenents an IPFS node backed by a Storj datastore.

Both the IPFS Gateway and the HTTP API run on the default HTTPS port 443.

Only the `/api/v0/add` endpoint is available from the HTTP API. All other endpoints are restricted.

The IPFS Gateway is configured as a restricted gateway, i.e. it serves only the files available on the node. It will not attempt to discover them from the IPFS network. At the same time, all files uploaded to the node are discoverable from other nodes on the IPFS network.

## Upload and Pin

Execute the following command in your Terminal.

```
curl -X POST -F "file=@myfile" "https://ipfs-demo.dev.storj.io/api/v0/add"
```

Replace `myfile` with the path to your file on the local file system. Keep the `@` character in front of the file path. Uploads are limited to 64 MB. The command will return a JSON response with the hash of the uploaded file on the IPFS network.

Example:

```
curl -X POST -F "file=@/home/demo/storj-logo.png" "https://ipfs-demo.dev.storj.io/api/v0/add"
```

```json
{
    "Name": "storj-logo.png",
    "Hash": "QmWT7d4MAvva7uLoTRh8i7GiMSZUDND4Z5xNo5LCQeUrYh",
    "Size": "131539"
}
```

## Download

Use the following URL in the Web browser to request the file:

```
https://ipfs-demo.dev.storj.io/ipfs/myhash
```

Replace `myhash` with the hash returned by the upload command from the previous section.

Example: https://ipfs-demo.dev.storj.io/ipfs/QmWT7d4MAvva7uLoTRh8i7GiMSZUDND4Z5xNo5LCQeUrYh
