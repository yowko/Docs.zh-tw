---
title: 使用 Visual Studio Code 發佈 .NET Core 主控台應用程式
description: 發行會建立一組執行 .NET Core 應用程式所需的檔案。
ms.date: 07/04/2020
ms.openlocfilehash: a84e66126806e2ab45c14527df1b931fa9980468
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867642"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a>教學課程：使用 Visual Studio Code 發佈 .NET Core 主控台應用程式

本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。 發行會建立一組執行應用程式所需的檔案。 若要部署檔案，請將檔案複製到目的電腦。

.NET Core CLI 用來發佈應用程式，因此您可以在此教學課程中，使用除了 Visual Studio Code 的程式碼編輯器。

## <a name="prerequisites"></a>先決條件

- 本教學課程適用于您 [使用 Visual Studio Code 建立 .Net Core 主控台應用程式](with-visual-studio-code.md)中所建立的主控台應用程式。

## <a name="publish-the-app"></a>發佈應用程式

1. 啟動 Visual Studio Code。

1. 開啟您在[使用 Visual Studio Code 建立 .Net Core 主控台應用程式](with-visual-studio-code.md)中建立的*HelloWorld*專案資料夾。

1. 從主功能表選擇 [ **View**  >  **Terminal** ]。

   終端機會在 *HelloWorld* 資料夾中開啟。

1. 執行下列命令：

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   預設組建設定為 *Debug*，所以此命令會指定 *發行* 組建設定。 發行組建設定的輸出具有最基本的符號 debug 資訊，並且已完全優化。

   命令輸出會類似下列範例：

   ```output
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a>檢查檔案

根據預設，發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET Core 執行時間的電腦上執行。 若要執行已發佈的應用程式，您可以使用可執行檔，或 `dotnet HelloWorld.dll` 從命令提示字元執行命令。

在下列步驟中，您將查看發佈程式所建立的檔案。

1. 在左側導覽列中選取 [ **Explorer** ]。

1. 展開 *bin/Release/netcoreapp 3.1/publish*。

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="顯示已發佈檔案的 Explorer":::

   如圖所示，已發行的輸出包含下列檔案：

   * *HelloWorld.deps.json*

      這是應用程式的執行時間相依性檔案。 它會定義 .NET Core 元件和程式庫 (包括動態連結程式庫，其中包含執行應用程式所需的應用程式) 。 如需詳細資訊，請參閱 [執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。

   * *HelloWorld.dll*

      這是應用程式的 [framework 相依部署](../deploying/deploy-with-cli.md#framework-dependent-deployment) 版本。 若要執行這個動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。 執行應用程式的這個方法適用于已安裝 .NET Core 執行時間的任何平臺。

   * *HelloWorld.exe* Linux 上的 (*HelloWorld* ，而不是在 macOS 上建立。 ) 

      這是應用程式的 [framework 相依可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable) 版本。 檔案是作業系統特定的。

   * *HelloWorld.pdb* (對於部署為選用)

      這是 debug 符號檔。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

   * *HelloWorld.runtimeconfig.json*

      這是應用程式的執行時間設定檔案。 它會識別建置您應用程式以在其上執行的 .NET Core 版本。 您也可以將設定選項新增至其中。 如需詳細資訊，請參閱 [.Net Core 執行時間配置設定](../run-time-config/index.md#runtimeconfigjson)。

## <a name="run-the-published-app"></a>執行已發佈的應用程式

1. 在 [ **Explorer**] 中，以滑鼠右鍵按一下 [ *發佈* ] 資料夾 (<kbd>Ctrl</kbd>-按一下 macOS) ，然後選取 [ **在終端機中開啟**]。

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="顯示在終端機中開啟的內容功能表":::

1. 在 Windows 或 Linux 上，使用可執行檔來執行應用程式。

   1. 在 Windows 上輸入， `.\HelloWorld.exe` 然後按 <kbd>enter</kbd>鍵。

   1. 在 Linux 上，輸入 `./HelloWorld` ，然後按 <kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵以結束。

1. 在任何平臺上，使用下列命令來執行應用程式  [`dotnet`](../tools/dotnet.md) ：

   1. 輸入 `dotnet HelloWorld.dll` ，然後按 <kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵以結束。

## <a name="additional-resources"></a>其他資源

- [.NET Core 應用程式部署](../deploying/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已發佈主控台應用程式。 在下一個教學課程中，您將建立類別庫。

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 建立 .NET Standard 程式庫](library-with-visual-studio-code.md)
