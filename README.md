## HLF go chaincode template

### Start tunnel
```bash
ngrok tcp 999
```

### Install, approve and commit chaincode
```bash
CHAINCODE_NAME=chaincode1
API_URL="http://localhost:8080/graphql"
SIGNATURE_POLICY="OR('Org1MSP.member', 'Org2MSP.member')"
CHAINCODE_ADDRESS_TUNNEL="4.tcp.eu.ngrok.io:13438" # the forwarding URL you get from opening an ngrok tunnel
hlf-cc-dev start --localChaincode="localhost:9999" \
  --chaincodeAddress="${CHAINCODE_ADDRESS_TUNNEL}" \
  --chaincode="${CHAINCODE_NAME}" \
  --signaturePolicy="${SIGNATURE_POLICY}" \
  --env-file="${PWD}/.env" \
  --apiUrl="${API_URL}"
```

### Start chaincode

```bash
source .env && go run ./main.go
```

