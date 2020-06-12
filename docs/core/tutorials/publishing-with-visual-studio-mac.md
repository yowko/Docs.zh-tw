---
title: 使用 Visual Studio for Mac 發行 .NET Core 主控台應用程式
description: 發行會建立一組執行 .NET Core 應用程式所需的檔案。
ms.date: 06/08/2020
ms.openlocfilehash: 67762481d3a56b8473e643f71b8df909b6e54fc6
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713662"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a>教學課程：使用 Visual Studio for Mac 發行 .NET Core 主控台應用程式

本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。 發行會建立一組執行您的應用程式所需的檔案。 若要部署檔案，請將檔案複製到目的電腦。

## <a name="prerequisites"></a>Prerequisites

- 本教學課程適用于您在 Visual Studio for Mac 中建立[.Net Core 主控台應用程式](with-visual-studio-mac.md)中建立的主控台應用程式。

## <a name="publish-the-app"></a>發佈應用程式

1. 啟動 Visual Studio for Mac。

1. 開啟您在[Visual Studio for Mac 中建立 .Net Core 主控台應用程式](with-visual-studio-mac.md)中建立的 HelloWorld 專案。

1. 請確定 Visual Studio 正在組置您應用程式的發行版本。 如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="選取 [發行] 組建的 Visual Studio 工具列":::

1. 從主功能表中，選擇 [**組建**] [  >  **發行至資料夾**]。

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio [發行] 操作功能表":::

1. 在 [**發行至資料夾**] 對話方塊中，選取 [**發行**]。

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio 發行至資料夾] 對話方塊":::

   [發行] 資料夾隨即開啟，其中顯示已建立的檔案。

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="發行資料夾":::

1. 選取齒輪圖示，然後從內容功能表中選取 **[將 "publish" 複製為路徑名稱]** 。

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="將路徑複製到發行資料夾":::

## <a name="inspect-the-files"></a>檢查檔案

發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET Core 執行時間的電腦上執行。 使用者可以從命令提示字元執行命令，以執行已發佈的應用程式 `dotnet HelloWorld.dll` 。

如上圖所示，已發行的輸出會包含下列檔案：

* *HelloWorld.deps.json*

  這是應用程式的執行時間相依性檔案。 它會定義執行應用程式所需的 .NET Core 元件和程式庫（包括包含您應用程式的動態連結程式庫）。 如需詳細資訊，請參閱[執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。

* *HelloWorld.dll*

   這是與[framework 相依](../deploying/deploy-with-cli.md#framework-dependent-deployment)的應用程式部署版本。 若要執行此動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。 這種執行應用程式的方法可在已安裝 .NET Core 執行時間的任何平臺上運作。

* *HelloWorld.pdb* (對於部署為選用)

   這是 debug 符號檔案。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

* *HelloWorld.runtimeconfig.json*

   這是應用程式的執行時間設定檔。 它會識別建置您應用程式以在其上執行的 .NET Core 版本。 您也可以在其中新增設定選項。 如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。

## <a name="run-the-published-app"></a>執行已發佈的應用程式

1. 開啟終端機，並流覽至 [*發佈*] 資料夾。 若要這麼做，請輸入 `cd` ，然後貼上您稍早複製的路徑。 例如：

   ```
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. 使用命令執行應用程式 `dotnet` ：

   1. 輸入 `dotnet HelloWorld.dll` ，然後按<kbd>enter</kbd>鍵。

   1. 輸入名稱以回應提示，然後按任意鍵結束。

## <a name="additional-resources"></a>其他資源

- [.NET Core 應用程式部署](../deploying/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已發佈主控台應用程式。 在下一個教學課程中，您會建立類別庫。

> [!div class="nextstepaction"]
> [在適用于 mac 的 Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio-mac.md)
