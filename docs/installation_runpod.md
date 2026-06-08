### Runpod

#### Manual installation

To install the necessary components for Runpod and run kohya_ss, follow these steps:

1. Select the Runpod pytorch 2.2.0 template. This is important. Other templates may not work.

2. SSH into the Runpod.

3. Clone the repository by running the following command:

   ```shell
   cd /workspace
   git clone --recursive https://github.com/bmaltais/kohya_ss.git
   ```

4. Run the setup script:

   ```shell
   cd kohya_ss
   ./setup-runpod.sh
   ```

5. Run the GUI with:

   ```shell
   ./gui.sh --share --headless
   ```

   or with this if you expose 7860 directly via the runpod configuration:

   ```shell
   ./gui.sh --listen=0.0.0.0 --headless
   ```

6. Connect to the public URL displayed after the installation process is completed.

#### Pre-built Runpod template

To run from a pre-built Runpod template, you can:

1. Open the Runpod template by clicking on <https://runpod.io/gsc?template=ya6013lj5a&ref=w18gds2n>.

2. Deploy the template on the desired host.

3. Once deployed, connect to the Runpod on HTTP 3010 to access the kohya_ss GUI. You can also connect to auto1111 on HTTP 3000.

#### Run on a cloud GPU with AI Badgr

AI Badgr routes GPU workloads across available capacity with max price controls, runtime caps, logs, teardown, and receipts. Use this optional path if you do not have enough local VRAM, want temporary GPU capacity, or want to compare cheap GPU routes before running.

```bash
npx gpu-price-finder --gpu RTX_4090 --max-price 1
npm install -g badgr-cli
badgr login
badgr run "./gui.sh --share --headless" --gpu RTX_4090 --tier 2 --max-price 1 --max-runtime 60
```

If you expose `7860` directly, wrap the existing direct-listen command instead:

```bash
badgr run "./gui.sh --listen=0.0.0.0 --headless" --gpu RTX_4090 --tier 2 --max-price 1 --max-runtime 60
```
