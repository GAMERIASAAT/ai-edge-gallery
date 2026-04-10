# Google AI Edge Gallery ✨

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Build Android APK](https://github.com/GAMERIASAAT/ai-edge-gallery/actions/workflows/build_android.yaml/badge.svg)](https://github.com/GAMERIASAAT/ai-edge-gallery/actions/workflows/build_android.yaml)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/google-ai-edge/gallery)](https://github.com/google-ai-edge/gallery/releases)

**Explore, Experience, and Evaluate the Future of On-Device Generative AI with Google AI Edge.**

AI Edge Gallery is the premier destination for running the world's most powerful open-source Large Language Models (LLMs) on your mobile device. Experience high-performance Generative AI directly on your hardware—fully offline, private, and lightning-fast.

> **This fork** extends the upstream Google AI Edge Gallery with additional features:
> [Termux code execution](#-run-code-in-termux-new), [Metasploit RPC agent](#-metasploit-agent-new), and [Snapdragon NPU acceleration](#-snapdragon-npu-acceleration-new).

**Now Featuring: Gemma 4**

The latest version brings official support for the newly released Gemma 4 family. As the centerpiece of this release, Gemma 4 allows you to test the cutting edge of on-device AI. Experience advanced reasoning, logic, and creative capabilities without ever sending your data to a server.


| **Install the app today from Google Play** | **Install the app today from App Store** |
| :--- | :--- |
| <a href='https://play.google.com/store/apps/details?id=com.google.ai.edge.gallery'><img alt='Get it on Google Play' height="120" src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png'/></a> | <a href="https://apps.apple.com/us/app/google-ai-edge-gallery/id6749645337?itscg=30200&itsct=apps_box_badge&mttnsubad=6749645337" style="display: inline-block;"> <img src="https://toolbox.marketingtools.apple.com/api/v2/badges/download-on-the-app-store/black/en-us?releaseDate=1771977600" alt="Download on the App Store" style="width: 246px; height: 90px; vertical-align: middle; object-fit: contain;" /></a> |

For users without Google Play access, install the apk from the [**latest release**](https://github.com/google-ai-edge/gallery/releases/latest/)


## App Preview

<img width="480" alt="01" src="https://github.com/user-attachments/assets/a809ad78-aef4-4169-91ee-de7213cbb3bd" />
<img width="480" alt="02" src="https://github.com/user-attachments/assets/1effd10d-f45a-4f7b-9435-f50f1bdd36b6" />
<img width="480" alt="03" src="https://github.com/user-attachments/assets/e5089e41-2c18-4fbe-9011-ebe9e5a02044" />
<img width="480" alt="04" src="https://github.com/user-attachments/assets/0f39d3ed-7403-4606-a7c6-b2c7e51ba6c1" />
<img width="480" alt="05" src="https://github.com/user-attachments/assets/8c229e96-b598-4735-9f60-e96907e1d5d5" />
<img width="480" alt="06" src="https://github.com/user-attachments/assets/ac9fb77b-81de-4197-9ed3-f6fe58290b3e" />
<img width="480" alt="07" src="https://github.com/user-attachments/assets/bc86ba07-2eaf-49b1-980f-8a87a85c596f" />
<img width="480" alt="08" src="https://github.com/user-attachments/assets/061564ed-030f-4630-810b-13a7863fce4c" />

## ✨ Core Features

* **Agent Skills**: Transform your LLM from a conversationalist into a proactive assistant. Use the Agent Skills tile to augment model capabilities with tools like Wikipedia for fact-grounding, interactive maps, and rich visual summary cards. You can even load modular skills from a URL or browse community contributions on GitHub Discussions.

* **AI Chat with Thinking Mode**: Engage in fluid, multi-turn conversations and toggle the new Thinking Mode to peek "under the hood." This feature allows you to see the model's step-by-step reasoning process, which is perfect for understanding complex problem-solving. Note: Thinking Mode currently works with supported models, starting with the Gemma 4 family.

* **Ask Image**: Use multimodal power to identify objects, solve visual puzzles, or get detailed descriptions using your device's camera or photo gallery.

* **Audio Scribe**: Transcribe and translate voice recordings into text in real-time using high-efficiency on-device language models.

* **Prompt Lab**: A dedicated workspace to test different prompts and single-turn use cases with granular control over model parameters like temperature and top-k.

* **Mobile Actions**: Unlock offline device controls and automated tasks powered entirely by a finetune of FuntionGemma 270m.

* **Tiny Garden**: A fun, experimental mini-game that uses natural language to plant and harvest a virtual garden using a finetune of FunctionGemma 270m.

* **Model Management & Benchmark**: Gallery is a flexible sandbox for a wide variety of open-source models. Easily download models from the list or load your own custom models. Manage your model library effortlessly and run benchmark tests to understand exactly how each model performs on your specific hardware.

* **100% On-Device Privacy**: All model inferences happen directly on your device hardware. No internet is required, ensuring total privacy for your prompts, images, and sensitive data.

---

## 🆕 Fork-Specific Features

### 🖥️ Run Code in Termux *(new)*

The **Agent Chat** tile gains a new built-in skill — **Run in Termux** — that lets the LLM execute shell commands and code snippets directly inside the [Termux](https://termux.dev) terminal emulator on your Android device.

**Supported languages (anything installed in Termux):**
- `bash` / `sh`
- `python3`
- `node` (Node.js)
- `ruby`, `perl`, and more

**How it works:**
1. Make sure Termux is installed and has granted the `RUN_COMMAND` permission to this app.
2. Open the **Agent Chat** task and select or enable the **Run in Termux** skill.
3. Ask the LLM to run code: *"Run a Python script that prints today's date"* or *"Install numpy in Termux"*.
4. The LLM calls the `runTermuxCommand` tool, which fires a Termux `RUN_COMMAND` intent, and the terminal opens with the output.

**Termux setup:**
```bash
# In Termux, allow other apps to run commands:
# Settings → Apps → Termux → Permissions → Run commands in Termux from other apps → Allow
```

---

### 🔒 Metasploit Agent *(new)*

A dedicated **Metasploit Agent** task that lets the on-device LLM control a running [Metasploit Framework](https://www.metasploit.com/) instance via its JSON RPC API (`msfrpcd`) — no shell required.

**Capabilities:**
| Tool | Description |
|------|-------------|
| `msfConnect` | Authenticate to a running `msfrpcd` service |
| `msfConsoleCommand` | Run any msfconsole command and capture output |
| `msfSearchModules` | Search modules by keyword, CVE, platform, or type |
| `msfModuleInfo` / `msfModuleOptions` | Inspect module details and configurable options |
| `msfExecuteModule` | Launch a module as a background job |
| `msfListSessions` / `msfSessionCommand` | Interact with active shell/meterpreter sessions |
| `msfListJobs` / `msfKillJob` | Manage background jobs |

**Setup:**
```bash
# Start msfrpcd in Termux (no SSL, port 55553):
msfrpcd -P yourpassword -U msf -n -f
```

Then open the **Metasploit Agent** task in the app and tell the LLM:
> *"Connect to Metasploit on localhost with password yourpassword, then search for EternalBlue exploits."*

> **For authorized security testing and educational use only.** Only target systems you own or have explicit written permission to test.

---

### ⚡ Snapdragon NPU Acceleration *(new)*

On devices with a **Qualcomm Snapdragon** SoC, the app automatically detects the NPU (Neural Processing Unit) and adds it as the **default accelerator** option for all LLM tasks.

**Supported chips:**
- Modern: Any SoC with the `SM` prefix (SM8650 = Snapdragon 8 Gen 3, SM8550 = 8 Gen 2, etc.)
- Legacy: `kona` (865/865+), `lahaina` (888/888+), `taro` (8 Gen 1), `waipio` (8+ Gen 1), `kalama` (8 Gen 2), `pineapple` (8 Gen 3), `sun` (8 Elite)

When a Snapdragon SoC is detected, NPU appears first in the Accelerator selector in model settings. You can still fall back to GPU or CPU manually.

---

## 🏁 Get Started in Minutes!

1. **Check OS Requirement**: Android 12 and up, and iOS 17 and up.
2.  **Download the App:**
    - Install the app from [Google Play](https://play.google.com/store/apps/details?id=com.google.ai.edge.gallery) or [App Store](https://apps.apple.com/us/app/google-ai-edge-gallery/id6749645337).
    - For users without Google Play access: install the apk from the [**latest release**](https://github.com/google-ai-edge/gallery/releases/latest/)
    - Or build from this fork and download the APK from [GitHub Actions](https://github.com/GAMERIASAAT/ai-edge-gallery/actions/workflows/build_android.yaml).
3.  **Install & Explore:** For detailed installation instructions (including for corporate devices) and a full user guide, head over to our [**Project Wiki**](https://github.com/google-ai-edge/gallery/wiki)!

## 🛠️ Technology Highlights

*   **Google AI Edge:** Core APIs and tools for on-device ML.
*   **LiteRT:** Lightweight runtime for optimized model execution.
*   **Hugging Face Integration:** For model discovery and download.
*   **Termux Integration:** Run any code on-device via the Termux terminal.
*   **Metasploit RPC API:** Structured JSON-RPC control of Metasploit Framework.
*   **Snapdragon NPU:** Hardware-accelerated inference on Qualcomm devices.

## ⌨️ Development

Check out the [development notes](DEVELOPMENT.md) for instructions about how to build the app locally.

## 🤝 Feedback

This is an **experimental Beta release**, and your input is crucial!

*   🐞 **Found a bug?** [Report it here!](https://github.com/google-ai-edge/gallery/issues/new?assignees=&labels=bug&template=bug_report.md&title=%5BBUG%5D)
*   💡 **Have an idea?** [Suggest a feature!](https://github.com/google-ai-edge/gallery/issues/new?assignees=&labels=enhancement&template=feature_request.md&title=%5BFEATURE%5D)

## 📄 License

Licensed under the Apache License, Version 2.0. See the [LICENSE](LICENSE) file for details.

## 🔗 Useful Links

*   [**Project Wiki (Detailed Guides)**](https://github.com/google-ai-edge/gallery/wiki)
*   [Hugging Face LiteRT Community](https://huggingface.co/litert-community)
*   [LiteRT-LM](https://github.com/google-ai-edge/LiteRT-LM)
*   [Google AI Edge Documentation](https://ai.google.dev/edge)
*   [Termux](https://termux.dev)
*   [Metasploit Framework](https://www.metasploit.com/)
