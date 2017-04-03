---
title: "在 Visual Studio 2017 中使用 .NET Core 測試類別庫"
description: "了解如何使用 Visual Studio 2017 測試以 C# 撰寫的類別庫"
keywords: ".NET Core, .NET 標準類別庫, Visual Studio 2017, 單元測試"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee21799706b971f0ec13285b0771b32b4367f570
ms.lasthandoff: 03/13/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 .NET Core 測試類別庫 #

在[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫](library-with-visual-studio-2017.md)中，我們已建立一個將擴充方法加入 @System.String類別的簡易類別庫。 現在我們將建立單元測試，確定它如預期般運作。 我們會將我們的單元測試專案加入在上一個主題中建立的方案。

## <a name="creating-a-unit-test-project"></a>建立單元測試專案 ##

若要建立單元測試專案，請執行下列作業︰

1. 在 [方案總管] 中，開啟 **ClassLibraryProject** 方案節點的操作功能表，然後依序選擇 [加入]****、[新增專案]****。

   <!-- Need a VS 2017 version  [!NOTE] In addition to a Unit Test project, you can also use Visual Studio to create an XUnit test project for .NET Core. For a walkthrough that includes an XUnit test project, see [Getting started with .NET Core on Windows, using Visual Studio 2015](../../core/tutorials/using-on-windows.md). --> 

1. 在 [加入新專案]**** 對話方塊方塊中，展開 **Visual C#** 節點和 **.NET Core** 節點，然後選擇 [單元測試專案 (.NET Core)]**** 專案範本，並命名為 `StringLibraryTest`，如下圖所示。

   ![Image](./media/testproject.jpg)

