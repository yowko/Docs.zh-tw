---
title: "使用 MSTest 和 Windows 的 .NET Core"
description: "搭配 Visual Studio 2015 時，如何使用 MSTest 和 Windows 的 .NET Core"
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 94304cd742b63e77126bfa40651faa6974e58853
ms.lasthandoff: 03/03/2017

---

# <a name="unit-testing-with-mstest-and-net-core-on-windows-using-visual-studio-2015"></a>搭配 Visual Studio 2015 時，使用 Windows 的 .NET Core 和 MSTest 的單元測試

以多個平台為目標時，xUnit 可能是較好的選擇，但您也可以搭配使用 Windows 的 .NET Core 和 MSTest。

## <a name="prerequisites"></a>必要條件

按照[開始使用 Windows 的 .NET Core](../tutorials/using-on-windows.md) 中的指示，以建立程式庫專案。

### <a name="writing-the-test-project-using-mstest"></a>使用 MSTest 撰寫測試專案

1. 在方案總管中，開啟 [方案] 節點的操作功能表，然後依序選擇 [新增]、[新增方案資料夾]。 將資料夾命名為 "test"。 
   這只是方案資料夾，不是實體資料夾。

2. 開啟 **test** 資料夾的操作功能表，並選擇 [新增]。 [新增專案]。 在 [新增專案] 對話方塊中，選擇 [主控台應用程式 (.NET Core)]。 將它命名為 "TestLibrary"，並明確放在 `Golden\test` 路徑下方。 

   > [!IMPORTANT]
   > 專案必須是主控台應用程式，而不是類別庫。

3. 在 **TestLibrary** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [新增參考]。 

4. 在 [參考管理員] 對話方塊中，分別核取 [專案] 下的 [程式庫]、[方案] 節點，然後再按一下 [確定]。 

5. 在 **TestLibrary** 專案中，開啟 `project.json` 檔案，並將 `"Library": "1.0.0-*"` 取代為 `"Library": {"target": "project"}`。 

   這是為了避免將 `Library` 專案解析為同名的 NuGet 套件。 將目標明確設為「專案」時，可確保工具會先搜尋具有該名稱的專案，而不是套件。 

6. 開啟 [參考] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。

7. 選擇 "nuget.org" 做為 [套件來源]，然後選擇 [瀏覽] 索引標籤。 核取 [包括發行前版本] 核取方塊，然後瀏覽 **MSTest.TestFramework** 1.0.1 預覽版本或更新版本，然後按一下 [安裝]。 

8. 瀏覽 **dotnet-test-mstest** 1.1.1 預覽版本或更新版本，然後按一下 [安裝]。

9. 編輯 `project.json`，以在 `"version"` 區段之後新增 `"testRunner": "mstest",`。

10. 將 `LibraryTests.cs` 類別檔案新增至 **TestLibrary** 專案中，並在檔案頂端新增 `using` 指示詞 `Microsoft.VisualStudio.TestTools.UnitTesting;` 和 `using Library;`，然後將下列程式碼新增至類別：
    ```csharp
    [TestClass]
    public class LibraryTests
    {
        [TestMethod]
        public void ThingGetsObjectValFromNumber()
        {
            Assert.AreEqual(42, new Thing().Get(42));
        }
    }
    ```
    * 選擇性地從 **TestLibrary** 專案中刪除 `Program.cs` 檔案，然後從 `project.json` 移除 `"buildOptions": {"emitEntryPoint": true},`。

   您現在應該能夠建置方案。 
   
11. 在 [測試] 功能表上，選擇 [Windows]、[測試總管]，然後在 [測試總管] 中選擇 [全部執行]。
   
   測試應該會順利通過。

