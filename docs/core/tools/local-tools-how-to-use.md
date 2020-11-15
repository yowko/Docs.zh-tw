---
title: 教學課程：安裝和使用 .NET 本機工具
description: 瞭解如何安裝和使用 .NET 工具作為本機工具。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 2cb25443706293b66325d43136afcd3fd886294d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633877"
---
# <a name="tutorial-install-and-use-a-net-local-tool-using-the-net-cli"></a>教學課程：使用 .NET CLI 安裝和使用 .NET 本機工具

本文 **適用于：** ✔️ .net CORE 3.0 SDK 和更新版本

本教學課程會教您如何安裝和使用本機工具。 您可以使用您在 [本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。

## <a name="prerequisites"></a>先決條件

* 完成 [本系列的第一個教學](global-tools-how-to-create.md)課程。
* 安裝 .NET Core 2.1 執行時間。

  在本教學課程中，您會安裝並使用以 .NET Core 2.1 為目標的工具，因此您必須在電腦上安裝該執行時間。 若要安裝2.1 執行時間，請移至 [.Net Core 2.1 下載頁面](https://dotnet.microsoft.com/download/dotnet-core/2.1) ，並在 [ **執行應用程式-運行** 時間] 資料行中尋找執行時間安裝連結。

## <a name="create-a-manifest-file"></a>建立資訊清單檔

若要安裝僅限本機存取的工具 (針對目前的目錄和子目錄) ，必須將其新增至資訊清單檔案。

從 *botsay* 資料夾中，流覽至存放 *庫* 資料夾的其中一個層級：

```console
cd ..
```

藉由執行 [dotnet new](dotnet-new.md) 命令來建立資訊清單檔案：

```dotnetcli
dotnet new tool-manifest
```

輸出會指出檔案已成功建立。

```console
The template "Dotnet local tool manifest file" was created successfully.
```

檔案 *上的 .config/dotnet-tools.js* 還沒有工具：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

資訊清單檔中所列的工具可供目前的目錄和子目錄使用。 目前的目錄是包含 *.config* 目錄與資訊清單檔案的目錄。

當您使用參考本機工具的 CLI 命令時，SDK 會在目前目錄和父目錄中搜尋資訊清單檔案。 如果它找到資訊清單檔案，但檔案未包含參考的工具，它會繼續透過上層目錄進行搜尋。 當搜尋找到參考的工具，或找到的資訊清單檔案的設定為時，就會結束搜尋 `isRoot` `true` 。

## <a name="install-botsay-as-a-local-tool"></a>將 botsay 安裝為本機工具

從您在第一個教學課程中建立的套件安裝工具：

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

此命令會將工具新增至您在上一個步驟中建立的資訊清單檔案。 命令輸出會顯示新安裝的工具所在的資訊清單檔案：

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

檔案 *上的 .config/dotnet-tools.js* 現在有一項工具：

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

`dotnet tool run`從存放 *庫* 資料夾執行命令來叫用工具：

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a>還原其他人所安裝的本機工具

您通常會在存放庫的根目錄中安裝本機工具。 將資訊清單檔案簽入存放庫之後，其他開發人員就可以取得最新的資訊清單檔案。 若要安裝資訊清單檔案中列出的所有工具，可以執行單一 `dotnet tool restore` 命令。

1. 開啟檔案的 *.config/dotnet-tools.js* ，並將內容取代為下列 JSON：

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

1. 取代為 `<name>` 您用來建立專案的名稱。

1. 儲存您的變更。

   進行這項變更與從儲存機制取得最新版本的方式相同，就是在其他人安裝了專案目錄的封裝之後 `dotnetsay` 。

1. 執行 `dotnet tool restore` 命令。

   ```dotnetcli
   dotnet tool restore
   ```

   此命令會產生如下列範例所示的輸出：

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. 確認工具可供使用：

   ```dotnetcli
   dotnet tool list
   ```

   輸出是套件和命令的清單，類似于下列範例：

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

## <a name="update-a-local-tool"></a>更新本機工具

安裝的本機工具版本 `dotnetsay` 是2.1.3。  最新版本是2.1.4。 使用 [dotnet tool update](dotnet-tool-update.md) 命令將工具更新為最新版本。

```dotnetcli
dotnet tool update dotnetsay
```

輸出會指出新的版本號碼：

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

Update 命令會尋找包含封裝識別碼的第一個資訊清單檔，並加以更新。 如果搜尋範圍內的任何資訊清單檔中沒有這類套件識別碼，SDK 會將新專案新增至最接近的資訊清單檔案。 搜尋範圍會透過父目錄來執行，直到找到具有的資訊清單檔為止 `isRoot = true` 。

## <a name="remove-local-tools"></a>移除本機工具

執行 [dotnet tool uninstall](dotnet-tool-uninstall.md) 命令以移除已安裝的工具：

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a>疑難排解

如果您在遵循本教學課程時收到錯誤訊息，請參閱 [疑難排解 .net 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="see-also"></a>另請參閱

如需詳細資訊，請參閱[.Net Core 工具](global-tools.md)。
