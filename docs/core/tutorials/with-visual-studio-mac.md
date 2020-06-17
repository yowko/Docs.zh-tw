---
title: 使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式。
ms.date: 06/02/2020
ms.openlocfilehash: 9cab838eaab2c59d8a0270267514f57acb7c60fb
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84811662"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a>教學課程：使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式

本教學課程說明如何使用 Visual Studio for Mac 建立及執行 .NET Core 主控台應用程式。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
>
> * 在 Visual Studio for Mac 中，從功能表**選取**  >  [說明] [回報**問題**] 或 [從歡迎畫面**回報問題**]，這會開啟用來提出錯誤報表的視窗。 您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)入口網站追蹤您的意見反應。
> * 若要提出建議，請從功能表**選取 [** 說明]  >  [**提供建議**] 或從 [歡迎使用] 畫面中**提供建議**，這會帶您前往[Visual Studio for Mac 的開發人員社區網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。

## <a name="prerequisites"></a>必要條件

* [Visual Studio for Mac 8.6 版或更新版本](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 選取 [安裝 .NET Core] 選項。 安裝 Xamarin 對於 .NET Core 開發而言是選擇性的。 如需詳細資訊，請參閱下列資源：

  * [教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。
  * [支援的 macOS 版本](../install/dependencies.md?pivots=os-macos)。
  * [Visual Studio for Mac 支援的 .Net Core 版本](/visualstudio/mac/net-core-support)。

## <a name="create-the-app"></a>建立應用程式

建立名為 "HelloWorld" 的 .NET Core 主控台應用程式專案。

1. 啟動 Visual Studio for Mac。

1. 在 [開始] 視窗中選取 [**新增**]。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Visual Studio for Mac [開始] 畫面上的 [新增] 按鈕":::

1. 在 [**新增專案**] 對話方塊中，選取 [ **Web 和主控台**] 節點底下的 [**應用程式**]。 選取 [**主控台應用程式**] 範本，然後選取 **[下一步]**。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="[新增專案] 範本清單":::

1. 在 [設定**新的主控台應用程式**] 對話方塊的 [**目標 Framework** ] 下拉式選單中，選取 [ **.net Core 3.1**]，然後選取 **[下一步]**。

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="選取目標 Framework":::

1. 輸入 "HelloWorld" 作為**專案名稱**，然後選取 [**建立**]。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="設定新主控台應用程式對話方塊":::

此範本會建立簡單的 "Hello World" 應用程式。 它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！" 在終端機視窗中。

範本程式碼會定義具有單一方法的類別，其 `Program` `Main` 接受 <xref:System.String> 陣列做為引數：

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

1. 按<kbd>⌥</kbd><kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>選項</kbd> + <kbd>命令</kbd> + <kbd>enter</kbd>）以執行應用程式而不進行偵測。

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="終端機會顯示 Hello World！":::

1. 關閉**終端**機視窗。

## <a name="enhance-the-app"></a>增強應用程式

增強應用程式，以提示使用者輸入其名稱，並連同日期和時間一起顯示。

1. 在*Program.cs*中，以 `Main` 下列程式碼取代方法的內容，也就是呼叫的那一行 `Console.WriteLine` ：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   此程式碼會在主控台中顯示「What is your name?」， 在主控台視窗中，等候使用者輸入後面接著<kbd>enter</kbd>鍵的字串。 它會將此字串儲存在名為的變數中 `name` 。 此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。 最後，它會在主控台視窗中顯示這些值。

   `\n`代表換行字元。

   字串前面的貨幣符號（ `$` ）可讓您在字串中的大括弧內放置運算式，例如變數名稱。 運算式值會插入字串中，以取代運算式。 此語法稱為「插入[字串](../../csharp/language-reference/tokens/interpolated.md)」。

1. 按<kbd>⌥</kbd><kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>選項</kbd> + <kbd>命令</kbd> + <kbd>enter</kbd>）以執行應用程式。

1. 輸入名稱並按<kbd>enter</kbd>，以回應提示。

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="終端機顯示已修改的程式輸出":::

1. 關閉終端機。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立 .NET Core 主控台應用程式。 在下一個教學課程中，您會對應用程式進行 debug。

> [!div class="nextstepaction"]
> [在 Visual Studio 中，對 .NET Core 主控台應用程式進行 Debug](debugging-with-visual-studio-mac.md)
