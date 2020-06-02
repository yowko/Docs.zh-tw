---
title: 在 Visual Studio Code 中使用 .NET Core 測試 .NET Standard 類別庫
description: 建立 .NET Core 類別庫的單元測試專案。 確認 .NET Core 類別庫可在單元測試中正常運作。
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292186"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a>教學課程：在 Visual Studio Code 中使用 .NET Core 測試 .NET Standard 程式庫

本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。

## <a name="prerequisites"></a>Prerequisites

- 本教學課程適用于您在[Visual Studio Code 中建立 .NET Standard 程式庫](library-with-visual-studio-code.md)中建立的解決方案。

## <a name="create-a-unit-test-project"></a>建立單元測試專案

1. 開啟 Visual Studio Code。

1. 開啟 `ClassLibraryProjects` 您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。

1. 建立名為 "StringLibraryTest" 的單元測試專案。

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   專案範本會使用下列程式碼來建立 UnitTest1.cs 檔案：

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
   - 它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性來定義 `TestMethod1` 。

   執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。

   > [!NOTE]
   > MSTest 是您可以從中選擇的三種測試架構之一。 其他則是 xUnit 和 nUnit。

1. 將測試專案加入至方案。

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. 執行下列命令，以建立類別庫專案的專案參考：

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

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

由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)和和 `null` 字串。 空字串是沒有任何字元的，其 <xref:System.String.Length> 為0。 一個 `null` 字串尚未初始化。 您可以 `StartsWithUpper` 直接呼叫做為靜態方法，並傳遞單一 <xref:System.String> 引數。 或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫作為擴充方法 `string` `null` 。

您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素重複呼叫方法。 因為測試方法會在發現第一次失敗時失敗，所以您會呼叫方法多載，讓您傳遞一個字串來表示方法呼叫中所使用的字串值。

建立測試方法：

1. 開啟*StringLibraryTest/unittest1.cpp* ，並以下列程式碼取代所有程式碼。

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。 方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。

1. 儲存您的變更。

1. 執行測試：

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   終端機輸出顯示所有測試都已通過。

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a>處理測試失敗

如果您執行的是測試導向開發（TDD），您必須先撰寫測試，而且第一次執行時才會失敗。 接著，您可以將程式碼新增至應用程式，讓測試成功。 在此情況下，您在撰寫應用程式驗證碼之後就已建立測試，因此您未看到測試失敗。 若要驗證測試在預期失敗時失敗，請在測試輸入中加入不正確值。

1. 修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. 執行測試：

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   終端機輸出顯示一個測試失敗，並提供失敗測試的錯誤訊息。

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. 復原您在步驟 1 中所做的修改，並移除字串 "Error"。 重新執行測試和測試階段。

## <a name="test-the-release-version-of-the-library"></a>測試程式庫的發行版本

在執行程式庫的「偵錯工具」版本後，現在所有測試都已成功，請針對程式庫的發行組建，再次執行測試。 許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。

1. 使用發行組建設定執行測試：

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   所有測試皆通過。

## <a name="additional-resources"></a>其他資源

- [.NET Core 與 .NET Standard 中的單元測試](../testing/index.md)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已對類別庫進行單元測試。 您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [使用 dotnet CLI 建立及發佈套件](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。 若要深入瞭解，請遵循 NuGet 教學課程：

> [!div class="nextstepaction"]
> [利用 dotnet CLI 安裝並使用套件](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

程式庫不一定要以封裝的形式散發。 它可以與使用它的主控台應用程式配套。 若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 發行 .NET Core 主控台應用程式](publishing-with-visual-studio-code.md)
