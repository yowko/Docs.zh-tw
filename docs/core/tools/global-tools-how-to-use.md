---
title: 教學課程：安裝和使用 .NET 通用工具
description: 瞭解如何安裝和使用 .NET 工具作為全域工具。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 01b773516da92fb16fb0f67fc6617e0c70d17c9d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633890"
---
# <a name="tutorial-install-and-use-a-net-global-tool-using-the-net-cli"></a>教學課程：使用 .NET CLI 安裝和使用 .NET 通用工具

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

本教學課程會教您如何安裝和使用全域工具。 您可以使用您在 [本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。

## <a name="prerequisites"></a>先決條件

* 完成 [本系列的第一個教學](global-tools-how-to-create.md)課程。

## <a name="use-the-tool-as-a-global-tool"></a>使用工具作為通用工具

1. 在 *botsay* 專案資料夾中執行 [dotnet tool install](dotnet-tool-install.md)命令，以從套件安裝此工具：

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   `--global`參數會指示 .NET CLI 將工具二進位檔安裝在預設位置，該位置會自動新增至 PATH 環境變數。

   `--add-source`參數會指示 .NET CLI 暫時使用 */nupkg* 目錄作為 NuGet 套件的其他來源摘要。 您為套件提供了唯一的名稱，以確保它只會在 */nupkg* 目錄中，而不會在 Nuget.org 網站上找到。

   輸出會顯示用來呼叫工具和安裝版本的命令：

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. 叫用工具：

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > 如果此命令失敗，您可能需要開啟新的終端機才能重新整理路徑。

1. 執行 [dotnet tool uninstall](dotnet-tool-uninstall.md) 命令以移除此工具：

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>使用工具作為在自訂位置安裝的通用工具

1. 從套件安裝此工具。

   在 Windows 上：

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   在 Linux 或 macOS 上：

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   `--tool-path`參數會指示 .NET CLI 將工具二進位檔安裝在指定的位置。 如果目錄不存在，則會建立該目錄。 此目錄不會自動新增至 PATH 環境變數。

   輸出會顯示用來呼叫工具和安裝版本的命令：

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. 叫用工具：

   在 Windows 上：

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   在 Linux 或 macOS 上：

   ```console
   ~/bin/botsay hello from the bot
   ```

1. 執行 [dotnet tool uninstall](dotnet-tool-uninstall.md) 命令以移除此工具：

   在 Windows 上：

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   在 Linux 或 macOS 上：

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>疑難排解

如果您在遵循本教學課程時收到錯誤訊息，請參閱 [疑難排解 .net 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已安裝並使用工具作為全域工具。 若要安裝和使用相同的工具作為本機工具，請繼續進行下一個教學課程。

> [!div class="nextstepaction"]
> [安裝和使用本機工具](local-tools-how-to-use.md)
