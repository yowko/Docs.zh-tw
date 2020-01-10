---
title: 在 Visual Studio 中使用 .NET Core 建立 Hello World 應用程式
description: 瞭解如何使用 Visual Studio，以建立您的第一個C# .net Core 主控台應用程式，或 Visual Basic。
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714003"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>教學課程：在 Visual Studio 2019 中建立您的第一個 .NET Core 主控台應用程式

本文提供在 Visual Studio 2019 中建立和執行 Hello World .NET Core 主控台應用程式的逐步介紹。 Hello World 的應用程式傳統上是用來向初學者介紹新的程式設計語言。 此程式只會顯示 "Hello World！" 這個片語 。

## <a name="prerequisites"></a>必要條件：

- 已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.4 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。

如需詳細資訊，請參閱[安裝 .NET Core SDK](../install/sdk.md?pivots=os-windows)一文中的[install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio)一節。

## <a name="create-the-app"></a>建立應用程式

下列指示會建立簡單的 Hello World 主控台應用程式：

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 開啟 Visual Studio 2019。

1. 建立名為C# "HelloWorld" 的新 .net Core 主控台應用程式專案。

   1. 在開始視窗中，選擇 [建立新專案]。

      ![在 [Visual Studio 開始] 視窗上選取 [建立新專案] 按鈕](./media/with-visual-studio/start-window.png)

   1. 在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。 接下來， **C#** 從 [語言] 清單中選擇，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]** 。

      ![建立已選取篩選的新專案視窗](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > 如果您看不到 .NET Core 範本，可能是您已安裝必要的工作負載。 在 [**找不到您要尋找的內容嗎？** ] 訊息底下，選擇 [**安裝更多工具和功能**] 連結。 Visual Studio 安裝程式隨即開啟。 請確定您已安裝 **.Net Core 跨平臺開發**工作負載。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**HelloWorld** 。 接著，選擇 [建立]。

      ![以 [專案名稱]、[位置] 和 [方案名稱] 欄位設定新的專案視窗](./media/with-visual-studio/configure-new-project.png)

   .NET Core 的 C# 主控台應用程式範本會自動定義一個 `Program` 類別，該類別具有採用 <xref:System.String> 陣列為引數的單一 `Main` 方法。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 開啟 Visual Studio 2019。

1. 建立名為 "HelloWorld" 的新 Visual Basic .NET Core 主控台應用程式專案。

   1. 在開始視窗中，選擇 [建立新專案]。

      ![在 [Visual Studio 開始] 視窗上選取 [建立新專案] 按鈕](./media/with-visual-studio/start-window.png)

   1. 在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。 接下來，從 [語言] 清單中選擇 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]** 。

      ![選擇主控台應用程式 (.NET Framework) 的 Visual Basic 專案範本](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > 如果您看不到 .NET Core 範本，可能是您已安裝必要的工作負載。 在 [**找不到您要尋找的內容嗎？** ] 訊息底下，選擇 [**安裝更多工具和功能**] 連結。 Visual Studio 安裝程式隨即開啟。 請確定您已安裝 **.Net Core 跨平臺開發**工作負載。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**HelloWorld** 。 接著，選擇 [建立]。

   適用于 .NET Core 的主控台應用程式範本會自動定義具有單一方法的類別 `Program`，`Main`，接受 <xref:System.String> 陣列做為引數。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 啟動應用程式時所提供的任何命令列引數都可在 `args` 參數中取得。

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以在主控台視窗中顯示常值字串 "Hello World!" 。

## <a name="run-the-app"></a>執行應用程式

1. 若要執行程式，請選擇工具列上的 [ **HelloWorld** ]，或按**F5**。

   ![已選取 [HelloWorld 執行] 按鈕的 Visual Studio 工具列](./media/with-visual-studio/run-program.png)

   主控台視窗隨即開啟，並出現 "Hello World！" 文字 列印在畫面上，而部分 Visual Studio 的調試資訊。

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. 按任意鍵以關閉主控台視窗。

## <a name="enhance-the-app"></a>增強應用程式

增強您的應用程式以提示使用者輸入其名稱，並將其與日期和時間一起顯示。 下列指示會再次修改並執行應用程式：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 以下列程式碼取代 `Main` 方法的內容，這目前只是呼叫 `Console.WriteLine`的那一行：

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按 Enter 鍵。 它會將此字串儲存至名為 `name` 的變數。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，使用[字串插值](../../csharp/language-reference/tokens/interpolated.md)在主控台視窗中顯示這些值。

1. 選擇 [建置] >  [建置方案] 來編譯程式。

1. 若要執行程式，請選擇工具列上的 [ **HelloWorld** ]，或按**F5**。

1. 輸入名稱並按**enter**鍵，以回應提示。

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. 按任意鍵以關閉主控台視窗。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 以下列程式碼取代 `Main` 方法的內容，這目前只是呼叫 `Console.WriteLine`的那一行：

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按 Enter 鍵。 它會將此字串儲存至名為 `name` 的變數。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，使用[字串插值](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)在主控台視窗中顯示這些值。

1. 選擇 [建置] >  [建置方案] 來編譯程式。

1. 若要執行程式，請選擇工具列上的 [ **HelloWorld** ]，或按**F5**。

1. 輸入名稱並按**enter**鍵，以回應提示。

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. 按任意鍵以關閉主控台視窗。

---

## <a name="next-steps"></a>後續步驟

在本文中，您已建立並執行您的第一個 .NET Core 應用程式。 在下一個步驟中，您會對應用程式進行 debug。

> [!div class="nextstepaction"]
> [在 Visual Studio 中，對 .NET Core Hello World 應用程式進行 Debug](debugging-with-visual-studio.md)
