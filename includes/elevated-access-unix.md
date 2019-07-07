---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540094"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="8a4e6-101">安裝全域工具</span><span class="sxs-lookup"><span data-stu-id="8a4e6-101">Install the global tool</span></span>

<span data-ttu-id="8a4e6-102">您應該使用 `--tool-path` 選項，將套件資產安裝在受保護的位置。</span><span class="sxs-lookup"><span data-stu-id="8a4e6-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="8a4e6-103">這種區隔可避免將受限制使用者環境與提升權限的環境共用。</span><span class="sxs-lookup"><span data-stu-id="8a4e6-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="8a4e6-104">系統會建立具有 `drwxr-xr-x` 權限的 `/usr/local/share/dotnet-tools`。</span><span class="sxs-lookup"><span data-stu-id="8a4e6-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="8a4e6-105">如果目錄已存在，請使用 `ls -l` 命令驗證受限制使用者沒有編輯目錄的權限。</span><span class="sxs-lookup"><span data-stu-id="8a4e6-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="8a4e6-106">如果有，請使用 `sudo chmod o-w -R /usr/share/dotnet-tools` 命令來移除存取權。</span><span class="sxs-lookup"><span data-stu-id="8a4e6-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="8a4e6-107">執行全域工具</span><span class="sxs-lookup"><span data-stu-id="8a4e6-107">Run the global tool</span></span>

<span data-ttu-id="8a4e6-108">**選項 1**：搭配 sudo 使用完整路徑：</span><span class="sxs-lookup"><span data-stu-id="8a4e6-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="8a4e6-109">**選項 2**：新增工具的符號連結，每個工具一次：</span><span class="sxs-lookup"><span data-stu-id="8a4e6-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="8a4e6-110">然後使用以下項目執行：</span><span class="sxs-lookup"><span data-stu-id="8a4e6-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="8a4e6-111">解除安裝全域工具</span><span class="sxs-lookup"><span data-stu-id="8a4e6-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="8a4e6-112">如果您已經建立符號連結，您也需要將其移除：</span><span class="sxs-lookup"><span data-stu-id="8a4e6-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
