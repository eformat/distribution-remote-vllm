# LlamaStack custom build

Clone upstream

```bash
git clone git@github.com:llamastack/llama-stack.git llama-stack
```

Change dir

```bash
cd ~/git/llama-stack
```

Build llama-stack using podman

```bash
export USE_COPY_NOT_MOUNT="true"
export LLAMA_STACK_DIR="."
export CONTAINER_BINARY=podman
```

Copy our ubi based build file

```bash
cp build.yaml llama_stack/templates/ci-tests/build.yaml
```

Build image

```bash
uv run llama stack build --config llama_stack/templates/ci-tests/build.yaml
```

Tag and push image

```bash
podman tag localhost/ubi9-test:dev quay.io/eformat/distribution-remote-vllm:latest
podman push quay.io/eformat/distribution-remote-vllm:latest
```
