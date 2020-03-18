---
title: 在視覺化工作室中使用 .NET 核心創建 Hello World 應用程式
description: 瞭解如何使用 Visual Studio 使用 C# 或視覺化基本版創建第一個 .NET 核心主控台應用程式。
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714003"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>教程：在 Visual Studio 2019 中創建您的第一個 .NET 核心主控台應用程式

本文提供了在 Visual Studio 2019 中創建和運行 Hello World .NET 核心主控台應用程式的分步介紹。 Hello World 應用程式傳統上用於向初學者介紹新的程式設計語言。 這個程式只是顯示短語"你好世界！ 。

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2019 版本 16.4 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，安裝了 **.NET Core 跨平臺開發**工作負載。 .NET 核心 3.1 SDK 在選擇此工作負載時會自動安裝。

有關詳細資訊，請參閱[安裝 .NET 核心 SDK](../install/sdk.md?pivots=os-windows)一文上的["使用視覺化工作室安裝](../install/sdk.md?pivots=os-windows#install-with-visual-studio)"部分。

## <a name="create-the-app"></a>建立應用程式

以下說明創建一個簡單的 Hello World 主控台應用程式：

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. 開啟 Visual Studio 2019。

1. 創建新的 C# .NET 核心主控台應用專案，名為"HelloWorld"。

   1. 在啟動視窗中，選擇 **"創建新專案**"。

      ![創建在視覺化工作室啟動視窗中選擇的新專案按鈕](./media/with-visual-studio/start-window.png)

   1. 在"**創建新專案**"頁上，在搜索框中輸入**主控台**。 接下來，從"語言"清單中選擇**C#，** 然後從"平臺"清單中選擇 **"所有平臺**"。 選擇**主控台應用 （.NET 核心）** 範本，然後選擇 **"下一步**"。

      ![創建一個選中篩選器的新專案視窗](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > 如果未看到 .NET Core 範本，則可能缺少安裝所需的工作負載。 在 **"未查找要查找的內容"** 消息下，選擇 **"安裝更多工具和功能**"連結。 視覺化工作室安裝程式將打開。 確保您安裝了 **.NET Core 跨平臺開發**工作負載。

   1. 在"**配置新專案**"頁上，在 **"專案名稱"** 框中輸入**HelloWorld。** 然後，選擇 **"創建**"。

      ![使用專案名稱、位置和解決方案名稱欄位配置新專案視窗](./media/with-visual-studio/configure-new-project.png)

   .NET Core 的 C# 主控台應用程式範本會自動定義一個 `Program` 類別，該類別具有採用 <xref:System.String> 陣列為引數的單一 `Main` 方法。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. 開啟 Visual Studio 2019。

1. 創建新的視覺基礎 .NET 核心主控台應用程式專案名為"HelloWorld"。

   1. 在啟動視窗中，選擇 **"創建新專案**"。

      ![創建在視覺化工作室啟動視窗中選擇的新專案按鈕](./media/with-visual-studio/start-window.png)

   1. 在"**創建新專案**"頁上，在搜索框中輸入**主控台**。 接下來，從"語言"清單中選擇 **"視覺化基礎知識**"，然後從"平臺"清單中選擇 **"所有平臺**"。 選擇**主控台應用 （.NET 核心）** 範本，然後選擇 **"下一步**"。

      ![選擇主控台應用程式 (.NET Framework) 的 Visual Basic 專案範本](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > 如果未看到 .NET Core 範本，則可能缺少安裝所需的工作負載。 在 **"未查找要查找的內容"** 消息下，選擇 **"安裝更多工具和功能**"連結。 視覺化工作室安裝程式將打開。 確保您安裝了 **.NET Core 跨平臺開發**工作負載。

   1. 在"**配置新專案**"頁上，在 **"專案名稱"** 框中輸入**HelloWorld。** 然後，選擇 **"創建**"。

   .NET Core 的主控台應用範本自動定義一個類`Program`，使用單個方法 ，`Main`將<xref:System.String>陣列作為參數。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在`args`參數中提供了啟動應用程式時提供的任何命令列參數。

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以在主控台視窗中顯示常值字串 "Hello World!" 。

## <a name="run-the-app"></a>執行應用程式

1. 要運行該程式，請選擇工具列上的**HelloWorld，** 或按**F5**。

   ![已選擇 HelloWorld 運行按鈕的視覺化工作室工具列](./media/with-visual-studio/run-program.png)

   主控台視窗打開，上面寫著"你好世界！ 列印在螢幕上和一些視覺化工作室調試資訊。

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. 按任意鍵關閉主控台視窗。

## <a name="enhance-the-app"></a>增強應用程式

增強您的應用程式以提示使用者輸入其名稱，並將其與日期和時間一起顯示。 以下說明再次修改並運行應用：

# <a name="c"></a>[C#](#tab/csharp)

1. 將`Main`方法的內容（當前只是調用`Console.WriteLine`的行）替換為以下代碼：

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按 Enter 鍵。 它會將此字串儲存至名為 `name` 的變數。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，使用[字串插值](../../csharp/language-reference/tokens/interpolated.md)在主控台視窗中顯示這些值。

1. 通過選擇**生成** > **解決方案**編譯器。

1. 要運行該程式，請選擇工具列上的**HelloWorld，** 或按**F5**。

1. 通過輸入名稱並按**Enter**鍵回應提示。

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. 按任意鍵關閉主控台視窗。

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. 將`Main`方法的內容（當前只是調用`Console.WriteLine`的行）替換為以下代碼：

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按 Enter 鍵。 它會將此字串儲存至名為 `name` 的變數。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，使用[字串插值](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)在主控台視窗中顯示這些值。

1. 通過選擇**生成** > **解決方案**編譯器。

1. 要運行該程式，請選擇工具列上的**HelloWorld，** 或按**F5**。

1. 通過輸入名稱並按**Enter**鍵回應提示。

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. 按任意鍵關閉主控台視窗。

---

## <a name="next-steps"></a>後續步驟

在本文中，您已經創建並運行了第一個 .NET Core 應用程式。 在下一步中，您將調試應用。

> [!div class="nextstepaction"]
> [在視覺工作室調試 .NET 核心 Hello World 應用程式](debugging-with-visual-studio.md)
