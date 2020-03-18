---
title: 教程：安裝和使用 .NET 核心全域工具
description: 瞭解如何安裝和使用 .NET 工具作為全域工具。
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156734"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

本教程將教您如何安裝和使用全域工具。 使用在本[系列的第一個教程](global-tools-how-to-create.md)中創建的工具。

## <a name="prerequisites"></a>必要條件

* 完成[本系列的第一個教程](global-tools-how-to-create.md)。

## <a name="use-the-tool-as-a-global-tool"></a>將該工具用作全域工具

1. 通過在*microsoft.botsay*專案資料夾中運行[dotnet 工具安裝](dotnet-tool-install.md)命令，從包中安裝該工具：

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   該`--global`參數告訴 .NET Core CLI 在自動添加到 PATH 環境變數的預設位置安裝工具二進位檔案。

   該`--add-source`參數告訴 .NET Core CLI 暫時使用 *./nupkg*目錄作為 NuGet 包的附加源源。 您為包指定了一個唯一的名稱，以確保它僅在 *./nupkg*目錄中找到，而不是在Nuget.org網站中找到。

   輸出顯示用於調用該工具的命令和安裝的版本：

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. 調用該工具：

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > 如果此命令失敗，您可能需要打開一個新終端來刷新 PATH。

1. 通過運行[dotnet 工具卸載](dotnet-tool-uninstall.md)命令移除工具：

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>將該工具用作安裝在自訂位置的全域工具

1. 從包安裝該工具。

   在 Windows 上：

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   在 Linux 或 macOS 上：

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   該`--tool-path`參數告訴 .NET 核心 CLI 在指定位置安裝工具二進位檔案。 如果目錄不存在，則創建該目錄。 此目錄不會自動添加到 PATH 環境變數。

   輸出顯示用於調用該工具的命令和安裝的版本：

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. 調用該工具：

   在 Windows 上：

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   在 Linux 或 macOS 上：

   ```console
   ~/bin/botsay hello from the bot
   ```

1. 通過運行[dotnet 工具卸載](dotnet-tool-uninstall.md)命令移除工具：

   在 Windows 上：

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   在 Linux 或 macOS 上：

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>疑難排解

如果您在學習本教程時收到錯誤訊息，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="next-steps"></a>後續步驟

在本教程中，您安裝並使用了工具作為全域工具。 要安裝和使用與本地工具相同的工具，請先進行下一個教程。

> [!div class="nextstepaction"]
> [安裝和使用本地工具](local-tools-how-to-use.md)
