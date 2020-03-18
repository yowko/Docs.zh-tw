---
title: 在視覺化工作室中使用 .NET 核心測試 .NET 標準類庫
description: 為您的 .NET Core 類別庫建立單元測試專案。 藉由單元測試確認您的 .NET Core 類別庫運作正常。
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156617"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>在視覺化工作室中使用 .NET 核心測試 .NET 標準庫

在[Visual Studio 中構建 .NET 標準庫中](library-with-visual-studio.md)，您創建了一個簡單的類庫，向<xref:System.String>類添加擴充方法。 現在您將建立單元測試，確定它如預期般運作。 我們會將我們的單元測試專案加入在上一篇文章中建立的方案。

## <a name="create-a-unit-test-project"></a>建立單元測試專案

若要建立單元測試專案，請執行下列作業︰

1. 打開在`ClassLibraryProjects`Visual Studio 文章中[生成 .NET 標準庫中](library-with-visual-studio.md)創建的解決方案。

1. 向解決方案添加名為"StringLibraryTest"的新單元測試專案。

   1. 按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。

   1. 在"**添加新專案**"頁上，在搜索框中輸入**mstest。** 從"語言"清單中選擇**C#** 或**視覺化基本，** 然後從"平臺"清單中選擇 **"所有平臺**"。 選擇**MsTest 測試專案 （.NET 核心）** 範本，然後選擇 **"下一步**"。

   1. 在"**配置新專案**"頁上，在 **"專案名稱"** 框中輸入**字串庫測試**。 然後選擇 [建立]****。

   > [!NOTE]
   > 除了 MSTest 之外，您還可以在視覺化工作室中為 .NET Core 創建 xUnit 和 nUnit 測試專案。

1. Visual Studio 創建專案，並在代碼視窗中使用以下代碼打開類檔：

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

   - 它會將 [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) 屬性套用至 `UnitTest1` 類別。 執行單元測試時，在測試類別中標示 [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) 屬性的每個測試方法都將自動執行。

   - 它將[TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)屬性應用於在`TestMethod1`C#`TestSub`或 Visual Basic 中定義，作為運行單元測試時自動執行的測試方法。

