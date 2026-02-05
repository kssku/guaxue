import requests
import json
from pathlib import Path

# ========= 配置区 =========

# 你要刮取的 GitHub 原始文件（示例）
TARGET_URL = "https://raw.githubusercontent.com/OWNER/REPO/BRANCH/FILE"

OUTPUT_PATH = Path("data/result.json")

# ========= 抓取 =========

def fetch():
    resp = requests.get(TARGET_URL, timeout=30)
    resp.raise_for_status()
    return resp.text

# ========= 主逻辑 =========

def main():
    content = fetch()

    OUTPUT_PATH.parent.mkdir(parents=True, exist_ok=True)

    data = {
        "source": TARGET_URL,
        "length": len(content),
        "preview": content[:200]
    }

    with open(OUTPUT_PATH, "w", encoding="utf-8") as f:
        json.dump(data, f, ensure_ascii=False, indent=2)

    print("抓取并写入完成")

if __name__ == "__main__":
    main()
