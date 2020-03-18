---
title: 使用 Mac 視覺化工作室構建完整的 .NET 核心解決方案
description: 本文將引導您構建一個 .NET Core 解決方案，其中包括可重用的庫和單元測試。
ms.date: 12/19/2019
ms.openlocfilehash: 8c9fcca404a3875b6bb7f9cf20551a017ff553c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239959"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>使用 Mac 視覺化工作室在 macOS 上構建完整的 .NET 核心解決方案

Visual Studio for Mac 針對開發 .NET Core 應用程式，提供功能完整的整合式開發環境 (IDE)。 本文將引導您構建一個 .NET Core 解決方案，其中包括可重用的庫和單元測試。

本教學課程會示範如何建立能接受來自使用者的搜尋文字和文字字串、使用類別庫中的方法計算搜尋文字出現在字串中的次數，並將結果傳回給使用者的應用程式。 解決方案也包含類別庫的單元測試，作為單元測試概念的簡介。 如果您偏好使用完整範例來進行教學課程，請下載[範例解決方案 (英文)](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
>
> - 在 Mac 的 Visual Studio 中，從功能表中選擇 **"説明** > **報告問題**"或"從歡迎"螢幕**中報告問題**，該螢幕將打開一個視窗以提交 Bug 報告。 您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。
> - 要提出建議，請從功能表中選擇 **"説明** > **提供建議**"或"從歡迎畫面**提供建議**"，該螢幕將帶您前往[Mac 開發人員社區網頁的視覺化工作室](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。

## <a name="prerequisites"></a>必要條件

- [.NET 核心 SDK 3.1 或更高版本](https://dotnet.microsoft.com/download)
- [Visual Studio 2019 for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

有關先決條件的詳細資訊，請參閱[.NET Core 依賴項和要求](../install/dependencies.md?pivots=os-macos)。 有關 Mac Visual Studio 2019 的完整系統要求，請參閱[Visual Studio 2019，瞭解 Mac 產品系列系統要求](/visualstudio/productinfo/vs2019-system-requirements-mac)。

## <a name="building-a-library"></a>建置程式庫

1. 在啟動視窗中，選擇 **"新專案**"。 在 [新增專案]**** 對話方塊中的 [.NET Core]**** 節點下，選取 [.NET Standard 程式庫]**** 範本。 此命令創建一個 .NET 標準庫，該庫針對 .NET Core 以及支援[.NET 標準](../../standard/net-standard.md)版本 2.1 的任何其他 .NET 實現。 如果安裝了多個版本的 .NET Core SDK，則可以為庫選擇不同版本的 .NET 標準。 選擇".NET 標準 2.1"並選擇 **"下一步**"。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. 將專案命名為 "TextUtils" (「文字公用程式」的簡短名稱)，並將解決方案命名為 "WordCounter"。 保持選取 [在解決方案目錄中建立專案目錄]****。 選取 [建立]****。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac [新增專案] 對話方塊選項](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. 在 **"解決方案**"墊中，`TextUtils`展開節點以顯示範本提供的類檔 *，Class1.cs*。 Ctrl 按一下該檔，從內容功能表中選擇 **"重命名**"，並將檔重命名為*WordCount.cs*。 開啟檔案，並以下列程式碼取代內容：

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/TextUtils/WordCount.cs)]

1. 使用三種不同方法中的任何一種保存檔：使用鍵盤快捷<kbd>鍵&#8984;，</kbd>+<kbd>s</kbd>從功能表中選擇 **"檔** > **保存**"，或按一下檔的選項卡，然後選擇"從內容功能表**中保存**"。 下圖顯示 IDE 視窗︰

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac IDE 視窗，其中包含程式庫檔案和方法](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. 選取 IDE 視窗下邊界中的 [錯誤]****，以開啟 [錯誤]**** 面板。 選取 [建置輸出]**** 按鈕。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac IDE 的下邊界，顯示 [錯誤] 按鈕](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. 從功能表中選擇 > **"生成全部**"。 **Build**

   解決方案隨即建置。 建置輸出面板會顯示建置成功。

   > [!div class="mx-imgBorder"]
   > ![[錯誤] 面板的 Visual Studio Mac [建置輸出] 窗格，其中包含「建置成功」訊息](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>建立測試專案

單元測試能在開發與發佈期間提供自動化的軟體測試。 本教程中使用的測試框架是[xUnit（版本 2.4.0 或更高版本），](https://xunit.github.io/)在以下步驟中將 xUnit 測試專案添加到解決方案時會自動安裝該框架：

1. 在 **"解決方案**"邊欄中，ctrl`WordCounter`按一下解決方案並選擇"**添加新** > **專案**"。

1. 在 [新增專案]**** 對話方塊中，從 [.NET Core]**** 節點選取 [測試]****。 選取 [xUnit 測試專案]****，接著選取 [下一步]****。

   > [!div class="mx-imgBorder"]
   > ![建立 xUnit 測試專案的 Visual Studio Mac [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. 如果您有多個版本的 .NET Core SDK，則需要選擇此專案的版本。 選擇 **.NET 核心 3.1**。 將新專案命名為 "TestLibrary"，並選取 [建立]****。

   > [!div class="mx-imgBorder"]
   > ![提供專案名稱的 Visual Studio Mac [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. 為了讓測試程式庫能搭配 `WordCount` 類別使用，請將參考加入 `TextUtils` 專案。 在 **"解決方案**"邊欄中，ctrl 按一下**測試庫**下的**依賴項**。 從操作功能表選取 [編輯參考]****。

1. 在 **"編輯參考"** 對話方塊中，選擇"專案"選項卡上的 **"文本Utils"****專案**。選擇 **"確定**"。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac [編輯參考] 對話方塊](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. 在 [TestLibrary]**** 專案中，將 *UnitTest1.cs* 檔案重新命名為 *TextUtilsTests.cs*。

1. 打開檔，並將代碼替換為以下代碼：

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   下圖顯示具有單元測試程式碼的 IDE。 請留意 `Assert.NotEqual` 陳述式。

   > [!div class="mx-imgBorder"]
   > ![IDE 主視窗中的 Visual Studio for Mac 初始單元測試](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   請務必讓新的測試失敗一次，以確認其測試邏輯正確。 該方法會傳入 "Jack" (大寫) 這個名字，以及具有 "Jack" 和 "jack" (大寫與小寫) 的字串。 如果 `GetWordCount` 方法能正常運作，它會針對搜尋文字傳回兩個實例計數。 為了刻意讓此測試失敗，您會先實作測試，以判斷提示 `GetWordCount` 方法沒有傳回搜尋文字 "Jack" 的兩個實例。 繼續進行下一個步驟以刻意讓測試失敗。

1. 開啟螢幕右側的 [單元測試]**** 面板。 從功能表中選擇 **"查看** > **測試**"。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac [單元測試] 面板](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. 按一下**固定**圖示維持面板開啟。 （在下圖中突出顯示。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac [單元測試] 面板固定圖示](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. 按一下 [全部執行]**** 按鈕。

   測試會失敗，這是正確的結果。 測試方法會判斷提示 `inputString` 的兩個實例 ("Jack") 沒有從提供給 `GetWordCount` 方法的字串 "Jack jack" 傳回。 由於文字大小寫的因素已經在 `GetWordCount` 方法中排除，因此會傳回兩個實例。 2「不等於」** 2 的判斷提示將會失敗。 這個結果是正確的結果，我們測試的邏輯是好的。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 測試失敗顯示畫面](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. 將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `IgnoreCasing` 測試方法。 使用鍵盤快速鍵<kbd>Ctrl</kbd>+<kbd>s</kbd>、**檔** > 從功能表**中保存**檔，或按一下檔的選項卡並選擇"從內容功能表**中保存**"。

   藉由將 `inputString` "Jack jack" 傳入 `GetWordCount`，您預期 `searchWord` "Jack" 會傳回兩個實例。 按一下螢幕底部 [單元測試]**** 面板中的 [執行測試]**** 按鈕或 [測試結果]**** 面板中的 [重新執行測試]**** 按鈕來重新執行測試。 測試會成功。 字串 "Jack jack" 中有兩個 "Jack" 實例 (忽略大小寫)，且測試判斷提示為 `true`。

   > [!div class="mx-imgBorder"]
   > ![用於 Mac 測試通過顯示的視覺化工作室](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. 使用 `Fact` 測試個別的傳回值，只是單元測試的初步用途。 另一個強大的技術，是使用 `Theory` 一次測試數個值。 將下列方法加入至 `TextUtils_GetWordCountShould` 類別。 在您加入此方法後，您在類別中會有兩個方法：

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` 會檢查 `GetWordCount` 方法是否能正確計數。 `InlineData` 提供要檢查的計數、搜尋文字，以及輸入字串。 測試方法會針對每一行資料各執行一次。 請注意，即使您知道資料中的計數是正確的，且值符合 `GetWordCount` 方法所傳回的計數，仍然要再次先使用 `Assert.NotEqual` 來判斷提示出錯誤。 執行刻意讓測試失敗的步驟，起初看起來似乎有點浪費時間，但是先透過讓測試失敗以檢查測試的邏輯，是一項對測試邏輯很重要的檢查。 當您遇到預期會失敗卻成功的測試方法時，代表測試邏輯中有錯誤。 每次當您建立測試方法時，都值得採取此步驟。

1. 儲存檔案，然後再次執行測試。 大小寫的測試會通過，但是三個計數測試會失敗。 這個結果正是你所期望的。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 預期的測試失敗](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. 將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `CountInstancesCorrectly` 測試方法。 儲存檔案。 再次執行測試。 所有測試皆通過。

   > [!div class="mx-imgBorder"]
   > ![適用于 Mac 預期測試通過的視覺工作室](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>新增主控台應用程式

1. 在 **"解決方案**"邊欄中，ctrl`WordCounter`按一下解決方案。 從 [.NET Core]**** > [應用程式]**** 範本中選取範本，來新增 [主控台應用程式]**** 專案。 選取 [下一步]****。 將專案命名為 **WordCounterApp**。 選取 [建立]**** 以在解決方案中建立專案。

1. 在 **"解決方案**"邊欄中，ctrl 按一下新**WordCounterApp**專案**的依賴項**節點。 在 [編輯參考]**** 對話方塊中，選取 [TextUtils]**** 並選取 [確定]****。

1. 打開*Program.cs*檔。 將代碼替換為以下代碼：

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/WordCounterApp/Program.cs)]

1. 按一下專案並`WordCounterApp`選擇"從內容功能表**中運行專案**"。 當您執行應用程式時，請根據主控台視窗中的提示，提供搜尋文字和輸入字串的值。 應用程式會指出搜尋文字在字串中出現的次數。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 主控台視窗，顯示您的應用程式正在執行](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. 最後一個要探索的功能，是使用 Visual Studio for Mac 進行偵錯。 在 `Console.WriteLine` 陳述式上設定中斷點：選取行 23 的左邊界，您會在程式碼行旁邊看見一個紅色圓圈。 或者，選擇程式碼上的任意位置，然後從功能表中選擇 **"運行** > **切換中斷點**"。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 中斷點設定](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. 按一下`WordCounterApp`專案。 從內容功能表中選擇 **"開始調試專案**"。 當應用程式執行時，輸入搜尋的文字 "cat"，以及 要搜尋的字串 "The dog chased the cat, but the cat escaped"。 當到達 `Console.WriteLine` 陳述式時，程式執行會在執行該陳述式之前中止。 在 **"區域變數"**`searchWord`選項卡中，您可以看到`inputString`、`wordCount`和`pluralChar`值。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 偵錯工具程式執行已停止](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. 在 [即時運算]**** 窗格中，輸入 "wordCount = 999"，並按 Enter。 此命令將無意義值 999 分配給`wordCount`變數，顯示您可以在調試時替換變數值。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 變更 [即時運算] 視窗中的值](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. 在工具列中，按一下 [繼續]** 箭號。 查看主控台視窗中的輸出。 它會報告您在對應用程式進行偵錯時所設定的不正確值，999。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 工具列中的 [繼續] 按鈕](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![Visual Studio for Mac 主控台視窗輸出](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

您可以使用同一過程使用單元測試專案調試代碼。 ctrl 按一下**測試庫**專案，並從內容功能表中選擇 **"開始調試專案**"，而不是啟動 WordCount 應用專案。 Mac 的視覺化工作室在連接調試器後啟動測試專案。 執行將停止在您添加到測試專案的任何中斷點或基礎庫代碼處。

## <a name="see-also"></a>另請參閱

- [Visual Studio 2019 for Mac 版本資訊](/visualstudio/releasenotes/vs2019-mac-relnotes)
