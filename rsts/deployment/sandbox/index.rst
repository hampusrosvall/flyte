.. _deployment-sandbox:

##################
Sandbox Deployment
##################

**************************
Flyte Deployment - Sandbox
**************************
This guide helps you set up Flyte from scratch, on any kubernetes cluster, It will helpful in trying out flyte. It details step-by-step instructions to go from a bare Kubernetes cluster to a fully functioning Flyte deployment that members of your company can use.

.. note::

  Please make sure you have a working kubernetes cluster with write permission


1. Add Helm repo for Flyte,Postgres & Minio

.. code-block::

 helm repo add flyteorg https://helm.flyte.org
 helm repo add bitnami https://charts.bitnami.com/bitnami

2. Install Minio deployment in kubernetes cluster

.. code-block::

 helm install minio bitnami/minio -n default --set auth.rootPassword="flyte"

3. Install Postgres deployment in kubernetes cluster

.. code-block::

 helm install postgresql bitnami/postgresql -n default --set auth.postgresPassword="flyte"

4. Create a values-override.yaml file

.. code-block::

 helm install flyte flyteorg/flyte-core -n default -f https://raw.githubusercontent.com/flyteorg/flyte/master/charts/flyte-core/values-sandbox.yaml

