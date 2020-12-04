---
title: 使用 Visual Studio for Mac 測試 .NET 類別庫
description: 建立 .NET 類別庫的單元測試專案。 確認 .NET 類別庫可在單元測試中正確運作。
ms.date: 11/18/2020
ms.openlocfilehash: 02d5aa74258ec15c5447b23246a3c7e9c61a6760
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599522"
---
# <a name="test-a-net-class-library-using-visual-studio"></a>使用 Visual Studio 測試 .NET 類別庫

本教學課程示範如何將測試專案加入至方案，以自動化單元測試。

## <a name="prerequisites"></a>必要條件

- 本教學課程適用于 [使用 Visual Studio for Mac 建立 .net 類別庫](library-with-visual-studio-mac.md)中所建立的方案。

## <a name="create-a-unit-test-project"></a>建立單元測試專案

單元測試能在開發與發佈期間提供自動化的軟體測試。 [MSTest](https://github.com/Microsoft/testfx-docs) 是您可以從中選擇的三種測試架構之一。 其他則為 [xUnit](https://xunit.net/) 和 [nUnit](https://nunit.org/)。

1. 開始 Visual Studio for Mac。

1. 開啟 `ClassLibraryProjects` 您在 [使用 Visual Studio for Mac 建立 .net 類別庫](library-with-visual-studio-mac.md)中建立的方案。

1. 在 **solution** pad 中， <kbd>ctrl +</kbd>按一下 `ClassLibraryProjects` 方案，然後選取 [**加入**  >  **新專案**]。

1. 在 [**新增專案**] 對話方塊中，從 [ **Web] 和 [主控台**] 節點選取 [**測試**]。 選取 [ **MSTest] 專案** ，然後選取 **[下一步]**。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="建立測試專案 Visual Studio Mac [新增專案] 對話方塊":::

1. 選取 [ **.net 5.0** ] 作為 **目標架構** ，然後選取 **[下一步]**。

1. 將新專案命名為 "StringLibraryTest"，然後選取 [ **建立**]。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="提供專案名稱的 Visual Studio Mac [新增專案] 對話方塊":::

   Visual Studio 會使用下列程式碼建立類別檔案：

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

   單元測試範本建立的原始程式碼會執行下列動作︰

   - 它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。
   - 它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。
   - 它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性套用至 `TestMethod1` 。

   執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。

## <a name="add-a-project-reference"></a>新增專案參考

若要讓測試專案使用 `StringLibrary` 類別，請將參考加入至 `StringLibrary` 專案。

1. 在 **Solution** pad 中，依序按一下 [ **StringLibraryTest**] 底下的 [相依性 **]** 。 <kbd>ctrl</kbd> 從內容功能表選取 [ **加入參考** ]。

1. 在 [ **參考** ] 對話方塊中，選取 [ **StringLibrary** ] 專案。 選取 [確定]。

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac [編輯參考] 對話方塊":::

## <a name="add-and-run-unit-test-methods"></a>加入並執行單元測試方法

當 Visual Studio 執行單元測試時，它會執行每個以屬性標記之 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 類別中的屬性標記的方法  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。 當找到第一個失敗或方法中包含的所有測試都成功時，測試方法便會結束。

最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。 許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。 `Assert`下表顯示某些類別最常呼叫的方法：

| Assert 方法     | 函數 |
| ------------------ | -------- |
| `Assert.AreEqual`  | 驗證兩個值或物件相等。 如果值或物件不相等，判斷提示就會失敗。 |
| `Assert.AreSame`   | 驗證兩個物件變數參考相同的物件。 如果變數參考不同的物件，判斷提示就會失敗。 |
| `Assert.IsFalse`   | 驗證條件為 `false`。 如果條件為 `true`，判斷提示就會失敗。 |
| `Assert.IsNotNull` | 確認物件不是 `null` 。 如果物件為 `null`，判斷提示就會失敗。 |

您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，來指出預期會擲回的例外狀況類型。 如果未擲回指定的例外狀況，測試便會失敗。

在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。 您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。 同樣地，您想提供幾個開頭不是大寫字元的字串。 您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。

因為您的程式庫方法會處理字串，您也想要確保它能成功處理 [空字串 (`String.Empty`) ](xref:System.String.Empty)、沒有任何字元且其為0的有效字串 <xref:System.String.Length> ，以及 `null` 尚未初始化的字串。 您可以 `StartsWithUpper` 直接呼叫作為靜態方法，並傳遞單一 <xref:System.String> 引數。 或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫做為擴充方法 `string` `null` 。

您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素呼叫方法。 您將呼叫方法多載，讓您指定在測試失敗時所要顯示的錯誤訊息。 訊息會識別造成失敗的字串。

建立測試方法：

1. 開啟 *UnitTest1.cs* 檔案，並以下列程式碼取代程式碼：

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha (u + 0391) 和斯拉夫文大寫字母 EM (U + 041C) 。 方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha (u + 03B1) 和斯拉夫文小寫字母 Ghe (U + 0433) 。

1. 在功能表列上 **，選取 [**  >  **另存** 新檔]。 在對話方塊中，確定 [ **編碼** ] 設定為 [ **Unicode (utf-8)**。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio 另存新檔] 對話方塊":::

1. 當系統詢問您是否要取代現有的檔案時，請選取 [ **取代**]。

   如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。 當這種情況發生時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。

1. 開啟螢幕右側的 [單元測試] 面板。 從功能表選取 [ **View**  >  **測試**]。

1. 按一下 **固定** 圖示維持面板開啟。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Visual Studio for Mac [單元測試] 面板固定圖示":::

1. 按一下 [全部執行] 按鈕。

   所有測試皆通過。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio for Mac 預期的測試階段":::

## <a name="handle-test-failures"></a>處理測試失敗

如果您正在執行以測試為導向的開發 (TDD) ，您會先撰寫測試，並在您第一次執行時失敗。 然後，將程式碼新增至應用程式，讓測試成功。 在本教學課程中，您已在撰寫應用程式程式碼驗證之後建立測試，因此您未看到測試失敗。 若要在預期測試失敗時驗證測試失敗，請將不正確值加入測試輸入。

1. 修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。 您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. 再次執行測試。

   這次，[ **測試瀏覽器** ] 視窗會指出兩個測試成功，另一個則失敗。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="測試總管視窗，其中包含失敗的測試":::

1. <kbd>ctrl</kbd>-按一下失敗的測試， `TestDoesNotStartWithUpper` 然後從操作功能表中選取 [ **顯示結果板** ]。

   **結果** 填充會顯示 assert 產生的訊息：「IsFalse 失敗。 'Error' 的預期︰false；實際：True」。 因為失敗，所以在測試 "Error" 之後，陣列中沒有任何字串。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="顯示 IsFalse 判斷提示失敗的 Test Explorer 視窗":::

1. 移除您在步驟1中新增的字串 "Error"。 重新執行測試和測試階段。

## <a name="test-the-release-version-of-the-library"></a>測試程式庫的發行版本

現在，在執行程式庫的偵錯工具時，所有測試都已通過，請針對程式庫的發行組建執行額外的測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

測試發行組建︰

1. 在 Visual Studio 工具列中，將組建組態從 [偵錯] 變更為 [發行]。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="醒目提示 [發行] 組建的 Visual Studio 工具列":::

1. 在 **Solution** pad 中， <kbd>Ctrl +</kbd>按一下 **StringLibrary** 專案，然後從內容功能表中選取 [ **建立** ]，以重新編譯程式庫。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="StringLibrary 操作功能表和建置命令":::

1. 重新執行單元測試。

   所有測試皆通過。

## <a name="debug-tests"></a>偵錯測試

如果您使用 Visual Studio for Mac 作為 IDE，您可以使用教學課程：使用您的單元測試專案來進行程式碼 [的偵錯工具](debugging-with-visual-studio-mac.md) 中所示的相同程式：使用 Visual Studio for Mac 來對程式碼進行程式碼處理。 請不要啟動 *展示* 應用程式專案，而是在 **StringLibraryTests** 專案上按 <kbd>ctrl 鍵</kbd>，然後從操作功能表中選取 [**開始調試** 程式]。

Visual Studio 啟動已附加偵錯工具的測試專案。 執行將會在您已新增至測試專案或基礎程式庫程式碼的任何中斷點停止執行。

## <a name="additional-resources"></a>其他資源

* [.NET 中的單元測試](../testing/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已對類別庫進行單元測試。 您可以將程式庫以套件的形式發佈至 [NuGet](https://nuget.org) ，以將程式庫提供給其他人使用。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [建立及發行套件 (dotnet CLI)](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

如果您將程式庫發佈為 NuGet 套件，其他人可以安裝和使用它。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [在 Visual Studio for Mac 中安裝和使用套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

程式庫不需要以套件的形式散發。 它可以與使用它的主控台應用程式配套。 若要瞭解如何發佈主控台應用程式，請參閱本系列的先前教學課程：

> [!div class="nextstepaction"]
> [使用 Visual Studio for Mac 發佈 .NET 主控台應用程式](publishing-with-visual-studio-mac.md)
