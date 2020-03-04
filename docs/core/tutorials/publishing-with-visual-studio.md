---
title: 使用 Visual Studio 發佈您的 .NET Core Hello World 應用程式
description: 發行會建立一組執行您的 .NET Core 應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156630"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>使用 Visual Studio 發佈您的 .NET Core Hello World 應用程式

在[Visual Studio 中使用 .Net Core 建立 Hello World 應用程式](with-visual-studio.md)時，您已建立 Hello World 主控台應用程式。 在[使用 Visual Studio 來進行 Hello World 應用程式](debugging-with-visual-studio.md)的「偵測」時，您會使用 Visual Studio 偵錯工具進行測試。 現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。 發行會建立一組執行您的應用程式所需的檔案。 若要部署檔案，請將檔案複製到目的電腦。

## <a name="publish-the-app"></a>發佈應用程式

1. 請確定 Visual Studio 正在組置您應用程式的發行版本。 如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]** 。

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. 在 **HelloWorld** 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]。 （您也可以從主要的 [**組建**] 功能表中選取 [**發佈 HelloWorld** ]）。

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)

1. 在 [**挑選發行目標**] 頁面上，選取 [**資料夾**]，然後選取 [**建立設定檔**]。

   ![在 Visual Studio 中挑選發行目標](media/publishing-with-visual-studio/pick-publish-target.png)

1. 在 [**發行**] 頁面上，選取 [**發佈**]。

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>檢查檔案

發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在 .NET Core 所支援的任何平臺上執行，並在系統上安裝 .NET Core。 使用者可以按兩下可執行檔，或從命令提示字元發出 `dotnet HelloWorld.dll` 命令，以執行已發佈的應用程式。

在下列步驟中，您將查看發行程式所建立的檔案。

1. 開啟命令提示字元。

   開啟命令提示字元的方法之一，就是在 Windows 工作列的 [搜尋] 方塊中輸入**命令提示**字元（簡稱**cmd** ）。 選取 [**命令提示**字元] 桌面應用程式，如果已在搜尋結果中選取，請按**enter** 。

1. 在應用程式專案目錄的*bin\Release\netcoreapp3.1\publish*子目錄中，流覽至已發佈的應用程式。

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/published-files-output.png)

   如圖所示，已發行的輸出會包含下列檔案：

      * *HelloWorld.deps.json*

         這是應用程式的執行時間相依性檔案。 它會定義執行應用程式所需的 .NET Core 元件和程式庫（包括包含您應用程式的動態連結程式庫）。 如需詳細資訊，請參閱[執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。

      * *HelloWorld.dll*

         這是與[framework 相依](../deploying/deploy-with-cli.md#framework-dependent-deployment)的應用程式部署版本。 若要執行此動態連結程式庫，請在命令提示字元中輸入 `dotnet HelloWorld.dll`。

      * *HelloWorld .exe*

         這是與[framework 相依的應用程式可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。 若要執行，請在命令提示字元中輸入 `HelloWorld.exe`。

      * *HelloWorld.pdb* (對於部署為選用)

         這是 debug 符號檔案。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

      * *HelloWorld.runtimeconfig.json*

         這是應用程式的執行時間設定檔。 它會識別建置您應用程式以在其上執行的 .NET Core 版本。 您也可以在其中新增設定選項。 如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。

## <a name="additional-resources"></a>其他資源

- [.NET Core 應用程式部署](../deploying/index.md)
