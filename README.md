Tested on crc
=============

# Prerequisites
`$ crc setup`\
`$ crc start -m 10240`\
`$ oc login ...`\
`$ oc create secret generic mycluster-pull-secret --from-file=.dockerconfigjson=/path/to/pull-secret --type=kubernetes.io/dockerconfigjson`\
`$ cd $source_code`\
`$ make deploy`

# Steps

1) `oc create myns myns2`
2) `oc create secret generic kcsecret --from-file=kubeconfig=kubeconfig`
3) `oc create secret generic kcsecret2 --from-file=kubeconfig=kubeconfig2`
4) `oc create secret generic sshsecret --from-file=ssh-publickey=~/.ssh/id_rsa.pub`
5) `oc create -f cd.yml`
6) `oc create -f syncset.yml`
7) `oc create -f syncset2.yml`

# Verify:
`$ oc get cm -n myns`\
`$ oc get cm -n myns2`
