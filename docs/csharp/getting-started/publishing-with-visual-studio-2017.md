---
title: "使用 Visual Studio 2017 發行您的 Hello World 應用程式"
description: "使用 Visual Studio 2017 發行您的 Hello World 應用程式"
keywords: ".NET, .NET Core, .NET Core 主控台應用程式, 發行 (.NET Core), 部署 (.NET Core)"
author: stevehoag
ms.author: shoag
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f4a30d19e111d395088e38c4543c9dacee6105fd
ms.lasthandoff: 03/13/2017

---

# <a name="publishing-your-hello-world-application-with-visual-studio-2017"></a>使用 Visual Studio 2017 發行您的 Hello World 應用程式

[在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式](with-visual-studio-2017.md)中，您已建立 Hello World 主控台應用程式，然後在[使用 Visual Studio 2017 針對您的 C# Hello World 應用程式進行偵錯](debugging-with-visual-studio-2017.md)中，使用 Visual Studio 偵錯工具來加以測試。 現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。 發行會建立一組執行您的應用程式所需的檔案，您可以將它們複製到目標電腦來加以部署。

編譯和執行您的應用程式： 

1. 請確定 Visual Studio 正在建置您應用程式的發行版本。 如有必要，請將工具列上的組態設定從[偵錯]**** 變更為 [發行]****，如下圖所示。

   ![Image](media/release.jpg)

1. 開啟主控台視窗。 例如，在 Windows 工具列的 [請隨意提出問題]**** 文字方塊中輸入 `Command Prompt`，然後選擇 [命令提示字元]**** 傳統型應用程式來開啟主控台視窗。

1. 在 HelloWorld 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]****。 您也可以從主要的 Visual Studio [建置]**** 功能表，選取 [發行 HelloWorld]****。

1. 如下圖所示，當 [發行]**** 對話方塊出現時，請選取 [建立新設定檔]**** 來建立新的發行設定檔。

1. 在下圖所示的 [挑選發行目標]**** 對話方塊中，選取 [確定]**** 按鈕以將您的應用程式發行到本機檔案系統。 您可以在應用程式專案目錄的 bin\release\PublishOutput 子目錄中找到它。

1. 現在，您已建立發行設定檔，請在 [發行]**** 對話方塊中選取 [發行]**** 按鈕，如下圖所示。

   ![Image](media/publish-2.jpg)

1. 如下圖所示，發行的輸出包含下列三個檔案，其會形成您的應用程式，而您可以將它們複製到目標系統來加以部署︰

      - HelloWorld.dll
   
      - HelloWorld.deps.json

      - HelloWorld.runtimeconfig.json

   第四個檔案 HelloWorld.pdb 包含偵錯符號。 該檔案不必隨您的應用程式發佈，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

   ![Image](media/pub-files.jpg)

發佈程序會建立與 Framework 相依的部署。只要 .NET Core 安裝在系統上，發行的應用程式即可以在 .NET Core 支援的任何平台上執行。 使用者可以從主控台視窗發出 `dotnet.exe HelloWorld.dll` 命令來執行您的應用程式。

如需有關發行和部署 .NET Core 應用程式的詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。
