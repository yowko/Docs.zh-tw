---
title: 使用 Visual Studio 發佈您的 .NET Core Hello World 應用程式
description: 發行會建立一組執行您的 .NET Core 應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 745fb2af332afa278c78ec9baeea7230fe725c02
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241486"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a>教學課程：使用 Visual Studio 發行 .NET Core 主控台應用程式

本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。 發行會建立一組執行您的應用程式所需的檔案。 若要部署檔案，請將檔案複製到目的電腦。

## <a name="prerequisites"></a>Prerequisites

- 本教學課程適用于您在[Visual Studio 2019 的建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的主控台應用程式。

## <a name="publish-the-app"></a>發佈應用程式

1. 請確定 Visual Studio 正在組置您應用程式的發行版本。 如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. 以滑鼠右鍵按一下**HelloWorld**專案（而非 HelloWorld 方案），然後從功能表中選取 [**發佈**]。

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)

1. 在**發行**頁面的 [**目標**] 索引標籤上，選取 [**資料夾**]，然後選取 **[下一步]**。

   ![在 Visual Studio 中挑選發行目標](media/publishing-with-visual-studio/pick-publish-target.png)

1. 在 [**發佈**] 頁面的 [**位置**] 索引標籤上，選取 **[完成]**。

   ![Visual Studio 發行頁面位置] 索引標籤](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. 在 **[發行] 視窗的**[**發行**] 索引標籤上，選取 [**發佈**]。

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>檢查檔案

發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET Core 執行時間的電腦上執行。 使用者可以按兩下可執行檔，或從命令提示字元發出命令，以執行已發佈的應用程式 `dotnet HelloWorld.dll` 。

在下列步驟中，您將查看發行程式所建立的檔案。

1. 在**方案總管**中，選取 [**顯示所有**檔案]。

1. 在專案資料夾中，展開 [ *bin/Release/netcoreapp 3.1/publish*]。

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="顯示已發佈檔案的方案總管":::

   如圖所示，已發行的輸出會包含下列檔案：

   * *HelloWorld.deps.json*

      這是應用程式的執行時間相依性檔案。 它會定義執行應用程式所需的 .NET Core 元件和程式庫（包括包含您應用程式的動態連結程式庫）。 如需詳細資訊，請參閱[執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。

   * *HelloWorld.dll*

      這是與[framework 相依](../deploying/deploy-with-cli.md#framework-dependent-deployment)的應用程式部署版本。 若要執行此動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。 這種執行應用程式的方法可在已安裝 .NET Core 執行時間的任何平臺上運作。

   * *HelloWorld .exe*

      這是與[framework 相依的應用程式可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。 若要執行，請 `HelloWorld.exe` 在命令提示字元中輸入。 檔案是作業系統特定的檔案。

   * *HelloWorld.pdb* (對於部署為選用)

      這是 debug 符號檔案。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

   * *HelloWorld.runtimeconfig.json*

      這是應用程式的執行時間設定檔。 它會識別建置您應用程式以在其上執行的 .NET Core 版本。 您也可以在其中新增設定選項。 如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。

## <a name="run-the-published-app"></a>執行已發佈的應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下 [*發行*] 資料夾，然後選取 [**複製完整路徑**]。

1. 開啟命令提示字元，並流覽至 [*發行*] 資料夾。 輸入 `cd` ，然後貼上完整路徑。 例如：

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. 使用可執行檔來執行應用程式：

   1. 輸入 `HelloWorld.exe` ，然後按<kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵結束。

1. 使用命令執行應用程式 `dotnet` ：

   1. 輸入 `dotnet HelloWorld.dll` ，然後按<kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵結束。

## <a name="additional-resources"></a>其他資源

- [.NET Core 應用程式部署](../deploying/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已發佈主控台應用程式。 在下一個教學課程中，您會建立類別庫。

> [!div class="nextstepaction"]
> [在 Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)
