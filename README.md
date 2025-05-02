# aztec-sequencer
Docker Compose setup for running the Aztec Network sequencer(testnet) and node monitoring.


### Prerequisites
- Docker and Docker Compose installed - https://docs.docker.com/engine/install/ubuntu/#installation-methods
- aztec - `bash -i <(curl -s https://install.aztec.network)`


### How to run the sequencer
- `cp .env.sample .env`
- **Update all variables in .env file**
- `docker compose up -d`


### Monitoring
- Log in to Grafana with your `GRAFANA_USER` and `GRAFANA_PASSWORD` on `http://your_host_ip_address:3000`
- Check sequencer logs `docker logs -f aztec-node-node-1`


### Register your validator (you will need some Sepolia ETH)
**Important:** Only perform this step after the sequencer sync is complete.

```bash
aztec add-l1-validator \
  --l1-rpc-urls ETH_SEPOLIA_RPC_ENDPOINT \
  --private-key your-private-key \
  --attester 0xYourEthAddress \
  --proposer-eoa 0xYourEthAddress \
  --staking-asset-handler 0xF739D03e98e23A7B65940848aBA8921fF3bAc4b2 \
  --l1-chain-id 11155111