1. 選擇 [確定]**** 按鈕以建立專案。 Visual Studio 就會建立專案，並在程式碼視窗中開啟 `UnitTest1.cs` 檔案，如下圖所示。

   ![Image](./media/unit_test_code_window.jpg)

   單元測試範本建立的原始程式碼會執行下列動作︰

   - 它會匯入 [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) 命名空間，其中包含用於單元測試的類型。

   - 它會將 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性套用至 `UnitTest1` 類別。 執行自動單元測試時，在測試類別中標示 \[TestMethod\] 屬性的每個測試方法將會自動執行。

   - 它會套用 [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。

1. 在 [方案總管] 中，開啟 **StringLibraryTest** 專案的 [相依性]**** 節點的操作功能表，然後選擇 [加入參考]****。 這會在我們的類別庫專案 `StringLibrary`中加入參考。 

1. 在 [參考管理員]**** 對話方塊中，展開 [專案]**** 節點，選擇 [方案]****，然後選擇 **StringLibrary** 旁的核取方塊，如下圖所示。 將參考加入 `StringLibrary` 組件，可讓編譯器解析 **StringLibrary** 方法的呼叫。

   ![Image](./media/add_reference.jpg)

1. 按一下 [確定]**** 按鈕以關閉 [參考管理員]**** 對話方塊。

## <a name="adding-and-running-unit-test-methods"></a>新增和執行單元測試方法 ##

Visual Studio 執行單元測試時，它會執行單元測試 (即套用 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性的類別) 中標示 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性的每個方法。 測試方法會在發生第一次失敗時或方法中包含的所有測試均成功時結束。

最常見的測試會呼叫 [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) 類別的成員。 許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。 它最常呼叫的一些方法包括︰

- `Assert.AreEqual`，會驗證兩個值或物件是否相等。 如果值或物件不相等，判斷提示就會失敗。

- `Assert.AreSame`，會驗證兩個物件變數是否參考相同的物件。 如果變數參考不同的物件，判斷提示就會失敗。

- `Assert.IsFalse`，會驗證條件是否為 False。 如果條件為 True，判斷提示就會失敗。

- `Assert.IsNotNull`，會驗證物件是否不為 `null`。 如果物件為 `null`，判斷提示就會失敗。

此外，[ \[ExpectedException\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) 屬性可用來指示測試方法應該擲回的例外狀況類型。 您可以使用它來測試應該會導致例外狀況的條件。 如果沒有擲回指定的例外狀況，測試便會失敗。

在測試 `StringLibrary.StartsWithUpper` 方法時，我們想提供幾個以大寫字元開頭的字串。 我們預期這個方法在這些情況下傳回 `True`，因此我們可以呼叫 [Assert.IsTrue (布林值、字串)](https://msdn.microsoft.com/library/ms243754.aspx) 方法。 同樣地，我們想提供幾個開頭不是大寫字元的字串。 我們預期這個方法在這些情況下傳回 False，因此我們可以呼叫 [Assert.IsFalse (布林值、字串)](https://msdn.microsoft.com/library/ms243805.aspx) 方法。

因為我們的程式庫方法會處理字串，我們也想確定它會成功處理[空字串](xref:System.String.Empty) (不包含任何字元且其 @System.String.Length 為 0 的有效字串) 和 `null` 字串 (未初始化的字串)。 如果在 @System.String 執行個體上呼叫 `StartsWithUpper` 做為擴充方法，它將無法傳遞 `null` 字串。 不過，它也可以直接做為靜態方法呼叫，並傳遞單一 @System.String 引數。

我們會定義三個方法，每個方法會針對字串陣列中的每個元素重複呼叫其 [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) 方法。 因為測試方法會在發生第一次失敗時失敗，我們將呼叫一個方法多載，以便傳遞一個字串來指示在方法呼叫中使用的字串值。

建立測試方法：

1. 以下面程式碼取代程式碼視窗中的程式碼：

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs#1)]

   請注意，我們在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。

1. 在功能表列上，選擇 [檔案]****、[將 UnitTest1.cs As 另存為]****。 在 [另存新檔]**** 對話方塊中，選擇 [儲存]**** 按鈕旁的箭號，然後選擇 [以編碼方式儲存]*****。

1. 在 [確認另存新檔] 對話方塊中，選擇 [是]**** 按鈕以儲存檔案。

1. 從 [進階儲存選項]**** 對話方塊的 [編碼]**** 下拉式清單中選擇 [Unicode (UTF-8 有簽章) - 字碼頁 65001]****，然後選擇 [確定]****。

   如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。 在此情況下，執行階段將無法正確解碼 ASCII 範圍之外的字元，因此測試結果將不精確。

1. 在功能表列上，選擇 [測試]****、[執行]****、[所有測試]****。 [測試總管]**** 視窗應該會開啟，並顯示這兩個測試都執行成功，如下圖所示。 請注意，這三項測試都會列在 [通過的測試]**** 區段中，而 [摘要]**** 區段則報告測試回合的結果。

   ![Image](./media/first_test.jpg)

## <a name="handling-test-failures"></a>處理測試失敗 ##

我們的測試回合未失敗，因此，現在我們將它稍微變更，使其中一個測試方法失敗︰

1. 修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列以包含字串 "Error"，使陳述式如以下所示︰

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. 選擇 [測試]****、[執行]****、[所有測試]**** 以執行測試。 [測試總管]**** 視窗現在會指出兩項測試成功，一項測試失敗，如下圖所示。

   ![Image](./media/failed_test.jpg)

1. 在 [失敗的測試]**** 區段中選擇失敗的測試 `TestDoesNotStartWith`。 [測試總管]**** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。 預期為 'Error': false; 實際為: True」，如 [測試總管]**** 的下圖所示。 因為發生失敗，陣列中 "Error" 之後的所有字串並未經過測試。

   ![Image](./media/failed_test2.jpg)

1. 移除已加入的程式碼 (`"Error", `)，然後重新執行測試。 它現在應該會傳遞。

## <a name="testing-the-release-version-of-the-library"></a>測試程式庫的發行版本 ##

我們已針對偵錯版本的程式庫執行測試。 既然我們的測試全部通過，並已充分測試過我們的程式庫，我們應針對程式庫的發行組建執行更多時間的測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

測試發行組建︰

1. 在 Visual Studio 工具列中，將組建組態從 [偵錯]**** 變更為 [發行]****。 下圖顯示工具列的一部分。

   ![Image](./media/lib_release.jpg)

1. 在 [方案總管]**** 中，開啟 **StringLibrary** 專案節點的操作功能表，然後選擇 [建置]**** 以重新編譯程式庫。

1. 從 Visual Studio 功能表中選擇 [測試]****、[執行]****、[所有測試]**** 以重新執行單元測試。 測試應該會通過。

既然您已經完成程式庫測試，下一步是將它提供給呼叫端。 您可以將它與一或多個應用程式搭售，或是將將它發佈為 NuGet 套件。 如需如何執行的詳細資訊，請參閱[使用 .NET 標準類別庫](./consuming-library-with-visual-studio-2017.md)。

