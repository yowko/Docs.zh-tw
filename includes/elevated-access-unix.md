---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424702"
---
### <a name="install-the-global-tool"></a>安裝全域工具

您應該使用 `--tool-path` 選項，將套件資產安裝在受保護的位置。 這種區隔可避免將受限制使用者環境與提升權限的環境共用。

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

系統會建立具有 `drwxr-xr-x` 權限的 `/usr/local/share/dotnet-tools`。 如果目錄已存在，請使用 `ls -l` 命令驗證受限制使用者沒有編輯目錄的權限。 如果有，請使用 `sudo chmod o-w -R /usr/share/dotnet-tools` 命令來移除存取權。

### <a name="run-the-global-tool"></a>執行全域工具

**選項 1**：搭配 sudo 使用完整路徑：

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**選項 2**：新增工具的符號連結，每個工具一次：

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

然後使用以下項目執行：

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>解除安裝全域工具

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

如果您已經建立符號連結，您也需要將其移除：

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```