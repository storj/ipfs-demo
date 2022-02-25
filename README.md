The IPFS demo box implmenents an IPFS node backed by a Storj datastore.

The HTTP API of the IPFS node running on port 5443. Only the `/api/v0/add` endpoint is available.

The IPFS Gateway is running on port 443.

## Upload and Pin

Execute the following command in your Terminal.

```
curl -X POST -F "file=@myfile" "https://ipfs-demo.dev.storj.io:5443/api/v0/add"
```

Replace `myfile` with the path to your file on the local file system. Keep the `@` character in front of the file path. Uploads are limited to 64 MB.

The command will return a JSON response with the hash of the uploaded file on the IPFS network.

Example:

```
curl -u admin:mypass -X POST -F "file=@/home/kaloyan/Pictures/Storj Logomark - Color-1064x1200-369e5a5.png" "https://ipfs-demo.dev.storj.io:5443/api/v0/add"
```

```json
{
    "Name": "Storj Logomark - Color-1064x1200-369e5a5.png",
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
