---
title: 使用 Visual Studio 2017 發行您的 Hello World 應用程式
description: 發行會建立一組執行您的應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: f3cecbd39ee557a620cd779bdff6b630642e7f56
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a>使用 Visual Studio 2017 發行您的 Hello World 應用程式

於[在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式](with-visual-studio.md)或[在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic Hello World 應用程式](vb-with-visual-studio.md)中，您建立了 Hello World 主控台應用程式。 在[使用 Visual Studio 2017 針對 C# Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)中，您已使用 Visual Studio 偵錯工具加以測試。 現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。 發行會建立一組執行您的應用程式所需的檔案，您可以將這些檔案複製到目標電腦來加以部署。

編譯和執行您的應用程式： 

1. 請確定 Visual Studio 正在組置您應用程式的發行版本。 如有必要，請將工具列上的組建組態設定從 [偵錯] 變更為 [發行]。

   ![Visual Studio 工具列](media/publishing-with-visual-studio/toolbar.png)

1. 在 **HelloWorld** 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]。 您也可以從主要的 Visual Studio **[建置]** 功能表，選取 **[發行 HelloWorld]**。

   ![Visual Studio 工具列](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio 工具列](media/publishing-with-visual-studio/publishwindow.png)

1. 開啟主控台視窗。 例如，在 Windows 工作列的 [Type here to search] (在這裡鍵入要搜尋的文字) 文字方塊中，輸入 `Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。

1. 巡覽至已發行的應用程式，其位於應用程式專案目錄的 `bin\release\PublishOutput` 子目錄中。 如下圖所示，已發行的輸出包含下列四個檔案：

      * *HelloWorld.deps.json*

         應用程式的執行階段相依性檔案。 它會定義執行您應用程式所需的 .NET Core 元件和程式庫 (包含內含您應用程式的動態連結程式庫)。 如需詳細資訊，請參閱[執行階段組態檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。
 
      * *HelloWorld.dll*

         包含您應用程式的檔案。 它是動態連結程式庫，可在主控台視窗中輸入 `dotnet HelloWorld.dll` 命令予以執行。 

      * *HelloWorld.pdb* (對於部署為選用)

         包含偵錯符號的檔案。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

      * *HelloWorld.runtimeconfig.json*

         應用程式的執行階段組態檔。 它會識別建置您應用程式以在其上執行的 .NET Core 版本。 如需詳細資訊，請參閱[執行階段組態檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。  

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/publishedfiles.png)

發行程序會建立與 Framework 相依的部署，在這種部署類型中，只要 .NET Core 安裝在系統上，發行的應用程式即可以在 .NET Core 支援的任何平台上執行。 使用者可以從主控台視窗發出 `dotnet HelloWorld.dll` 命令來執行您的應用程式。

如需有關發行和部署 .NET Core 應用程式的詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。
