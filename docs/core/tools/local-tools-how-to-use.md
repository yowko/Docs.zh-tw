---
title: 教程：安裝和使用 .NET 核心本地工具
description: 瞭解如何安裝和使用 .NET 工具作為本地工具。
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156695"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具

**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本

本教程將教您如何安裝和使用本地工具。 使用在本[系列的第一個教程](global-tools-how-to-create.md)中創建的工具。

## <a name="prerequisites"></a>必要條件

* 完成[本系列的第一個教程](global-tools-how-to-create.md)。
* 安裝 .NET 核心 2.1 運行時。

  在本教程中，您可以安裝並使用以 .NET Core 2.1 為目標的工具，因此需要在電腦上安裝該運行時。 要安裝 2.1 運行時，請轉到[.NET Core 2.1 下載頁面](https://dotnet.microsoft.com/download/dotnet-core/2.1)，並在 **"運行應用 - 運行時**"列中找到運行時安裝連結。

## <a name="create-a-manifest-file"></a>創建清單檔

要僅安裝本地訪問工具（對於目前的目錄和子目錄），必須將其添加到清單檔中。

從*Microsoft.botsay*資料夾，向上導航一個級別到*存儲庫*資料夾：

```console
cd ..
```

通過運行[dotnet 新](dotnet-new.md)命令創建清單檔：

```dotnetcli
dotnet new tool-manifest
```

輸出指示檔成功創建。

```console
The template "Dotnet local tool manifest file" was created successfully.
```

*.config/dotnet-tools.json*檔中尚未包含任何工具：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

清單檔中列出的工具可用於目前的目錄和子目錄。 目前的目錄是包含包含清單檔的 *.config*目錄的目錄。

當您使用引用本地工具的 CLI 命令時，SDK 將搜索目前的目錄和父目錄中的清單檔。 如果它找到清單檔，但該檔不包括引用的工具，它將通過父目錄繼續搜索。 搜索在找到引用的工具或找到設置為`isRoot``true`的清單檔時結束。

## <a name="install-botsay-as-a-local-tool"></a>將僵屍資訊作為本地工具安裝

從第一個教程中創建的包安裝該工具：

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

此命令將該工具添加到您在上一步中創建的清單檔中。 命令輸出顯示新安裝的工具的清單檔位於：

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

*.config/dotnet 工具.json*檔現在有一個工具：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>使用工具

通過從`dotnet tool run`*存儲庫*資料夾中運行命令來調用該工具：

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>還原其他人安裝的本地工具

通常在存儲庫的根目錄中安裝本地工具。 將清單檔簽入存儲庫後，其他開發人員可以獲取最新的清單檔。 要安裝清單檔中列出的所有工具，它們可以運行單個`dotnet tool restore`命令。

1. 打開 *.config/dotnet 工具.json*檔，並將內容替換為以下 JSON：

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. 替換為`<name>`用於創建專案的名稱。

1. 儲存您的變更。

   進行此更改與在其他人為專案目錄安裝包`dotnetsay`後從存儲庫獲取最新版本相同。

1. 執行 `dotnet tool restore` 命令。

   ```dotnetcli
   dotnet tool restore
   ```

   該命令生成輸出，如下所示：

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. 驗證這些工具是否可用：

   ```dotnetcli
   dotnet tool list
   ```

   輸出是包和命令的清單，類似于以下示例：

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. 測試控管：

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>更新本地工具

本地工具`dotnetsay`的已安裝版本為 2.1.3。  最新版本為 2.1.4。 使用[dotnet 工具更新](dotnet-tool-update.md)命令將該工具更新到最新版本。

```dotnetcli
dotnet tool update dotnetsay
```

輸出指示新版本號：

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

更新命令查找包含包 ID 並更新它的第一個清單檔。 如果在搜尋範圍內的任何清單檔中沒有此類包 ID，SDK 會向最近的清單檔添加新條目。 搜尋範圍通過父目錄向上，直到找到 具有 的`isRoot = true`清單檔。

## <a name="remove-local-tools"></a>刪除本地工具

通過運行[dotnet 工具卸載](dotnet-tool-uninstall.md)命令刪除已安裝的工具：

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>疑難排解

如果您在學習本教程時收到錯誤訊息，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="see-also"></a>另請參閱

有關詳細資訊，請參閱[.NET 核心工具](global-tools.md)
