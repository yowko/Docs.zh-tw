---
title: 使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio for Mac 來建立 .NET Core 主控台應用程式。
ms.date: 06/02/2020
ms.openlocfilehash: ca933bc9322109ba7d1f808fcc44696a9766a6d4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537596"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a>教學課程：使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式

本教學課程說明如何使用 Visual Studio for Mac 來建立和執行 .NET Core 主控台應用程式。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
>
> * 在 Visual Studio for Mac 中， **Help**  >  **Report a Problem**從功能表中選取 [說明]，或從歡迎畫面回報**問題**，這會開啟用來提出錯誤報表的視窗。 您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)入口網站追蹤您的意見反應。
> * 若要提出建議，請**Help**  >  從功能表中選取 [說明]**提供建議**，或從歡迎畫面**提供**建議，這會帶您前往[Visual Studio for Mac 開發人員社群網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。

## <a name="prerequisites"></a>Prerequisites

* [Visual Studio for Mac 8.6 版或更新版本](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 選取安裝 .NET Core 的選項。 安裝 Xamarin 是 .NET Core 開發的選擇性選項。 如需詳細資訊，請參閱下列資源：

  * [教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。
  * [支援的 macOS 版本](../install/windows.md)。
  * [Visual Studio for Mac 支援的 .Net Core 版本](/visualstudio/mac/net-core-support)。

## <a name="create-the-app"></a>建立應用程式

建立名為 "HelloWorld" 的 .NET Core 主控台應用程式專案。

1. 開始 Visual Studio for Mac。

1. 在 [開始] 視窗中選取 [ **新增** ]。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Visual Studio for Mac [開始] 畫面上的 [新增] 按鈕":::

1. 在 [**新增專案**] 對話方塊的 [Web]**和 [主控台**] 節點底下，選取 [**應用程式**]。 選取 [ **主控台應用程式** ] 範本，然後選取 **[下一步]**。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="[新增專案] 範本清單":::

1. 在 [**設定您的新主控台應用程式**] 對話方塊的 [**目標 Framework** ] 下拉式清單中，選取 [ **.net Core 3.1**]，然後選取 **[下一步]**。

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="選取目標 Framework":::

1. 輸入 "HelloWorld" 作為 **專案名稱**，然後選取 [ **建立**]。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="設定新主控台應用程式對話方塊":::

此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！" 在終端機視窗中。

範本 `Program` 程式碼會使用單一方法定義類別， `Main` 這個方法會採用 <xref:System.String> 陣列作為引數：

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

`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。 當應用程式啟動時所提供的任何命令列引數都可在陣列中使用 `args` 。

## <a name="run-the-app"></a>執行應用程式

1. 按<kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>命令</kbd> + <kbd>輸入</kbd>) 來執行應用程式，而不進行任何偵錯工具。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="終端機會顯示 Hello World！":::

1. 關閉 **終端** 機視窗。

## <a name="enhance-the-app"></a>增強應用程式

增強應用程式以提示使用者輸入其名稱，並將它與日期和時間一起顯示。

1. 在 *Program.cs*中， `Main` 使用下列程式碼取代方法的內容，也就是呼叫的行 `Console.WriteLine` ：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   這段程式碼會在主控台視窗中顯示提示，並等候使用者輸入字串，然後按 <kbd>enter</kbd> 鍵。 它會將此字串儲存在名為的變數中 `name` 。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 它會在主控台視窗中顯示這些值。 最後，它會在主控台視窗中顯示提示，並呼叫 <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> 方法來等候使用者輸入。

   `\n`代表換行字元。

   字串前面的貨幣符號 (`$`) 可讓您在字串中將運算式（例如變數名稱）放在大括弧中。 運算式值會插入字串以取代運算式。 這個語法稱為 [插補字串](../../csharp/language-reference/tokens/interpolated.md)。

1. 按<kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>命令</kbd> + <kbd>輸入</kbd>) 來執行應用程式。

1. 輸入名稱並按 <kbd>enter</kbd>，以回應提示。

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="終端機顯示修改過的程式輸出":::

1. 關閉終端機。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立 .NET Core 主控台應用程式。 在下一個教學課程中，您將會對應用程式進行偵錯工具。

> [!div class="nextstepaction"]
> [使用 Visual Studio for Mac 來對 .NET Core 主控台應用程式進行偵錯工具](debugging-with-visual-studio-mac.md)
