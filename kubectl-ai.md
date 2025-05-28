## Alguns exemplos

```bash
cat busybox-deployment.yaml | kubectl ai "change replicas to 1" --raw | kubectl apply -f -

```

```bash

# Visual Studio Code
$ kubectl ai "create a foo namespace" --raw | code -

# Vim
$ kubectl ai "create a foo namespace" --raw | vim -

```

```bash
cat busybox-deployment.yaml | kubectl ai "change replicas to 1" --raw > busybox-deployment-update.yaml

```