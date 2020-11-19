---
title: 使用 Visual Studio 發佈 .NET 主控台應用程式
description: 瞭解如何使用 Visual Studio 來建立執行 .NET 應用程式所需的一組檔案。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: b0c6bd85ddf86f0eb11c56f01abb74a7e9786363
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915997"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio"></a>教學課程：使用 Visual Studio 發佈 .NET 主控台應用程式

本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。 發行會建立一組執行您的應用程式所需的檔案。 若要部署檔案，請將檔案複製到目的電腦。

## <a name="prerequisites"></a>先決條件

- 本教學課程適用于您 [使用 Visual Studio 建立 .net 主控台應用程式](with-visual-studio.md)中所建立的主控台應用程式。

## <a name="publish-the-app"></a>發佈應用程式

1. 啟動 Visual Studio。

1. 開啟您在 [使用 Visual Studio 建立 .net 主控台應用程式](with-visual-studio.md)中建立的 *HelloWorld* 專案。

1. 請確定 Visual Studio 使用發行組建設定。 如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。

   :::image type="content" source="media/publishing-with-visual-studio/visual-studio-toolbar-release.png" alt-text="選取 [發行] 組建的 Visual Studio 工具列":::

1. 以滑鼠右鍵按一下 **HelloWorld** 專案， (不是 HelloWorld 方案) 然後從功能表中選取 [ **發行** ]。

   :::image type="content" source="media/publishing-with-visual-studio/publish-context-menu.png" alt-text="Visual Studio [發行] 操作功能表":::

1. 在 [**發行**] 頁面的 [**目標**] 索引標籤上選取 [**資料夾**]，然後選取 **[下一步]**。

   :::image type="content" source="media/publishing-with-visual-studio/pick-publish-target.png" alt-text="在 Visual Studio 中挑選發佈目標":::

1. 在 [**發行**] 頁面的 **特定目標** 索引標籤上，選取 [**資料夾**]，然後選取 **[下一步**]。

   :::image type="content" source="media/publishing-with-visual-studio/pick-specific-publish-target.png" alt-text="在 Visual Studio 中挑選特定的發佈目標":::

1. 在 [**發行**] 頁面的 [**位置**] 索引標籤上，選取 **[完成]**。

   :::image type="content" source="media/publishing-with-visual-studio/publish-page-loc-tab.png" alt-text="Visual Studio 發佈頁面位置] 索引標籤":::

1. 在 [**發行**] 視窗的 [**發行**] 索引標籤上，選取 [**發行**]。

   :::image type="content" source="media/publishing-with-visual-studio/publish-page.png" alt-text="Visual Studio [發行] 視窗":::

## <a name="inspect-the-files"></a>檢查檔案

根據預設，發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET 執行時間的電腦上執行。 使用者可以按兩下可執行檔，或從命令提示字元發出命令，以執行已發佈的應用程式 `dotnet HelloWorld.dll` 。

在下列步驟中，您將查看發佈程式所建立的檔案。

1. 在 **方案總管** 中，選取 [ **顯示所有** 檔案]。

1. 在專案資料夾中，展開 *bin/Release/net 5.0/publish*。

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="顯示已發佈檔案方案總管":::

   如圖所示，已發行的輸出包含下列檔案：

   * *HelloWorld.deps.json*

      這是應用程式的執行時間相依性檔案。 它會定義 .NET 元件和程式庫 (包括動態連結程式庫，其中包含執行應用程式所需的應用程式) 。 如需詳細資訊，請參閱 [執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。

   * *HelloWorld.dll*

      這是應用程式的 [framework 相依部署](../deploying/deploy-with-cli.md#framework-dependent-deployment) 版本。 若要執行這個動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。 執行應用程式的這個方法適用于已安裝 .NET 執行時間的任何平臺。

   * *HelloWorld.exe*

      這是應用程式的 [framework 相依可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable) 版本。 若要執行，請 `HelloWorld.exe` 在命令提示字元中輸入。 檔案是作業系統特定的。

   * *HelloWorld.pdb* (對於部署為選用)

      這是 debug 符號檔。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

   * *HelloWorld.runtimeconfig.json*

      這是應用程式的執行時間設定檔案。 它會識別您的應用程式建立用來執行的 .NET 版本。 您也可以將設定選項新增至其中。 如需詳細資訊，請參閱 [.net 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。

## <a name="run-the-published-app"></a>執行已發佈的應用程式

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ *發佈* ] 資料夾，然後選取 [ **複製完整路徑**]。

1. 開啟命令提示字元，然後流覽至 [ *發佈* ] 資料夾。 若要這樣做，請輸入， `cd` 然後貼上完整的路徑。 例如：

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. 使用可執行檔來執行應用程式：

   1. 輸入 `HelloWorld.exe` ，然後按 <kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵以結束。

1. 使用下列命令來執行應用程式 `dotnet` ：

   1. 輸入 `dotnet HelloWorld.dll` ，然後按 <kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵以結束。

## <a name="additional-resources"></a>其他資源

- [.NET 應用程式部署](../deploying/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已發佈主控台應用程式。 在下一個教學課程中，您將建立類別庫。

> [!div class="nextstepaction"]
> [使用 Visual Studio 建立 .NET 類別庫](library-with-visual-studio.md)
