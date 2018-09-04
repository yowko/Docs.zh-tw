---
title: 使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 解決方案
description: 本主題會逐步引導您建置一個包含可重複使用之程式庫和單元測試的 .NET Core 解決方案。
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: 17d7cc5b085b4d47ebf1e5ed9a766be9d5d8b01f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530492"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 解決方案

Visual Studio for Mac 針對開發 .NET Core 應用程式，提供功能完整的整合式開發環境 (IDE)。 本主題會逐步引導您建置一個包含可重複使用之程式庫和單元測試的 .NET Core 解決方案。

本教學課程會示範如何建立能接受來自使用者的搜尋文字和文字字串、使用類別庫中的方法計算搜尋文字出現在字串中的次數，並將結果傳回給使用者的應用程式。 解決方案也包含類別庫的單元測試，作為單元測試概念的簡介。 如果您偏好使用完整範例來進行教學課程，請下載[範例解決方案 (英文)](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter)。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

> [!NOTE]
> 我們非常重視您的意見反應。 您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：
> * 在 Visual Studio for Mac 中，從功能表選取 [說明] > [回報問題]，或從歡迎畫面選取 [回報問題]，這會開啟用來提出錯誤報告的視窗。 您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。
> * 若要提出建議，請從功能表選取 [說明] > [提供建議]，或從歡迎畫面選取 [提供建議]，這會帶您前往 [Visual Studio for Mac UserVoice 網頁](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac) \(英文\)。

## <a name="prerequisites"></a>必要條件

