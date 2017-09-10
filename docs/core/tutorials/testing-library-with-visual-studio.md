---
title: "在 Visual Studio 2017 中使用 .NET Core 測試類別庫"
description: "了解如何使用 Visual Studio 2017 測試以 C# 撰寫的類別庫"
keywords: ".NET Core, .NET 標準類別庫, Visual Studio 2017, 單元測試"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
ms.translationtype: HT
ms.sourcegitcommit: 3a25c1c3b540bac8ef963a8bbf708b0700c3e9e2
ms.openlocfilehash: 30e46ae97563add2bdf34948349cf2d6214d0de8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/08/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 .NET Core 測試類別庫

於[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫](library-with-visual-studio.md)或[在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core 建置類別庫](vb-library-with-visual-studio.md)中，您建立了一個將擴充方法新增至 <xref:System.String> 類別的簡易類別庫。 現在您將建立單元測試，確定它如預期般運作。 您會將您的單元測試專案新增至上一個主題中所建立的方案。

## <a name="creating-a-unit-test-project"></a>建立單元測試專案

若要建立單元測試專案，請執行下列作業︰

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. 在方案總管 中，開啟 **ClassLibraryProject** 方案節點的內容功能表，然後選取 [新增]  >  [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點。 然後選取後面跟著 [單元測試專案 (.NET Core)] 專案範本的 [.NET Core] 節點。 在 [名稱] 文字方塊中，輸入 "StringLibraryTest" 作為專案名稱。 選取 [確定] 以建立單元測試專案。

   ![[新增專案] 對話方塊](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > 除了單元測試專案之外，您也可以使用 Visual Studio 建立適用於 .NET Core 的 xUnit 測試專案。

1. Visual Studio 會建立專案，並在程式碼視窗中開啟 *UnitTest1.cs* 檔案。

   ![Visual Studio 程式碼視窗顯示預設的單元測試專案 UnitTest1 類別和 TestMethod1 方法](./media/testing-library-with-visual-studio/unittestwindow.png)

   單元測試範本建立的原始程式碼會執行下列動作︰

   * 它會匯入 [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) 命名空間，其中包含用於單元測試的類型。

   * 它會將 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性套用至 `UnitTest1` 類別。 執行單元測試時，在測試類別中標示 \[TestMethod\] 屬性的每個測試方法都將自動執行。

   * 它會套用 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。

1. 在方案總管 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性] 節點，然後從內容功能表中選取 [新增參考]。

   ![StringLibraryTest 相依性的內容功能表](./media/testing-library-with-visual-studio/addreference.png)

1. 在 [參考管理員] 對話方塊中，展開 [專案] 節點並核取 [StringLibrary] 旁的方塊。 將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。 選取 [確定] 按鈕。 這會在您的類別庫專案 `StringLibrary` 中新增參考。

   ![參考管理員](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. 在方案總管 中，開啟 **ClassLibraryProject** 方案節點的內容功能表，然後選取 [新增]  >  [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 [Visual Basic] 節點。 然後選取後面跟著 [單元測試專案 (.NET Core)] 專案範本的 [.NET Core] 節點。 在 [名稱] 文字方塊中，輸入 "StringLibraryTest" 作為專案名稱。 選取 [確定] 以建立單元測試專案。

   ![[新增專案] 對話方塊](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > 除了單元測試專案之外，您也可以使用 Visual Studio 建立適用於 .NET Core 的 xUnit 測試專案。

1. Visual Studio 會建立專案，並在程式碼視窗中開啟 *UnitTest1.vb* 檔案。

   ![Visual Studio 程式碼視窗顯示預設的單元測試專案 UnitTest1 類別和 TestMethod1 方法](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   單元測試範本建立的原始程式碼會執行下列動作︰

   * 它會匯入 [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) 命名空間，其中包含用於單元測試的類型。

   * 它會將 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性套用至 `UnitTest1` 類別。 執行單元測試時，在測試類別中標示 \[TestMethod\] 屬性的每個測試方法都將自動執行。

   * 它會套用 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。

1. 在方案總管 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性] 節點，然後從內容功能表中選取 [新增參考]。

   ![StringLibraryTest 相依性的內容功能表](./media/testing-library-with-visual-studio/addreference.png)

1. 在 [參考管理員] 對話方塊中，展開 [專案] 節點並核取 [StringLibrary] 旁的方塊。 將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。 選取 [確定] 按鈕。 這會在您的類別庫專案 `StringLibrary` 中新增參考。

   ![參考管理員](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>新增和執行單元測試方法

Visual Studio 執行單元測試時，它會執行單元測試類別 (即套用 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性的類別) 中標示 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性的每個方法。 測試方法會在發生第一次失敗時或方法中包含的所有測試均成功時結束。

最常見的測試會呼叫 [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) 類別的成員。 許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。 它最常呼叫的一些方法如下表所示。

Assert 方法 | 函式
--- | ---
`Assert.AreEqual` | 驗證兩個值或物件相等。 如果值或物件不相等，判斷提示就會失敗。
`Assert.AreSame` | 驗證兩個物件變數參考相同的物件。 如果變數參考不同的物件，判斷提示就會失敗。
`Assert.IsFalse` | 驗證條件為 `false`。 如果條件為 `true`，判斷提示就會失敗。
`Assert.IsNotNull` | 驗證物件不是 `null`。 如果物件為 `null`，判斷提示就會失敗。

您也可以將 [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) 屬性套用到測試方法。 指出測試方法預期擲回的例外狀況類型。 如果沒有擲回指定的例外狀況，測試便會失敗。

在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。 您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 [Assert.IsTrue (布林值,字串)](https://msdn.microsoft.com/library/ms243754.aspx) 方法。 同樣地，您想提供幾個開頭不是大寫字元的字串。 您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 [Assert.IsFalse (布林值,字串)](https://msdn.microsoft.com/library/ms243805.aspx) 方法。

因為您的程式庫方法會處理字串，您也想確定它會成功處理[空字串 (`String.Empty`)](xref:System.String.Empty)，這是不包含任何字元且其 @System.String.Length 為 0 的有效字串和尚未初始化的 `null` 字串。 如果在 @System.String 執行個體上呼叫 `StartsWithUpper` 做為擴充方法，它將無法傳遞 `null` 字串。 不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 @System.String 引數。

您會定義三個方法，每個方法會針對字串陣列中的每個項目重複呼叫其 [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) 方法。 因為測試方法會在發生第一次失敗時立即失敗，您將呼叫一個方法多載，以便傳遞一個字串來指示在方法呼叫中使用的字串值。

建立測試方法：

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. 在 *UnitTest1.cs* 程式碼視窗中，以下列程式碼取代程式碼：

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   請注意，您在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。

1. 在功能表列上，選取 [檔案] >  [將 UnitTest1.cs As 另存為]。 在 [另存新檔] 對話方塊中，選取 [儲存] 按鈕旁的箭號，然後選取 [以編碼方式儲存]*。

   ![[另存新檔] 對話方塊](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. 在 *UnitTest1.vb* 程式碼視窗中，以下列程式碼取代程式碼：

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   請注意，您在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。

1. 在功能表列上，選取 [檔案] > [將 UnitTest1.vb 另存為]。 在 [另存新檔] 對話方塊中，選取 [儲存] 按鈕旁的箭號，然後選取 [以編碼方式儲存]*。

   ![[另存新檔] 對話方塊](./media/testing-library-with-visual-studio/savefileas.png)
---

1. 在 [確認另存新檔] 對話方塊中，選取 [是] 按鈕以儲存檔案。

1. 在 [進階儲存選項] 對話方塊中，選取 [編碼] 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]，然後選取 [確定]。

   ![[進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。 發生該情況時，執行階段無法正確解碼 ASCII 範圍之外的 UTF8 字元，因此測試結果將不精確。

1. 在功能表列中，選取 [測試]  >  [執行]  >  [所有測試]。 [測試總管] 視窗隨即開啟並顯示測試成功執行。 這三項測試都會列在 [通過的測試] 區段中，而 [摘要] 區段則報告測試回合的結果。

   ![[測試總管] 視窗](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a>處理測試失敗

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
1. 從功能表列中，選取 [測試]  >  [執行]  >  [所有測試] 來執行測試。 [測試總管] 視窗表示兩個測試成功，而且有一項失敗。

   ![[測試總管] 視窗](./media/testing-library-with-visual-studio/failedtest.png)

1. 在 [失敗的測試] 區段中，選取失敗的測試 `TestDoesNotStartWith`。 [測試總管] 視窗會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。 'Error' 的預期︰false；實際：True」。 因為發生失敗，陣列中 "Error" 之後的所有字串並未經過測試。

   ![[測試總管] 視窗顯示「為 False」的判斷提示失敗](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. 移除已新增的程式碼 (`"Error", `)，然後重新執行測試。 測試將通過。

## <a name="testing-the-release-version-of-the-library"></a>測試程式庫的發行版本

您已針對偵錯版本的程式庫執行測試。 既然您的測試全部通過，並已充分測試過您的程式庫，您應針對程式庫的發行組建執行更多時間的測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

測試發行組建︰

1. 在 Visual Studio 工具列中，將組建組態從 [偵錯] 變更為 [發行]。

   ![Visual Studio 工具列](./media/testing-library-with-visual-studio/toolbar.png)

1. 在方案總管 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建] 以重新編譯程式庫。

   ![StringLibrary 內容功能表](./media/testing-library-with-visual-studio/buildlibrary.png)

1. 從功能表列中，選擇 [測試]  >  [執行]  >  [所有測試] 來執行單元測試。 所有測試皆通過。

既然您已經完成程式庫測試，下一步是將它提供給呼叫端。 您可以將它與一或多個應用程式搭售，或是將將它發佈為 NuGet 套件。 如需詳細資訊，請參閱[使用 .NET Standard 類別庫](./consuming-library-with-visual-studio.md)。

