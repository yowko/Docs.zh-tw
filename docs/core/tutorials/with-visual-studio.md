---
title: 在 Visual Studio 中使用 .NET Core 建立主控台應用程式
description: '瞭解如何使用 Visual Studio，以 c # 或 Visual Basic 建立 .NET Core 主控台應用程式。'
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201590"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>教學課程：在 Visual Studio 2019 中建立 .NET Core 主控台應用程式

本教學課程說明如何在 Visual Studio 2019 中建立及執行 .NET Core 主控台應用程式。

## <a name="prerequisites"></a>Prerequisites

- 已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。

  如需詳細資訊，請參閱[安裝 .NET Core SDK](../install/sdk.md?pivots=os-windows)一文中的[install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio)一節。

## <a name="create-the-app"></a>建立應用程式

<!-- markdownlint-disable MD025 -->

1. 開啟 Visual Studio 2019。

1. 建立名為 "HelloWorld" 的新 .NET Core 主控台應用程式專案。

   1. 在 [開始] 頁面上，選擇 [**建立新專案**]。

      ![在 Visual Studio 起始頁上選取 [建立新專案] 按鈕](./media/with-visual-studio/start-window.png)

   1. 在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。 接著，從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [**所有平臺**]。 選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]**。

      ![建立已選取篩選的新專案視窗](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > 如果您看不到 .NET Core 範本，可能會遺失必要的工作負載。 在 [**找不到您要尋找的內容嗎？** ] 訊息底下，選擇 [**安裝更多工具和功能**] 連結。 Visual Studio 安裝程式隨即開啟。 請確定您已安裝 **.Net Core 跨平臺開發**工作負載。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**HelloWorld** 。 接著，選擇 [建立]  。

      ![以 [專案名稱]、[位置] 和 [方案名稱] 欄位設定新的專案視窗](./media/with-visual-studio/configure-new-project.png)

   適用于 .NET Core 的主控台應用程式範本會定義一個類別， `Program` 其中包含單一方法，其 `Main` 採用 <xref:System.String> 陣列做為引數。 `Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。

   如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！" 。

## <a name="run-the-app"></a>執行應用程式

1. 若要執行程式，請選擇工具列上的 [ **HelloWorld** ]，或按**F5**。

   ![已選取 [HelloWorld 執行] 按鈕的 Visual Studio 工具列](./media/with-visual-studio/run-program.png)

   主控台視窗隨即開啟，並出現 "Hello World！" 文字 列印在畫面上，而部分 Visual Studio 的調試資訊。

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. 按任意鍵關閉主控台視窗。

## <a name="enhance-the-app"></a>增強應用程式

增強應用程式，以提示使用者輸入其名稱，並連同日期和時間一起顯示。 下列指示會修改並再次執行應用程式：

1. `Main`以下列程式碼取代方法的內容，這目前只是呼叫的那一行 `Console.WriteLine` ：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入字串並按 Enter 鍵。 它會將此字串儲存在名為的變數中 `name` 。 它也會抓取屬性的值 <xref:System.DateTime.Now?displayProperty=nameWithType> ，其中包含目前的本地時間，並將它指派給名為的變數 `date` （ `currentDate` 在 Visual Basic 中）。 最後，它會在主控台視窗中顯示這些值。

   `\n`（ `vbCrLf` 在 Visual Basic 中）代表分行符號。

   字串前面的貨幣符號（ `$` ）可讓您在字串中的大括弧內放置運算式，例如變數名稱。 運算式值會插入字串中，以取代運算式。 此語法稱為「插入[字串](../../csharp/language-reference/tokens/interpolated.md)」。

1. 若要執行程式，請選擇工具列上的 [ **HelloWorld** ]，或按**F5**。

1. 輸入名稱並按**enter**鍵，以回應提示。

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. 按任意鍵關閉主控台視窗。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立 .NET Core 應用程式。 在下一個教學課程中，您會對應用程式進行 debug。

> [!div class="nextstepaction"]
> [在 Visual Studio 中，對 .NET Core 主控台應用程式進行 Debug](debugging-with-visual-studio.md)
