# Prerequisite

## Install Java/JDK17 in your terminal

```
brew install openjdk@17
```
<br>

## Install Teamcity On-Premises
[Download TeamCity Here](https://www.jetbrains.com/teamcity/download/?shownFormKey=professional#section=server)

### Untar the file given
```
tar xzf TeamCity-2024.07.3.tar.gz
```

### Start TeamCity
```
./Teamcity/bin/runAll.sh start
```
<br>

## Install Docker Desktop
[Download Docker Here](https://docs.docker.com/desktop/install/mac-install/)

Configure it with your own created account

<br>

## Set up kubectl on your machine
[Download kubectl Here](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)

### Set this up as your current context
``` yaml
apiVersion: v1
kind: Config
preferences: {}

clusters:
- cluster:
    certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCVENDQWUyZ0F3SUJBZ0lJTnNiVnZVd2o1WFF3RFFZSktvWklodmNOQVFFTEJRQXdGVEVUTUJFR0ExVUUKQXhNS2EzVmlaWEp1WlhSbGN6QWVGdzB5TkRFd01ETXdOalV5TkRaYUZ3MHpOREV3TURFd05qVTNORFphTUJVeApFekFSQmdOVkJBTVRDbXQxWW1WeWJtVjBaWE13Z2dFaU1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLCkFvSUJBUUMvQWs2RHdLaW03dDI2ZWlZa3hTNGZUKys5czVLTmsrRE1EVFBmU0o4TXNZbnEwb21sNEloMHk0NC8KZGlXVmhHdE9QVFdiUFhOL1VGWW1LZ0JJVkN3K2V6MWx5MEsyRXljVlpyQ0NVS0w2VDNaSzNBTVpybTRsK1YySQpXUmg5UThlUVJVR0FMaElrNWxKczgrdWZZc1lUcjRScEEwUFlUWFpNcldvd1cxY0JKdXVRVTIxU2NIY2JjMFNGCld5Rkd1bzBsYUFZOHVFc1huSTVucld5K05JZ08vWVU5L2RTVzdMc0hsZXJEQzRMa09NaExaMkJLNVVtQjQydVkKMVB5UVdNTVd0RkxlV1F4SGNTNzN6MU9YN2V2VmF6TEorWG1sSi9CQUhjUjFWdkE1QndFaVVRcTQxZWV0SFBDTwowcnhZRmlUaUNBODVRY0ZsVkpwN0R0L1kxVlpWQWdNQkFBR2pXVEJYTUE0R0ExVWREd0VCL3dRRUF3SUNwREFQCkJnTlZIUk1CQWY4RUJUQURBUUgvTUIwR0ExVWREZ1FXQkJRblNJMFZWTkRoSndoOUQwR0FrZjYwQ1p2cit6QVYKQmdOVkhSRUVEakFNZ2dwcmRXSmxjbTVsZEdWek1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQVpzbnlzcDlncApSaGUxTzRnUGt1T2ZWWkExUEw4dEkybERPWmNnRjk1UnFZOFZ0Z2x2MXBMSEVzQnlSZ2tvbTBmM003WEJ1VU1jClBsZnpNN2dyaVF6c0FIUUxLTFpJb2dFMVFwcFFVRWdzQ1FZdUU3QXV1enorRG9aK0dUcXNYYVRVanRENHhqTDEKRm1MWW5iY3NkM1NTcTh3WDlKMkVSeVJ3dXFUVEZDNnVEYzNiVitwQ09IZGV0TXZiL1hRYzN0cTlrbUZub0ZCLwppUFJIaGpnQzViUWNYYk92ZHFsTnd6c202UGlnS3hXUFFkUTZ0NDc3ZkdjYzQxZWFFdWZZZ1h1dnVxSzdGeWxvCkxDWHZ2QWNGaEphUURjY3R2dUZ5Z001WGQwbGdTQzNsZ2crdGFxeXJWc2JNKzZUYkxvOHNxNCtaay8yWWpzT0EKRG1MeGNFLzVrWSthCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K
    server: https://9c9ac1f7-1d29-46f9-81a5-364913e1d417.ap-south-1.linodelke.net:443
  name: lke238244

users:
- name: lke238244-admin
  user:
    as-user-extra: {}
    token: eyJhbGciOiJSUzI1NiIsImtpZCI6InNlejVlMFJUNWw3U1FBYTlpS0xCWVFRYS1SZ1M0QWgzdWo2aUJVNXdDSXMifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJsa2UtYWRtaW4tdG9rZW4tY2hxcXYiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoibGtlLWFkbWluIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQudWlkIjoiZWMyMmNiNzgtYTc4Zi00OGZlLWFhOTktZmE2MmZmMDU0ZWEyIiwic3ViIjoic3lzdGVtOnNlcnZpY2VhY2NvdW50Omt1YmUtc3lzdGVtOmxrZS1hZG1pbiJ9.J8gij2fPqHkC7rtkDVjsv-JxD_vSGyEPuo1lblMuVN_g_4H40MtHGFpb6FpTty6BJzgDy2BiI78VT0_Kfvk7sZ31wEvrNrxPg--sMdxvRutwz0Y-FF6FG51c3Q3JiltGYMeB3sgTPSYyXinHqkVUa-HSfjyeQ_j1jT-8utqed1Yrl-O74AzAqJVw-n_41lntJ9ENDEsmtzh1goyQlsPbrClYAHDJFxCqx3Z5Euey1RokGZOaqr-9GL7giatsLuzPl-ghaF0RMVu3FkRbQ2fVNHVhB5Pohdsopjg6yGKxCkftPla_s0xBXVyFUkuHWrG2gTPpugxZTcBGq9P56mUyFQ

contexts:
- context:
    cluster: lke238244
    namespace: default
    user: lke238244-admin
  name: lke238244-ctx

current-context: lke238244-ctx
```

### Create a directory and paste it here
```
<HomeDir>/.kube/config
```
<br>
---

# Set Up TeamCity

## A. Set Up Your SSH Key

1. Navigate to the **Root Project** under the **Administration** tab.
2. Select **SSH Key** from the menu.
3. Click **Generate SSH Key** and follow the steps below:
    - **Pick Type**: Select `RSA` as the key type.
    - **Input Name**: Enter your preferred name for the key.
4. Click **Generate** to create the key.
5. Copy the **Public Key** and add it to your Git repository's SSH configuration.

## B. Creating a New Project

1. Set up your project by providing the repository URL.
2. For **Authentication**, select **SSH Key**.
3. Choose the SSH key you recently generated.
4. Click **Proceed** to continue with the project setup.


## B1. Create First Dev Build Configuration

### B1.1 Modify Default Branch and Branch Specification
- Set the default branch and branch specification to the head of the `dev` branch.
- Click **Proceed**.

### B1.2 Add 1st Build Step - Test
- **Name**: `Test`
- **Runner Type**: Select **Python**.
- **Command**: `Pytest`
- **Environment Tool**: Choose **Venv**.
- **Dependencies**: Add your `requirements.txt` file.
- Click **Save**.

### B1.3 Add 2nd Build Step - Build
- **Name**: `Build`
- **Runner Type**: Select **Command Line**.
- **Custom Script**:
    ```bash
    docker buildx build --no-cache --platform=linux/amd64 -t eywrld839/webapp:dev -t eywrld839/webapp:%build.number% -f ./utils/Docker/Dockerfile .
    ```
- Click **Save**.

### B1.4 Add 3rd Build Step - Docker Push
- **Name**: `Docker Push`
- **Runner Type**: Select **Docker**.
- **Docker Command**: Pick **Push**.
- **Image Name:Tag**:
    ```bash
    eywrld839/webapp:dev
    eywrld839/webapp:%build.number%
    ```
- Click **Save**.

### B1.5 Add 4th Build Step - Deploy
- **Name**: `Deploy`
- **Runner Type**: Select **Command Line**.
- **Custom Script**:
    ```bash
    export $(grep -v '^#' .env | xargs)
    sed -i '' "s/PLACEHOLDER_COLOR/$COLOR/g" ./utils/deployments/deployment-dev.yaml
    kubectl apply -f ./utils/deployments/deployment-dev.yaml
    kubectl set image deployment/web-app-dev web-app-container=eywrld839/webapp:%build.number% -n dev
    kubectl set image deployment/web-app-canary web-app-container=eywrld839/webapp:%build.number% -n prod
    ```
- Click **Save**.
