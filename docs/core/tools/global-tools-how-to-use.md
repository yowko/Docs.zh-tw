---
title: 教學課程：安裝和使用 .NET Core 通用工具
description: 瞭解如何安裝和使用 .NET 工具做為通用工具。
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156734"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

本教學課程會教您如何安裝和使用通用工具。 您會使用在[本系列的第一個教學](global-tools-how-to-create.md)課程中建立的工具。

## <a name="prerequisites"></a>Prerequisites

* 完成[此系列的第一個教學](global-tools-how-to-create.md)課程。

## <a name="use-the-tool-as-a-global-tool"></a>使用工具作為通用工具

1. 在*botsay*專案資料夾中執行[dotnet tool install](dotnet-tool-install.md)命令，以從套件安裝此工具：

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   `--global` 參數會告訴 .NET Core CLI 在自動新增至 PATH 環境變數的預設位置中安裝工具二進位檔。

   `--add-source` 參數會告訴 .NET Core CLI 暫時使用 */nupkg*目錄做為 NuGet 套件的額外來源摘要。 您為套件提供了唯一的名稱，以確保它只會在 */nupkg*目錄中找到，而不是在 Nuget.org 網站上。

   輸出會顯示用來呼叫工具和所安裝版本的命令：

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. 叫用工具：

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > 如果此命令失敗，您可能需要開啟新的終端機以重新整理路徑。

1. 執行[dotnet tool uninstall](dotnet-tool-uninstall.md)命令以移除此工具：

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>使用此工具作為自訂位置中安裝的通用工具

1. 從套件安裝工具。

   在 Windows 上：

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   在 Linux 或 macOS 上：

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   `--tool-path` 參數會告訴 .NET Core CLI 在指定的位置安裝工具二進位檔。 如果目錄不存在，則會建立它。 此目錄不會自動加入 PATH 環境變數中。

   輸出會顯示用來呼叫工具和所安裝版本的命令：

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

1. 執行[dotnet tool uninstall](dotnet-tool-uninstall.md)命令以移除此工具：

   在 Windows 上：

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   在 Linux 或 macOS 上：

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>疑難排解

如果您在教學課程之後收到錯誤訊息，請參閱針對[.Net Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已安裝並使用工具做為通用工具。 若要安裝和使用與本機工具相同的工具，請繼續進行下一個教學課程。

> [!div class="nextstepaction"]
> [安裝及使用本機工具](local-tools-how-to-use.md)
