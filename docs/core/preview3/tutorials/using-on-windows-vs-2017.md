---
title: "使用 Visual Studio 2017 在 Windows 上開始使用 .NET Core"
description: "使用 Visual Studio 2017 在 Windows 上開始使用 .NET Core"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 71eab6216e116b99927dfeaa8ce3cf70bcc08a5e
ms.openlocfilehash: 4437f44523bcc4e8517de5b6be42a63439f817d7

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2017"></a>使用 Visual Studio 2017 在 Windows 上開始使用 .NET Core

[Bertrand Le Roy](https://github.com/bleroy) 和 [Phillip Carter](https://github.com/cartermp) 撰

Visual Studio 2017 提供功能完整的開發環境來開發 .NET Core 應用程式。 本文件中的程序說明使用 Visual Studio 和 .NET Core 來建置非常簡單的主控台應用程式所需的步驟。

## <a name="prerequisites"></a>必要條件

請依照[我們的必要條件頁面](../windows-prerequisites.md)上的指示進行，更新您的環境。

## <a name="getting-started"></a>快速入門

下列步驟將設定 Visual Studio 2017 以進行 .NET Core 主控台應用程式的開發：

1. 開啟 Visual Studio 並在 [檔案] 功能表上，選擇 [新增]、[專案]。

2. 在 [新增專案] 對話方塊的 [範本] 清單中，展開 [Visual C#] 節點，然後選擇 [.NET Core]。 您應該會看到三到四個專案範本，分別適用於**主控台應用程式 (.NET Core)**、**單元測試專案 (.NET Core)**、**類別庫 (.NET Core)**，以及 **ASP.NET Core Web 應用程式 (.NET Core)**。 選擇 [主控台應用程式 (.NET Core)]、輸入專案的名稱、挑選一個位置，然後按一下 [確定]。

  ![新的專案︰主控台應用程式](media/new-project-console-app.png)

3. 產生的專案會有單一 C# 檔案，以將 "Hello World" 輸出到主控台。

  ![主控台應用程式專案](media/console-app-solution.png)

您可以在偵錯模式中使用 F5，或在發行模式中使用 CTRL+F5，來執行此應用程式。 您也可以設定中斷點來中斷執行並檢查變數，或開始撰寫更有趣的程式碼。

祝各位寫程式愉快！

## <a name="what-to-do-next"></a>後續步驟

在此簡單的介紹之後，您可能會猜想應如何重複使用程式庫和測試來建置更進階的解決方案。 [使用 Visual Studio 2017 在 Windows 上建置完整的 .NET Core 解決方案](using-on-windows-vs-2017-full-solution.md)主題會示範如何執行此動作。



<!--HONumber=Nov16_HO3-->


