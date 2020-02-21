---
title: 教學課程：安裝和使用 .NET Core 本機工具
description: 瞭解如何安裝和使用 .NET 工具做為本機工具。
ms.date: 02/12/2020
ms.openlocfilehash: 6de620772cec1e9d1b1f57380b72c0163d68337c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543863"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a>教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具

**本文適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

本教學課程會教您如何安裝和使用本機工具。 您會使用在[本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。

## <a name="prerequisites"></a>Prerequisites

* 完成[此系列的第一個教學](global-tools-how-to-create.md)課程。
* 安裝 .NET Core 2.1 執行時間。

  在本教學課程中，您會安裝並使用以 .NET Core 2.1 為目標的工具，因此您必須在電腦上安裝該執行時間。 若要安裝2.1 執行時間，請移至[.Net Core 2.1 下載頁面](https://dotnet.microsoft.com/download/dotnet-core/2.1)，並在 [**執行應用程式-運行**時間] 資料行中尋找執行時間安裝連結。

## <a name="create-a-manifest-file"></a>建立資訊清單檔

若要安裝僅限本機存取的工具（針對目前的目錄和子目錄），必須將它新增至資訊清單檔。 

從*botsay\<名稱 >*  資料夾中，流覽至 存放*庫* 資料夾的一個層級：

```console
cd ..
```

藉由執行[dotnet new](dotnet-new.md)命令來建立資訊清單檔：

```dotnetcli
dotnet new tool-manifest
```

輸出表示檔案建立成功。

```console
The template "Dotnet local tool manifest file" was created successfully.
```

*.Config/dotnet-tools*檔案尚未提供任何工具：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

資訊清單檔案中所列的工具可供目前的目錄和子目錄使用。 目前目錄是包含 *.config*目錄和資訊清單檔案的目錄。

當您使用參考本機工具的 CLI 命令時，SDK 會搜尋目前目錄和上層目錄中的資訊清單檔案。 如果找到資訊清單檔案，但檔案未包含參考的工具，它會繼續透過父目錄進行搜尋。 搜尋會在找到參考的工具或找到 `isRoot` 設定為 `true`的資訊清單檔案時結束。

## <a name="install-botsay-as-a-local-tool"></a>以本機工具安裝 botsay

從您在第一個教學課程中建立的套件安裝此工具：

```dotnetcli
dotnet tool install --add-source ./botsay-<name>/nupkg botsay-<name>
```

此命令會將工具新增至您在上一個步驟中建立的資訊清單檔案。 命令輸出會顯示新安裝工具所在的資訊清單檔案：

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

*.Config/dotnet-tools*檔案現在有一項工具：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay-<name>": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a>使用工具

從存放*庫*資料夾執行 `dotnet tool run` 命令來叫用工具：

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>還原其他人所安裝的本機工具

您通常會在存放庫的根目錄中安裝本機工具。 將資訊清單檔簽入至存放庫之後，其他開發人員就可以取得最新的資訊清單檔。 若要安裝資訊清單檔案中列出的所有工具，可以執行單一 `dotnet tool restore` 命令。

1. 開啟 *.config/dotnet-tools*檔案，並將內容取代為下列 json：

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "botsay-<name>": {
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

1. 以您用來建立專案的名稱取代 `<name>`。

1. 儲存您的變更。

   進行這種變更的方式與從存放庫取得最新版本，在其他人安裝了專案目錄的封裝 `dotnetsay`。 

1. 執行 `dotnet tool restore` 命令。

   ```dotnetcli
   dotnet tool restore
   ```

   命令會產生如下列範例所示的輸出：

   ```console
   Tool 'botsay-<name>' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. 確認工具可供使用：

   ```dotnetcli
   dotnet tool list
   ```

   輸出是封裝和命令的清單，類似于下列範例：

   ```console
   Package Id      Version      Commands       Manifest
   -------------------------------------------------------------------------------------------
   botsay-<name>   1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. 測試控管：

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a>更新本機工具

已安裝的本機工具 `dotnetsay` 版本為2.1.3。  最新版本是2.1.4。 使用[dotnet tool update](dotnet-tool-update.md)命令將工具更新為最新版本。

```dotnetcli
dotnet tool update dotnetsay
```

輸出會顯示新的版本號碼：

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Update 命令會尋找包含封裝識別碼的第一個資訊清單檔案，並加以更新。 如果在搜尋範圍內的任何資訊清單檔案中沒有此類套件識別碼，SDK 就會將新專案新增至最接近的資訊清單檔案。 搜尋範圍會透過父目錄來啟動，直到找到具有 `isRoot = true` 的資訊清單檔案為止。

## <a name="remove-local-tools"></a>移除本機工具

執行[dotnet tool uninstall](dotnet-tool-uninstall.md)命令以移除已安裝的工具：

```dotnetcli
dotnet tool uninstall botsay-<name>
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>疑難排解

如果您在教學課程之後收到錯誤訊息，請參閱針對[.Net Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。

## <a name="see-also"></a>另請參閱

如需詳細資訊，請參閱[.Net Core 工具](global-tools.md)
