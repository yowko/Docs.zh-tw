---
title: "使用 Visual Studio 2017 發佈 Hello World 應用程式 | Microsoft Docs"
description: "發行會建立一組執行您的應用程式所需的檔案。"
keywords: ".NET, .NET Core, 主控台應用程式, 發行, 部署"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 49fdae2ada3473463dcb120a35cfc8649a38a14d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# 使用 Visual Studio 2017 發行您的 Hello World 應用程式
<a id="publishing-your-hello-world-application-with-visual-studio-2017" class="xliff"></a>

[在 Visual Studio 2017 中使用 .NET Core 建 置 C# Hello World 應用程式](with-visual-studio.md)中，您已組置 Hello World 主控台應用程式。 在[使用 Visual Studio 2017 針對 C# Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)中，您已使用 Visual Studio 偵錯工具加以測試。 現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。 發行會建立一組執行您的應用程式所需的檔案，您可以將這些檔案複製到目標電腦來加以部署。

編譯和執行您的應用程式： 

1. 請確定 Visual Studio 正在組置您應用程式的發行版本。 如有必要，請將工具列上的組建組態設定從 [偵錯] 變更為 [發行]。

   ![Visual Studio 工具列](media/publishing-with-visual-studio/toolbar.png)

1. 在 **HelloWorld** 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]。 您也可以從主要的 Visual Studio **[建置]** 功能表，選取 **[發行 HelloWorld]**。

   ![Visual Studio 工具列](media/publishing-with-visual-studio/publish1.png)

1. 在 **HelloWorld** 發行視窗中，[選擇資料夾] 文字方塊內會提供預設的發行輸出資料夾。 選取 [發行] 按鈕。

   ![Visual Studio 工具列](media/publishing-with-visual-studio/publishwindow.png)

1. 開啟主控台視窗。 例如，在 Windows 工作列的 [請隨意提出問題] 文字方塊中，輸入`Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。

1. 巡覽至已發行的應用程式，其位於應用程式專案目錄的 `bin\release\PublishOutput` 子目錄中。 如下圖所示，已發行的輸出包含下列四個檔案：

      * *HelloWorld.deps.json*
      * *HelloWorld.dll*
      * *HelloWorld.pdb* (對於部署為選用)
      * *HelloWorld.runtimeconfig.json*

   *HelloWorld.pdb* 檔案包含偵錯符號。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/publishedfiles.png)

發行程序會建立與 Framework 相依的部署，在這種部署類型中，只要 .NET Core 安裝在系統上，發行的應用程式即可以在 .NET Core 支援的任何平台上執行。 使用者可以從主控台視窗發出 `dotnet HelloWorld.dll` 命令來執行您的應用程式。

如需有關發行和部署 .NET Core 應用程式的詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。

