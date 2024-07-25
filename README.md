# Prover-CLI

Prover-CLI is a command-line tool for processing and validating blockchain proofs.


## Prerequisites

- Python 3.6+
- Prometheus set up and running on your service
- Witness files generated using Jerigon


## Installation

git clone https://github.com/rebelArtists/prover_cli.git
cd prover_cli
python3 -m venv venv
source venv/bin/activate
pip install -e .


# Usage

## Set Up Port Forwarding
Before running the CLI, set up port forwarding for Prometheus for metric tracking:

nohup kubectl port-forward --namespace kube-prometheus --address localhost svc/prometheus-operated 9090:9090 &


## Process a Range of Witnesses

prover-cli run --begin_block 20362226 --end_block 20362237 --witness_dir /path/to/witnesses


## Validating and Extracting Proof

prover-cli validate --input_file /path/to/leader.out --output_file /path/to/cleaned_proof.json


## Plotting Metrics

prover-cli plot --csv_file /path/to/metrics.csv --metric_name cpu_usage --block_number 20362227 --threshold 0.002


## Review Metrics
Performance metrics are saved in metrics.csv in the current directory. Each row contains a unique metric
tagged by witness id


## Contributing
Contributions are welcome! Please open an issue or submit a pull request on GitHub.


## License
This project is licensed under the MIT License.

