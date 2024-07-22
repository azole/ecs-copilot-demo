# AWS ECS Copilot CLI Demo

## Initial Application

```bash
# initial my app with Copilot application
copilot app init --domain {your domain}

copilot app ls
```

## Create First Environment - test

```bash
# create test env
## 可以跳過這步驟，直接執行 copilot init
copilot env init --name test --profile default

# copilot init 時會一併執行
copilot env deploy --name test
copilot env ls
copilot env show --name test
```

## Deploy Services

```bash
# depoly first service
copilot init

# deploy second service - frontend
copilot svc init --name frontend
## add build args for react build
## edit copilot/frontend/manifest.yml
copilot svc deploy --name frontend --env test
```

### Service Commands

```bash
copilot svc ls
copilot svc show --name frontend
# exec 進去 container 裡
copilot svc exec -a demo -e test --name frontend
copilot svc status
copilot svc logs
```

## Create Second Environment - prod & Deploy Service

```bash
# deploy second environment
copilot env init --name prod  --profile default
copilot env deploy --name prod

# deploy backend service to prod
copilot svc deploy --env prod --name backend
## override prod frontend image build args
## edit copilot/frontend/manifest.yml
copilot svc deploy --env prod --name frontend
```

## Delete Application

```bash
copilot app delete
```

## Others

```bash
# local 測試
copilot run local --name backend --env test --port-override 3005:3000
```
