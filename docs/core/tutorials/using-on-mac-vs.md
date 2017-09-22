---
title: "使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core"
description: "本主題會逐步引導您使用 Visual Studio for Mac 和 .NET Core 建置簡單主控台應用程式。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8902e849-dd17-42c0-8264-cc7ae3927a0c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e11515031716a66ead866e52504137cb4e1df137
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core

Visual Studio for Mac 針對開發 .NET Core 應用程式，提供功能完整的整合式開發環境 (IDE)。 本主題會逐步引導您使用 Visual Studio for Mac 和 .NET Core 建置簡單主控台應用程式。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
> * 在 Visual Studio for Mac 中，從功能表選取 [說明] > [回報問題]，或從歡迎畫面選取 [回報問題]，這會開啟用來提出錯誤報告的視窗。 您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)入口網站追蹤您的意見反應。
> * 若要提出建議，從功能表選取 [說明] > [提供建議]，或從歡迎畫面選取 [提供建議]，這會帶您前往 [Visual Studio for Mac UserVoice 網頁](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac) \(英文\)。

## <a name="prerequisites"></a>必要條件

請參閱 [Mac 上 .NET Core 的先決條件](../../core/macos-prerequisites.md)主題。

## <a name="getting-started"></a>使用者入門

如果您已經安裝必要條件和 Visual Studio for Mac，請略過本節並移至[建立專案](#creating-a-project)。 請遵循下列步驟來安裝必要條件和 Visual Studio for Mac：

1. 下載並安裝 [.NET Core 和 OpenSSL (英文)](https://www.microsoft.com/net/core#macos)。

## <a name="creating-a-project"></a>建立專案

1. 選取歡迎畫面上的 [新增專案]。

   ![Visual Studio for Mac 歡迎畫面上的 [新增專案] 按鈕](./media/using-on-mac-vs/vsmac1.png)

1. 在 [新增專案] 對話方塊中，選取 [.NET Core] 節點下的 [應用程式]。 選取 [主控台應用程式] 範本，接著選取 [下一步]。

   ![[新增專案] 範本清單](./media/using-on-mac-vs/vsmac2.png)

1. 針對 [專案名稱] 輸入 "HelloWorld"。 選取 [建立]。

   ![設定新主控台應用程式對話方塊](./media/using-on-mac-vs/vsmac3.png)

1. 等候專案的相依性還原完畢。 專案具有單一 C# 檔案 *Program.cs*，其中包含具有 `Main` 方法的 `Program` 類別。 執行應用程式時，`Console.WriteLine` 陳述式會將 "Hello World!" 輸出到主控台。

   ![開啟 Program.cs 檔案的主視窗](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>執行應用程式

使用 <kbd>F5</kbd> 以偵錯模式執行應用程式，或使用 <kbd>CTRL</kbd>+<kbd>F5</kbd> 以發行模式執行應用程式。

![[應用程式輸出] 窗格顯示 Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>後續步驟

[使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 解決方案](using-on-mac-vs-full-solution.md)主題，能說明如何建置一個包含可重複使用之程式庫和單元測試的完整 .NET Core 解決方案。

