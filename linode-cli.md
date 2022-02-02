# linode-cli

## Create the cluster

    $ linode-cli lke cluster-create \
        --label foo \
        --tags foo \
        --region us-east \
        --k8s_version 1.22 \
        --node_pools.type g6-standard-1 \
        --node_pools.count 2 \

## Get cluster id

    $ cluster_id=$(linode-cli lke clusters-list --tags foo --text --format id --no-headers)

## Get the config

    $ linode-cli lke kubeconfig-view $cluster_id --json | jq '.[].kubeconfig' -r | base64 -d > $cluster_id-config.yml