---
title: 在 Visual Studio 中使用 .NET Core 測試 .NET Standard 類別庫
description: 為您的 .NET Core 類別庫建立單元測試專案。 藉由單元測試確認您的 .NET Core 類別庫運作正常。
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 79b680022484bb9222b66c3df76bdd5a06de8117
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005007"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a>教學課程：在 Visual Studio 中使用 .NET Core 測試 .NET Standard 程式庫

本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。

## <a name="prerequisites"></a>必要條件

- 本教學課程適用于您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。

## <a name="create-a-unit-test-project"></a>建立單元測試專案

1. 開啟 `ClassLibraryProjects` 您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。

1. 將名為 "StringLibraryTest" 的新單元測試專案加入至方案。

   1. 以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。

   1. 在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**mstest** 。 選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。

   1. 選擇 [ **MSTest 測試專案（.Net Core）** ] 範本，然後選擇 **[下一步]**。

   1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibraryTest** 。 接著，選擇 [建立]  。

   > [!NOTE]
   > MSTest 是您可以從中選擇的三種測試架構之一。 其他則是 xUnit 和 nUnit。

1. Visual Studio 會建立專案，並使用下列程式碼在程式碼視窗中開啟類別檔案。 如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   單元測試範本建立的原始程式碼會執行下列動作︰

   - 它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。
   - 它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。
   - 它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性，以 `TestMethod1` 在 c # 中或 `TestSub` 在 Visual Basic 中定義。

   執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。

1. 在**方案總管**中，以滑鼠右鍵按一下**StringLibraryTest**專案的 [相依性] 節點，然後從內容功能表中選取 [**加入專案參考** **]** 。

1. 在 [**參考管理員**] 對話方塊中，展開 [**專案**] 節點，然後選取 [ **StringLibrary**] 旁的方塊。 將參考加入 `StringLibrary` 元件，可讓編譯器在編譯**StringLibraryTest**專案時尋找**StringLibrary**方法。

1. 選取 [確定]。

## <a name="add-and-run-unit-test-methods"></a>新增和執行單元測試方法

當 Visual Studio 執行單元測試時，它會在以屬性標記的類別中，執行以屬性標記的每個方法 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。 測試方法會在發現第一個失敗或方法中包含的所有測試都成功時結束。

最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。 許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。 `Assert`下表顯示一些類別最常被呼叫的方法：

| Assert 方法     | 函式 |
| ------------------ | -------- |
| `Assert.AreEqual`  | 驗證兩個值或物件相等。 如果值或物件不相等，判斷提示就會失敗。 |
| `Assert.AreSame`   | 驗證兩個物件變數參考相同的物件。 如果變數參考不同的物件，判斷提示就會失敗。 |
| `Assert.IsFalse`   | 驗證條件為 `false`。 如果條件為 `true`，判斷提示就會失敗。 |
| `Assert.IsNotNull` | 驗證物件不是 `null` 。 如果物件為 `null`，判斷提示就會失敗。 |

您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，以指出預期會擲回的例外狀況類型。 如果未擲回指定的例外狀況，測試將會失敗。

在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。 您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。 同樣地，您想提供幾個開頭不是大寫字元的字串。 您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。

由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)、沒有任何字元的有效字串，以及 <xref:System.String.Length> 未初始化的 `null` 字串。 如果在 `StartsWithUpper` 實例上呼叫作為擴充方法 <xref:System.String> ，則不能將字串傳遞給它 `null` 。 不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 <xref:System.String> 引數。

您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素重複呼叫方法。 因為測試方法會在發現第一次失敗時失敗，所以您會呼叫方法多載，讓您傳遞一個字串來表示方法呼叫中所使用的字串值。

建立測試方法：

1. 在 [ *UnitTest1.cs* ] 或 [ *unittest1.cpp* ] 程式碼視窗中，將程式碼取代為下列程式碼：

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。 方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。

1. 在功能表列上，選取 [ **file**  >  **save UnitTest1.cs as** ] 或 [ **file**  >  **save unittest1.cpp .vb as**]。 在 [另存新檔]**** 對話方塊中，選取 [儲存]**** 按鈕旁的箭號，然後選取 [以編碼方式儲存]*****。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio 另存新檔] 對話方塊](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. 在 [確認另存新檔]**** 對話方塊中，選取 [是]**** 按鈕以儲存檔案。

1. 在 [進階儲存選項]**** 對話方塊中，選取 [編碼]**** 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]****，然後選取 [確定]****。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio [進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advanced-save-options.png)

   如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。 發生這種情況時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。

1. 在功能表列上，選取 [**測試**] [執行] [  >  **所有測試**]。 如果 [**測試 explorer** ] 視窗未開啟，請選擇 [**測試**] [測試  >  **瀏覽器**] 加以開啟。 這三項測試都會列在 [通過的測試]**** 區段中，而 [摘要]**** 區段則報告測試回合的結果。

   > [!div class="mx-imgBorder"]
   > ![測試總管視窗，其中包含通過的測試](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>處理測試失敗

您的測試回合未失敗，但將它稍微變更，使其中一個測試方法失敗：

1. 修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。 您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. 從功能表列選取 [**測試**] [執行] [  >  **所有測試**] 來執行測試。 [測試總管]**** 視窗表示兩個測試成功，而且有一項失敗。

   > [!div class="mx-imgBorder"]
   > ![測試總管視窗，其中包含失敗的測試](./media/testing-library-with-visual-studio/failed-test-window.png)

1. 選取失敗的測試 `TestDoesNotStartWith` 。 **[測試總管]** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。 'Error' 的預期︰false；實際：True」。 因為失敗，在「錯誤」之後的陣列中的所有字串都未經過測試。

   > [!div class="mx-imgBorder"]
   > ![顯示 IsFalse 判斷提示失敗的測試 Explorer 視窗](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. 復原您在步驟 1 中所做的修改，並移除字串 "Error"。 重新執行測試和測試階段。

## <a name="test-the-release-version-of-the-library"></a>測試程式庫的發行版本

在執行程式庫的「偵錯工具」版本後，現在所有測試都已成功，請針對程式庫的發行組建，再次執行測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

測試發行組建︰

1. 在 Visual Studio 工具列中，將組建組態從 [偵錯]**** 變更為 [發行]****。

   > [!div class="mx-imgBorder"]
   > ![醒目提示 [發行] 組建的 Visual Studio 工具列](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. 在方案總管**** 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建]**** 以重新編譯程式庫。

   > [!div class="mx-imgBorder"]
   > ![StringLibrary 操作功能表和建置命令](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. 從功能表列中選擇 [**測試**] [執行] [  >  **所有測試**] 來執行單元測試。 所有測試皆通過。

## <a name="additional-resources"></a>其他資源

- [單元測試基本概念-Visual Studio](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已對類別庫進行單元測試。 您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [使用 Visual Studio 建立和發佈 NuGet 套件](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝並使用套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

程式庫不一定要以封裝的形式散發。 它可以與使用它的主控台應用程式配套。 若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：

> [!div class="nextstepaction"]
> [使用 Visual Studio 發行 .NET Core 主控台應用程式](publishing-with-visual-studio.md)
