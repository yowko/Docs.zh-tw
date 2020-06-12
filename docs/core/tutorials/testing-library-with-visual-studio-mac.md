---
title: 使用 Visual Studio for Mac 測試具有 .NET Core 的 .NET Standard 類別庫
description: 建立 .NET Core 類別庫的單元測試專案。 確認 .NET Core 類別庫可在單元測試中正常運作。
ms.date: 06/08/2020
ms.openlocfilehash: a183049623df44cbb8c4abd47ce6e78d91adae12
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713606"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a>使用 Visual Studio 測試具有 .NET Core 的 .NET Standard 類別庫

本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。

## <a name="prerequisites"></a>Prerequisites

- 本教學課程適用于您在[Visual Studio for Mac 中建立 .NET Standard 程式庫](library-with-visual-studio-mac.md)中建立的解決方案。

## <a name="create-a-unit-test-project"></a>建立單元測試專案

單元測試能在開發與發佈期間提供自動化的軟體測試。 [MSTest](https://github.com/Microsoft/testfx-docs)是您可以從中選擇的三種測試架構之一。 其他則是[xUnit](https://xunit.net/)和[nUnit](https://nunit.org/)。

1. 啟動 Visual Studio for Mac。

1. 開啟 `ClassLibraryProjects` 您在[Visual Studio for Mac 中建立 .NET Standard 程式庫](library-with-visual-studio-mac.md)中建立的解決方案。

1. 在**solution** pad 中，以<kbd>ctrl</kbd>-按一下 `ClassLibraryProjects` 方案，然後**Add**選取 [  >  **新增專案**]。

1. 在 [**新增專案**] 對話方塊中，從 [ **Web] 和 [主控台**] 節點選取 [**測試**]。 選取**MSTest 專案**，後面接著 **[下一步]**。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Visual Studio Mac 新增專案] 對話方塊建立測試專案":::

1. 選取 [ **.Net Core 3.1**]。 將新專案命名為 "StringLibraryTest"，然後選取 [**建立**]。

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

若要讓測試專案與類別搭配使用 `StringLibrary` ，請加入專案的參考 `StringLibrary` 。

1. 在 [ **Solution** pad] 中，按<kbd>ctrl</kbd>-按一下 [ **StringLibraryTest**] 底下的 [**相關性]** 。 從內容功能表中選取 [**新增參考**]。

1. 在 [**參考**] 對話方塊中，選取 [ **StringLibrary** ] 專案。 選取 [確定]。

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac [編輯參考] 對話方塊":::

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

由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)、沒有任何字元的有效字串，以及 <xref:System.String.Length> 未初始化的 `null` 字串。 您可以 `StartsWithUpper` 直接呼叫做為靜態方法，並傳遞單一 <xref:System.String> 引數。 或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫作為擴充方法 `string` `null` 。

您將定義三個方法，每個方法都會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素呼叫方法。 您將呼叫方法多載，讓您指定要在測試失敗時顯示的錯誤訊息。 訊息會識別造成失敗的字串。

建立測試方法：

1. 開啟*UnitTest1.cs*檔案，並以下列程式碼取代程式碼：

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。 方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。

1. 在功能表列上 **，選取 [** 檔案] [  >  **另存**新檔]。 在對話方塊中，請確定 [**編碼**] 設定為 **[Unicode （utf-8）**]。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio 另存新檔] 對話方塊":::

1. 當系統詢問您是否要取代現有的檔案時，請選取 [**取代**]。

   如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。 發生這種情況時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。

1. 開啟螢幕右側的 [單元測試]**** 面板。 **View**  >  從功能表中選取 [View**測試**]。

1. 按一下**固定**圖示維持面板開啟。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Visual Studio for Mac [單元測試] 面板固定圖示":::

1. 按一下 [全部執行]**** 按鈕。

   所有測試皆通過。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio for Mac 預期的測試階段":::

## <a name="handle-test-failures"></a>處理測試失敗

如果您執行的是測試導向開發（TDD），您必須先撰寫測試，而且第一次執行時才會失敗。 接著，您可以將程式碼新增至應用程式，讓測試成功。 在本教學課程中，您已在撰寫應用程式驗證碼之後建立測試，因此您未看到測試失敗。 若要驗證測試在預期失敗時失敗，請在測試輸入中加入不正確值。

1. 修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。 您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. 再次執行測試。

   這次，[**測試瀏覽器**] 視窗會指出兩個測試成功，其中一個失敗。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="測試總管視窗，其中包含失敗的測試":::

1. 以<kbd>ctrl</kbd>-按一下失敗的測試， `TestDoesNotStartWithUpper` 然後從內容功能表中選取 [**顯示結果 Pad** ]。

   [**結果**] 面板會顯示判斷提示所產生的訊息：「IsFalse 失敗。 'Error' 的預期︰false；實際：True」。 由於失敗，因此在測試「錯誤」之後，陣列中沒有任何字串。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="顯示 IsFalse 判斷提示失敗的測試 Explorer 視窗":::

1. 移除您在步驟1中新增的字串 "Error"。 重新執行測試和測試階段。

## <a name="test-the-release-version-of-the-library"></a>測試程式庫的發行版本

現在，在執行程式庫的「偵錯工具」組建時，所有測試都已成功，請針對程式庫的發行組建，再次執行測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

測試發行組建︰

1. 在 Visual Studio 工具列中，將組建組態從 [偵錯]**** 變更為 [發行]****。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="醒目提示 [發行] 組建的 Visual Studio 工具列":::

1. 在**Solution** pad 中，以<kbd>ctrl</kbd>-按一下 [ **StringLibrary** ] 專案，然後從內容功能表中選取 [**組建**]，以重新編譯程式庫。

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="StringLibrary 操作功能表和建置命令":::

1. 再次執行單元測試。

   所有測試皆通過。

## <a name="debug-tests"></a>偵錯測試

您可以使用教學課程：使用 Visual Studio for Mac 來偵測[.Net Core 主控台應用程式](debugging-with-visual-studio-mac.md)中所示的相同進程，以使用您的單元測試專案來進行程式碼的 debug。 不要啟動展示應用程式專案，請以<kbd>ctrl</kbd>-按一下**StringLibraryTests**專案，然後從內容功能表中選取 [**開始調試專案**]。 Visual Studio 啟動已附加偵錯工具的測試專案。 執行會在您已加入測試專案或基礎程式庫程式碼的任何中斷點停止。

## <a name="additional-resources"></a>其他資源

* [.NET Core 與 .NET Standard 中的單元測試](../testing/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已對類別庫進行單元測試。 您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [建立及發行套件 (dotnet CLI)](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [在 Visual Studio for Mac 中安裝和使用套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

程式庫不一定要以封裝的形式散發。 它可以與使用它的主控台應用程式配套。 若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：

> [!div class="nextstepaction"]
> [使用 Visual Studio for Mac 發行 .NET Core 主控台應用程式](publishing-with-visual-studio-mac.md)
