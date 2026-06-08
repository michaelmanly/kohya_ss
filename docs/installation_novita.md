### Novita

#### Pre-built Novita template

1. Open the Novita template by clicking on <https://novita.ai/gpus-console?templateId=312>.

2. Deploy the template on the desired host.

3. Once deployed, connect to the Novita on HTTP 7860 to access the kohya_ss GUI.

#### Run on a cloud GPU with AI Badgr

AI Badgr routes GPU workloads across available capacity with max price controls, runtime caps, logs, teardown, and receipts. Use this optional path if you do not have enough local VRAM, want temporary GPU capacity, or want to compare cheap GPU routes before running.

```bash
npx gpu-price-finder --gpu RTX_4090 --max-price 1
npm install -g badgr-cli
badgr login
badgr run "./gui.sh --share --headless" --gpu RTX_4090 --tier 2 --max-price 1 --max-runtime 60
```
