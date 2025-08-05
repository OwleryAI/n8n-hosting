# n8n-kubernetes-hosting

Get up and running with n8n on the following platforms:

* [AWS](https://docs.n8n.io/hosting/server-setups/aws/)
* [Azure](https://docs.n8n.io/hosting/server-setups/azure/)
* [Google Cloud Platform](https://docs.n8n.io/hosting/server-setups/google-cloud/)

If you have questions after trying the tutorials, check out the [forums](https://community.n8n.io/).

## Prerequisites

Self-hosting n8n requires technical knowledge, including:

* Setting up and configuring servers and containers
* Managing application resources and scaling
* Securing servers and applications
* Configuring n8n

n8n recommends self-hosting for expert users. Mistakes can lead to data loss, security issues, and downtime. If you aren't experienced at managing servers, n8n recommends [n8n Cloud](https://n8n.io/cloud/).

## Contributions

For common changes, please open a PR to `main` branch and we will merge this
into cloud provider specific branches.

If you have a contribution specific to a cloud provider, please open your PR to
the relevant branch.

## Setting up SSL connection to aws postgres
* Download the global certs from https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html#UsingWithRDS.SSL.CertificatesAllRegions
* Add it as a configmap called global-ca-bundle `kubectl create configmap --from-file=<path to global bundle.pem>`(the name of the configmap is important, and is specifically used in the n8n-deployment.yaml. Check this file in case the name changes)
* Note the NODE_EXTRA_CA_CERTS environment variable is set when running n8n, so it knows where to look for other certs to trust
