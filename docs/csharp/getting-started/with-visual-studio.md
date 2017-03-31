---
title: "在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式"
description: "了解如何使用 Visual Studio 2017 建置簡單的 .NET Core 主控台應用程式。"
keywords: ".NET Core, .NET Core 主控台應用程式, Visual Studio 2017"
author: stevehoag
ms.author: shoag
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f1a20f399b4ab34986d700622ff3bf3859b001bd
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式 #

本主題提供使用 Visual Studio 2017 針對簡單 .NET Core 主控台應用程式進行建置、偵錯及發行的逐步指示。 Visual Studio 2017 提供功能完整的開發環境來建置 .NET Core 應用程式。 只要應用程式沒有任何平台特定的相依性，應用程式本身就可以在 .NET Core 的任何目標平台，以及安裝 .NET Core 的任何系統上執行。

## <a name="prerequisites"></a>必要條件 ##

- 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 (英文)](https://www.visualstudio.com/downloads/)。 

如需詳細資訊，請參閱＜Windows 必要條件＞主題上的 [Visual Studio 2017](../../core/windows-prerequisites.md) 一節。

## <a name="a-simple-hello-world-application"></a>簡單的 "Hello World" 應用程式 ##

讓我們開始建立簡單的 "Hello World" 主控台應用程式。 其步驟如下：

1. 啟動 Visual Studio 並在 [檔案]**** 功能表上選擇 [新增]****  >  [專案]****。 在 [新增專案]**** 對話方塊中，展開左側窗格中的 [Visual C#]**** 節點，然後選擇 [.NET Core]**** 節點。

2. 在右側窗格中，選擇 [主控台應用程式 (.NET Core)]****。 輸入專案名稱 `HelloWorld`，並確定已選取 [為方案建立目錄]**** 方塊，如下圖所示。

   ![顯示已選取 [主控台應用程式] 之 [新增專案] 對話方塊的螢幕擷取畫面](./media/with-visual-studio/vs_newproject.jpg)
   
3. 選擇 [確定] **** 按鈕。 Visual Studio 顯示具有程式碼視窗的開發環境，如下圖所示。 .NET Core 的 C# 主控台應用程式範本會自動定義一個 `Program` 類別，該類別具有採用 @System.String 陣列為引數的單一 `Main` 方法。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/vs_devenv.jpg)

   範本會建立一個非常簡單的 "Hello world" 應用程式，它會呼叫 @System.Console.WriteLine(System.String) 方法，在主控台視窗 顯示常值字串 "Hello World!"。 透過以工具列上的綠色箭頭選取 "HelloWorld" 按鈕，您將能以 [偵錯] 模式執行程式。 不過，如果您這樣做，主控台視窗將會在簡短顯示之後關閉。 這是因為在 `Main` 方法中的單一陳述式執行完畢之後，`Main` 會立即終止，而應用程式會立即結束。

4. 讓我們在主控台視窗關閉之前，先使現有的應用程式暫停。 在針對 @System.Console.WriteLine(System.String) 方法的呼叫後方加入下列程式碼：

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   此程式碼會提示使用者按下任意鍵，並暫停程式直到按下按鍵為止。

5. 在功能表列上，選擇 [建置] ****、[建置方案] ****。 這會將您的程式編譯至 IL，這是一種會接著由 Just-In-Time (JIT) 編譯器轉換為二進位程式碼的中繼語言。

6. 透過使用工具列上的綠色箭頭選取 "HelloWorld" 按鈕來執行程式。 其結果如下圖所示。

   ![Image](./media/with-visual-studio/simple_hello.jpg)

7. 按任意鍵以關閉視窗。

## <a name="enhancing-the-hello-world-application"></a>增強 "Hello World" 應用程式 ##

讓我們來增強應用程式以提示使用者輸入名字，然後將名字和日期與時間一起顯示在主控台視窗中。 若要修改並測試程式，請執行下列動作︰

1. 在程式碼視窗中，於 `public static void Main(string[] args)` 行之後的左括弧後方，以及第一個右括弧之前輸入下列 C# 程式碼。

   [!CODE [GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   下圖顯示產生的程式碼視窗。

   ![執行中的已修改程式](./media/with-visual-studio/codewindow.jpg)

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按下 Enter 鍵。 它會將此字串儲存至名稱為 `name` 的變數。 此程式碼也會擷取 @System.DateTime.Now 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 然後，程式碼會使用[複合格式字串](../../standard/base-types/composite-format.md)在主控台顯示這些值。

2. 選擇 [建置]****  >  [建置方案]**** 來編譯程式。 這會將您的程式編譯至 IL，這是一種會接著由 Just-In-Time (JIT) 編譯器轉換為二進位程式碼的中繼語言。

3. 在 Visual Studio 中以偵錯模式執行程式，方法為選取工具列上的綠色箭頭，按 F5，或是選擇 [偵錯]****  >  [開始偵錯]**** 功能表項目。 在您輸入名稱並按 Enter 鍵來回應提示之後，主控台視窗看起來應該如下︰

   ![執行中的已修改程式](./media/with-visual-studio/console.jpg)

4. 按任意鍵以關閉主控台視窗。 這樣會結束偵錯模式。

您現在已成功建立並執行這個簡單的應用程式。 若要開發專業的應用程式，您還可以執行一些其他步驟，來針對發行準備應用程式：

- 如需為應用程式進行偵錯的詳細資訊，請參閱[針對 Hello World 應用程式進行偵錯](debugging-with-visual-studio-2017.md)

- 如需發行應用程式可散發版本的詳細資訊，請參閱[發行 Hello World 應用程式](publishing-with-visual-studio-2017.md)。

## <a name="related-topics"></a>相關主題 ##

除了主控台應用程式之外，您也可以使用 .NET Core 和 Visual Studio 2017 建置類別庫。 如需逐步介紹，請參閱[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫](library-with-visual-studio-2017.md)。

您也可以使用 Visual Studio Code (可免費下載的程式碼編輯器)，在 Mac、Linux 和 Windows 上開發 .NET Core 主控台應用程式。 如需逐步教學課程，請參閱[開始使用 Visual Studio Code](with-visual-studio-code.md)。

