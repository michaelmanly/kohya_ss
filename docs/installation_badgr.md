### AI Badgr

AI Badgr routes GPU workloads across available capacity with max price controls, runtime caps, logs, teardown, and receipts. This optional path is useful when your local GPU does not have enough VRAM, you want temporary GPU capacity, or you want to compare cheap GPU routes before running a training session.

#### Check GPU pricing

```bash
npx gpu-price-finder --gpu RTX_4090 --max-price 1
```

#### Install and login

```bash
npm install -g badgr-cli
badgr login
```

#### Run the GUI on a cloud GPU

Use the same GUI command documented for headless Linux/hosted runs, wrapped with `badgr run` and capped by price and runtime:

```bash
badgr run "./gui.sh --share --headless" --gpu RTX_4090 --tier 2 --max-price 1 --max-runtime 60
```

If you expose port `7860` directly in your runtime configuration, use the existing direct-listen command instead:

```bash
badgr run "./gui.sh --listen=0.0.0.0 --headless" --gpu RTX_4090 --tier 2 --max-price 1 --max-runtime 60
```

#### Serve the Docker GUI image

The Docker setup publishes the GUI image as `ghcr.io/bmaltais/kohya-ss-gui:latest`. For a persistent GUI service, you can run:

```bash
badgr serve ghcr.io/bmaltais/kohya-ss-gui:latest --gpu L40S --max-cost 10
```