1. 在方案總管**** 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性]**** 節點，然後從內容功能表中選取 [新增參考]****。

   > [!div class="mx-imgBorder"]
   > ![字串庫測試依賴項的內容功能表](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. 在 [參考管理員]**** 對話方塊中，展開 [專案]**** 節點並核取 [StringLibrary]**** 旁的方塊。 將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。 選擇"**確定"** 按鈕。 引用將添加到類庫專案 。 `StringLibrary`

   ![視覺化工作室中的參考管理器對話方塊](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>添加和運行單元測試方法

當 Visual Studio 運行單元測試時，它將執行在單元測試類中<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>標記屬性的每個方法，即應用該屬性的<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>類。 當發現第一個失敗或該方法中包含的所有測試都成功時，測試方法將結束。

最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。 許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。 `Assert`類中一些最常用的方法顯示在下表中：

| Assert 方法     | 函式 |
| ------------------ | -------- |
| `Assert.AreEqual`  | 驗證兩個值或物件相等。 如果值或物件不相等，斷言將失敗。 |
| `Assert.AreSame`   | 驗證兩個物件變數參考相同的物件。 如果變數參考不同的物件，判斷提示就會失敗。 |
| `Assert.IsFalse`   | 驗證條件為 `false`。 如果條件為 `true`，判斷提示就會失敗。 |
| `Assert.IsNotNull` | 驗證物件不是`null`。 如果物件為 `null`，判斷提示就會失敗。 |

您還可以在測試方法中使用<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A>方法來指示預期要引發的異常類型。 如果未引發指定的異常，則測試將失敗。

在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。 您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> 方法。 同樣地，您想提供幾個開頭不是大寫字元的字串。 您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> 方法。

由於庫方法處理字串，您還希望確保它成功處理[一個空字串`String.Empty`（），](xref:System.String.Empty)一個沒有字元且其<xref:System.String.Length>為 0 的有效字串，以及尚未初始化的`null`字串。 如果在`StartsWithUpper`<xref:System.String>實例上調用為擴充方法，則無法傳遞`null`字串。 不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 <xref:System.String> 引數。

您將定義三種方法，每個方法都針對字串陣列中的每個<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>元素重複調用一個方法。 由於 test 方法發現第一個失敗後立即失敗，因此您將調用一個方法重載，該重載允許您傳遞指示方法調用中使用的字串值的字串。

建立測試方法：

1. 在*UnitTest1.cs*或*UnitTest1.vb*代碼視窗中，用以下代碼替換代碼：

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   `TestStartsWithUpper`該方法中的大寫字元測試包括希臘大寫字母 Alpha （U+0391） 和西瑞爾大寫字母 EM （U+041C）。 `TestDoesNotStartWithUpper`該方法中小寫字元的測試包括希臘小寫字母 Alpha （U+03B1） 和西瑞爾小字母 Ghe （U+0433）。

1. 在功能表列上，選擇 **"檔** > **保存UnitTest1.cs為**或**檔** > **保存單元測試1.vb為**。 在 [另存新檔]**** 對話方塊中，選取 [儲存]**** 按鈕旁的箭號，然後選取 [以編碼方式儲存]*****。

   > [!div class="mx-imgBorder"]
   > ![視覺化工作室保存檔作為對話方塊](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. 在 [確認另存新檔]**** 對話方塊中，選取 [是]**** 按鈕以儲存檔案。

1. 在 [進階儲存選項]**** 對話方塊中，選取 [編碼]**** 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]****，然後選取 [確定]****。

   > [!div class="mx-imgBorder"]
   > ![Visual Studio [進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advanced-save-options.png)

   如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。 發生這種情況時，運行時無法準確解碼 ASCII 範圍之外的 UTF8 字元，並且測試結果將不正確。

1. 在功能表列上，選擇 **"測試** > **運行** > **所有測試**"。 [測試總管]**** 視窗隨即開啟並顯示測試成功執行。 這三項測試都會列在 [通過的測試]**** 區段中，而 [摘要]**** 區段則報告測試回合的結果。

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

1. 通過從功能表列中選擇 **"測試** > **運行** > **所有測試**"來運行測試。 [測試總管]**** 視窗表示兩個測試成功，而且有一項失敗。

   > [!div class="mx-imgBorder"]
   > ![測試總管視窗，其中包含失敗的測試](./media/testing-library-with-visual-studio/failed-test-window.png)

1. 選擇失敗的測試。 `TestDoesNotStartWith` **[測試總管]** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。 'Error' 的預期︰false；實際：True」。 由於失敗，陣列中"錯誤"後的所有字串都未測試。

   > [!div class="mx-imgBorder"]
   > ![顯示 IsFalse 宣告失敗的測試資源管理器視窗](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. 復原您在步驟 1 中所做的修改，並移除字串 "Error"。 重新執行該測試，測試將會通過。

## <a name="test-the-release-version-of-the-library"></a>測試庫的發佈版本

您已針對偵錯版本的程式庫執行測試。 既然您的測試全部通過，並已充分測試過您的程式庫，您應針對程式庫的發行組建執行更多時間的測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

測試發行組建︰

1. 在 Visual Studio 工具列中，將組建組態從 [偵錯]**** 變更為 [發行]****。

   > [!div class="mx-imgBorder"]
   > ![醒目提示 [發行] 組建的 Visual Studio 工具列](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. 在方案總管**** 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建]**** 以重新編譯程式庫。

   > [!div class="mx-imgBorder"]
   > ![StringLibrary 操作功能表和建置命令](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. 通過從功能表列中選擇 **"測試** > **運行** > **所有測試**"來運行單元測試。 所有測試皆通過。

既然您已經完成程式庫測試，下一步是將它提供給呼叫端。 您可以將它與一或多個應用程式搭售，或是將將它發佈為 NuGet 套件。 如需詳細資訊，請參閱[使用 .NET Standard 類別庫](consuming-library-with-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [單元測試基礎知識 - 視覺化工作室](/visualstudio/test/unit-test-basics)