- OpenSSL (如果執行 .NET Core 1.1)：請參閱 [Mac 上 .NET Core 的先決條件](../macos-prerequisites.md)主題。
- [.NET Core SDK 1.1 或更新版本](https://www.microsoft.com/net/core#macos)
- [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

如需必要條件的詳細資訊，請參閱 [Mac 上 .NET Core 的先決條件](../../core/macos-prerequisites.md)。 如需 Visual Studio 2017 for Mac 的完整系統需求，請參閱 [Visual Studio 2017 for Mac 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-mac)。

## <a name="building-a-library"></a>建置程式庫

1. 選取歡迎畫面上的 [新增專案]。 在 [多平台] 節點下的 [新增專案] 對話方塊中，選取 [.NET 標準程式庫] 範本。 選取 [下一步]。

   ![[新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. 將專案命名為 "TextUtils" (「文字公用程式」的簡短名稱)，並將解決方案命名為 "WordCounter"。 保持選取 [在解決方案目錄中建立專案目錄]。 選取 [建立]。

   ![[新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. 在 [解決方案] 提要欄位中，展開 `TextUtils` 節點以顯示範本所提供的類別檔案 *Class1.cs*。 以滑鼠右鍵按一下該檔案，從操作功能表選取 [重新命名]，並將檔案重新命名為 *WordCount.cs*。 開啟檔案，並以下列程式碼取代內容：

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. 使用下列三種方法之一來儲存檔案：使用鍵盤快速鍵 <kbd>&#8984;</kbd>+<kbd>s</kbd>、從功能表選取 [檔案] > [儲存]，或以滑鼠右鍵按一下檔案的索引標籤，並從操作功能表選取 [儲存]。 下圖顯示 IDE 視窗︰

   ![顯示 TextUtils 類別庫、WordCount 類別檔案、靜態類別 WordCount，以及 GetWordCount 方法的 IDE 視窗](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. 選取 IDE 視窗下邊界中的 [錯誤]，以開啟 [錯誤] 面板。 選取 [建置輸出] 按鈕。

   ![IDE 的下邊界，顯示 [錯誤] 按鈕](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. 從功能表選取 [建置] > [全部建置]。

   解決方案隨即建置。 建置輸出面板會顯示建置成功。

   ![[錯誤] 面板的 [建置輸出] 窗格，顯示「建置成功」訊息](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>建立測試專案

單元測試能在開發與發佈期間提供自動化的軟體測試。 您在本教學課程中使用的測試架構是 [xUnit (版本 2.2.0 或更新版本)](https://xunit.github.io/)，這會在下列步驟中 xUnit 測試專案加入解決方案時自動安裝：

1. 在 [解決方案] 提要欄位中，以滑鼠右鍵按一下 `WordCounter` 解決方案，並選取 [新增] > [新增專案]。

1. 在 [新增專案] 對話方塊中，從 [.NET Core] 節點選取 [測試]。 選取 [xUnit 測試專案]，接著選取 [下一步]。

   ![建立 xUnit 測試專案的 [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. 將新專案命名為 "TestLibrary"，並選取 [建立]。

   ![提供專案名稱的 [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. 為了讓測試程式庫能搭配 `WordCount` 類別使用，請將參考加入 `TextUtils` 專案。 在 [解決方案] 提要欄位中，以滑鼠右鍵按一下 [TestLibrary] 底下的 [相依性]。 從操作功能表選取 [編輯參考]。

1. 在 [編輯參考] 對話方塊中，選取 [專案] 索引標籤上的 [TextUtils] 專案。選取 [確定]。

   ![[編輯參考] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. 在 [TestLibrary] 專案中，將 *UnitTest1.cs* 檔案重新命名為 *TextUtilsTests.cs*。

1. 開啟檔案，並以下列內容取代程式碼：

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

   ![IDE 主視窗中用來檢查 GetWordCount 的初始單元測試](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   請務必讓新的測試失敗一次，以確認其測試邏輯正確。 該方法會傳入 "Jack" (大寫) 這個名字，以及具有 "Jack" 和 "jack" (大寫與小寫) 的字串。 如果 `GetWordCount` 方法能正常運作，它會針對搜尋文字傳回兩個實例計數。 為了刻意讓此測試失敗，您會先實作測試，以判斷提示 `GetWordCount` 方法沒有傳回搜尋文字 "Jack" 的兩個實例。 繼續進行下一個步驟以刻意讓測試失敗。

1. 開啟螢幕右側的 [單元測試] 面板。

   ![單元測試面板](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. 按一下**固定**圖示維持面板開啟。

   ![單元測試面板固定圖示](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. 按一下 [全部執行] 按鈕。

   測試會失敗，這是正確的結果。 測試方法會判斷提示 `inputString` 的兩個實例 ("Jack") 沒有從提供給 `GetWordCount` 方法的字串 "Jack jack" 傳回。 由於文字大小寫的因素已經在 `GetWordCount` 方法中排除，因此會傳回兩個實例。 2「不等於」2 的判斷提示將會失敗。 這是正確的結果，並證明測試的邏輯是良好的。

   ![測試失敗](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. 將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `IgnoreCasing` 測試方法。 使用鍵盤快速鍵 <kbd>&#8984;</kbd>+<kbd>s</kbd>、功能表的 [檔案] > [儲存]，或是以滑鼠右鍵按一下檔案的索引標籤，並從操作功能表選取 [儲存] 來儲存檔案。

   藉由將 `inputString` "Jack jack" 傳入 `GetWordCount`，您預期 `searchWord` "Jack" 會傳回兩個實例。 按一下螢幕底部 [單元測試] 面板中的 [執行測試] 按鈕或 [測試結果] 面板中的 [重新執行測試] 按鈕來重新執行測試。 測試就會成功。 字串 "Jack jack" 中有兩個 "Jack" 實例 (忽略大小寫)，且測試判斷提示為 `true`。

   ![測試成功](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

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

1. 儲存檔案，然後再次執行測試。 大小寫的測試會通過，但是三個計數測試會失敗。 這正是您預期會發生的情況。

   ![測試失敗](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. 將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `CountInstancesCorrectly` 測試方法。 儲存檔案。 再次執行測試。 所有測試皆通過。

   ![測試成功](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>新增主控台應用程式

1. 在 [解決方案] 提要欄位中，以滑鼠右鍵按一下 `WordCounter` 解決方案。 從 [.NET Core] > [應用程式] 範本中選取範本，來新增 [主控台應用程式] 專案。 選取 [下一步]。 將專案命名為 **WordCounterApp**。 選取 [建立] 以在解決方案中建立專案。

1. 在 [解決方案] 提要欄位中，以滑鼠右鍵按一下新的 [WordCounterApp] 專案的 [相依性] 節點。 在 [編輯參考] 對話方塊中，選取 [TextUtils] 並選取 [確定]。

1. 開啟 *Program.cs* 檔案。 使用下列內容取代程式碼：

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. 若要在主控台視窗而非 IDE 中執行應用程式，請以滑鼠右鍵按一下 `WordCounterApp` 專案，選取 [選項]，並開啟 [組態] 底下的 [預設] 節點。 選取 [在外部主控台上執行] 方塊。 保持選取 [暫停主控台輸出] 選項。 此設定會造成應用程式在主控台視窗中繁衍，讓您可以輸入 `Console.ReadLine` 陳述式的輸入。 如果您讓應用程式在 IDE 中執行，便只能看見 `Console.WriteLine` 陳述式的輸出。 `Console.ReadLine` 陳述式不能在 IDE 的 [應用程式輸出] 面板中運作。

   ![[專案選項] 視窗](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. 由於目前版本的 Visual Studio for Mac 無法在解決方案執行時執行測試，您必須直接執行主控台應用程式。 以滑鼠右鍵按一下 `WordCounterApp` 專案，並從操作功能表中選取 [執行項目]。 如果您嘗試使用 [播放] 按鈕執行應用程式，測試執行器和應用程式會無法執行。 如需此問題工作狀態的詳細資訊，請參閱 [xunit/xamarinstudio.xunit (#60) (英文)](https://github.com/xunit/xamarinstudio.xunit/issues/60)。 當您執行應用程式時，請根據主控台視窗中的提示，提供搜尋文字和輸入字串的值。 應用程式會指出搜尋文字在字串中出現的次數。

   ![主控台視窗，顯示字串 'Iro ate olives by the lake, and the olives were wonderful' 中搜尋文字 olives。 應用程式回應「搜尋文字 olives 出現 2 次」。](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. 最後一個要探索的功能，是使用 Visual Studio for Mac 進行偵錯。 在 `Console.WriteLine` 陳述式上設定中斷點：選取行 23 的左邊界，您會在程式碼行旁邊看見一個紅色圓圈。 或者，選取程式碼行上的任何位置，並從功能表選取 [執行] > [切換中斷點]。

   ![行 23 (Console.WriteLine 陳述式) 上已設定中斷點](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. 以滑鼠右鍵按一下 `WordCounterApp` 專案。 從操作功能表選取 [開始偵錯項目]。 當應用程式執行時，輸入搜尋的文字 "cat"，以及 要搜尋的字串 "The dog chased the cat, but the cat escaped"。 當到達 `Console.WriteLine` 陳述式時，程式執行會在執行該陳述式之前中止。 在 [區域變數] 索引標籤中，您可以看到 `searchWord`、`inputString`、`wordCount` 及 `pluralChar` 值。

   ![程式執行於 Console.WriteLine 陳述式停止，[區域變數] 視窗顯示執行 Console.WriteLine 陳述式之前的值。](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. 在 [即時運算] 窗格中，輸入 "wordCount = 999"，並按 Enter。 這會將無意義值 999 指派給 `wordCount` 變數，顯示您可以在進行偵錯時取代變數值。

   ![已叫用中斷點。 [即時運算] 視窗中的 wordCount 已變更為 999 的值](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. 在工具列中，按一下 [繼續] 箭號。 查看主控台視窗中的輸出。 它會報告您在對應用程式進行偵錯時所設定的不正確值，999。

   ![工具列中的 [繼續] 按鈕](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![應用程式輸出中的搜尋文字計數已變更為 999 的值](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>另請參閱

* [Visual Studio 2017 for Mac 版本資訊](/visualstudio/releasenotes/vs2017-mac-relnotes)
