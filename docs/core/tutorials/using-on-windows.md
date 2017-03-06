---
title: "在 Windows 上開始使用 .NET Core"
description: "在 Windows 上開始使用 .NET Core, 使用 Visual Studio 2015"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 29019587d2d847c5184d07024fa763c8af805d50

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2015"></a>在 Windows 上開始使用 .NET Core, 使用 Visual Studio 2015

> [!WARNING]
> 此主題適用於 Visual Studio 2015 - .NET Core 工具 Preview 2。 .NET Core 工具 RC4 版本，請參閱[使用 Visual Studio 2017 在 Windows 上開始使用 .NET Core](../preview3/tutorials/using-on-windows-vs-2017.md) 主題。

Visual Studio 2015 提供功能完整的開發環境來開發 .NET Core 應用程式。 這份文件中的程序說明使用 Visual Studio 建立許多一般 .NET Core 方案，或包含 .NET Core 元件之方案的必要步驟。 案例包括測試以及使用未明確針對最新版本 .NET Core 建置的協力廠商程式庫。 

## <a name="prerequisites"></a>必要條件

請依照[我們的必要條件頁面](../windows-prerequisites.md)上的指示進行，更新您的環境。

## <a name="getting-started"></a>快速入門

下列步驟將設定 Visual Studio 2015 以進行 .NET Core 開發：

1. 開啟 Visual Studio 並在 [檔案] 功能表上，選擇 [新增]、[專案]。

2. 在 [新增專案] 對話方塊的 [範本] 清單中，展開 [Visual C#] 節點，然後選擇 [.NET Core]。 您應該會看到三個新專案範本，分別是針對**類別庫 (.NET Core)**、**主控台應用程式 (.NET Core)**，和 **ASP.NET Core Web 應用程式 (.NET Core)**。

<a name="a-solution-using-only-net-core-projects"></a>只使用 .NET Core 專案的方案
----------------------------------------

### <a name="writing-the-library"></a>撰寫程式庫

1. 在 Visual Studio 中，依序選擇 [檔案]、[新增]、[專案]。 在 [新增專案] 對話方塊中，展開 [Visual C#] 節點，然後依序選擇 [.NET Core] 節點、[類別庫 (.NET Core)]。 

2. 將專案命名為 "Library"、方案命名為 "Golden"。 維持核取 [為方案建立目錄]。 按一下 [確定]。

3. 在方案總管中，開啟 [參考] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。

4. 選擇 "nuget.org" 作為 [套件來源]，然後選擇 [瀏覽] 索引標籤。 瀏覽 **Newtonsoft.Json**。 按一下 [安裝]。 

5. 開啟 [參考] 節點的操作功能表，然後選擇 [還原套件]。

6. 將檔案 `Class1.cs` 重新命名為 `Thing.cs`。 接受類別的重新命名。 移除建構函式，並新增一個方法︰`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

   方案應該會建置而無錯誤。

### <a name="writing-the-test-project"></a>撰寫測試專案

1. 在方案總管中，開啟 [方案] 節點的操作功能表，然後依序選擇 [新增]、[新增方案資料夾]。 將資料夾命名為 "test"。 
   這只是方案資料夾，不是實體資料夾。

2. 開啟 **test** 資料夾的操作功能表，並選擇 [新增]。 [新增專案]。 在 [新增專案] 對話方塊中，選擇 [主控台應用程式 (.NET Core)]。 將它命名為 "TestLibrary"，並明確放在 `Golden\test` 路徑下方。 

> [!IMPORTANT]
> 專案必須是主控台應用程式，而不是類別庫。

3. 在 **TestLibrary** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [新增參考]。 

4. 在 [參考管理員] 對話方塊中，分別核取 [專案] 下的 [程式庫]、[方案] 節點，然後再按一下 [確定]。 

5. 在 **TestLibrary** 專案中，開啟 `project.json` 檔案，並將 `"Library": "1.0.0-*"` 取代為 `"Library": {"target": "project", "version": "1.0.0-*"}`。 

   這是為了避免將 `Library` 專案解析為同名的 NuGet 套件。 將目標明確設為「專案」時，可確保工具會先搜尋具有該名稱的專案，而不是套件。 
   
6. 在 **TestLibrary** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [還原套件]。

7. 開啟 [參考] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。

8. 選擇 "nuget.org" 作為 [套件來源]，然後選擇 [瀏覽] 索引標籤。 核取 [包括發行前版本] 核取方塊，然後瀏覽 **xUnit** 2.2.0 版本或更新版本，然後按一下 [安裝]。 

9. 瀏覽 **dotnet-test-xunit** 2.2.0 版本或更新版本，然後按一下 [安裝]。

10. 編輯 `project.json` 並將 `"imports": "dnxcore50"` 取代為 `"imports": [ "dnxcore50", "portable-net45+win8" ]`。 

   這樣可正確地還原 xunit 程式庫並讓專案正確地使用︰這些程式庫來編譯成搭配可移植式設定檔使用，這些設定檔包含 "portable-net45+win8"，但不包含 .NET Core，因為在建置時 .NET Core 並不存在。 `import` 會在建置階段放寬工具版本檢查。 您現在可以還原套件而不會發生錯誤。

11. 編輯 `project.json`，以在 `"frameworks"` 區段之後新增 `"testRunner": "xunit",`。

12. 將 `LibraryTests.cs` 類別檔案新增至 **TestLibrary** 專案中，並在檔案頂端新增 `using` 指示詞 `using Xunit;` 和 `using Library;`，然後將下列程式碼新增至類別：
    ```csharp
    [Fact]
    public void ThingGetsObjectValFromNumber() {
        Assert.Equal(42, new Thing().Get(42));
    }
    ```
    * 選擇性地從 **TestLibrary** 專案中刪除 `Program.cs` 檔案，然後從 `project.json` 移除 `"buildOptions": {"emitEntryPoint": true},`。

   您現在應該能夠建置方案。 
   
13. 在 [測試] 功能表上，選擇 [Windows]、[測試總管]，然後在 [測試總管] 中選擇 [全部執行]。
   
   測試應該會順利通過。

### <a name="writing-the-console-app"></a>撰寫主控台應用程式

1. 在方案總管中，開啟 `src` 資料夾的操作功能表，並新增一個新的 [主控台應用程式 (.NET Core)] 專案。 將它命名為 "App"，並將位置設為 `Golden\src`。

2. 在 **App** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [新增參考]。 

3. 在 [參考管理員] 對話方塊中，分別核取 [專案] 下的 [程式庫]、[方案] 節點，然後再按一下 [確定]。

4. 在 **App** 專案中，開啟 `project.json` 檔案，並將 `"Library": "1.0.0-*"` 取代為 `"Library": {"target": "project"}`。

5. 開啟 [參考] 節點的操作功能表，然後選擇 [還原套件]。

6. 開啟 **App** 節點的操作功能表，然後選擇 [設定為啟始專案]。

7. 開啟 `Program.cs` 檔案、將 `using Library;` 指示詞新增至檔案的頂端，然後將 `Console.WriteLine($"The answer is {new Thing().Get(42)}");` 新增至 `Main` 方法。

8. 在您剛才新增的行之後設定中斷點。

9. 按 F5 執行應用程式。

   應用程式應該會建置且不會發生錯誤，並且應該到達中斷點。 您也應該能夠確認應用程式輸出 "The answer is 42."。

<a name="a-mixed-net-core-library-and-net-framework-application"></a>混合的 .NET Core 程式庫和 .NET Framework 應用程式
--------------------------------------------------------

從先前指令碼取得的方案開始，執行下列步驟︰

1. 在方案總管中，開啟 **Library** 專案的 `project.json` 檔，並將 `"frameworks": {
    "netstandard1.6" }` 取代為 `"frameworks": {
    "netstandard1.4" }`。

2. 在 **Library** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [還原套件]。

   方案應該仍會建置，且功能和以前完全相同︰測試應該會順利通過，主控台應用程式應該執行且可以偵錯。

3. 在 **Library** 專案中，開啟操作功能表，然後選擇 [建置]。

4. 在方案總管中，開啟 `src` 資料夾的操作功能表，然後選擇 [新增]。 [新增專案]。

5. 在 [新增專案] 對話方塊中，依序選擇 [Visual C#] 節點和 [主控台應用程式]。

> [!IMPORTANT]
> 請確定您選擇標準的主控台應用程式，而不是 .NET Core 版本。 本節中，您將使用 .NET Framework 應用程式的程式庫。

6. 將專案命名為 "FxApp"，並將位置設定為 `Golden\src`。

7. 在 **FxApp** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [新增參考]。

8. 在 [參考管理員] 對話方塊中，選擇 [瀏覽] 並瀏覽到內建 `Library.dll` 的位置 (在 ..Golden\src\Library\bin\Debug\netstandard1.4 路徑下)，然後按一下 [新增]。 

   您也可以封裝程式庫並參考套件，這是從 .NET Framework 參考 .NET Core 程式碼的另一種方式。

9. 開啟 [參考] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。

10. 選擇 "nuget.org" 作為 [套件來源]，然後選擇 [瀏覽] 索引標籤。 核取 [包括發行前版本] 核取方塊，然後瀏覽 **Newtonsoft.Json**。 按一下 [安裝]。 

11. 在 **FxApp** 專案中，開啟 `Program.cs` 檔案，並將 `using Library;` 指示詞新增至檔案的頂端，將 `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` 新增至程式的 `Main` 方法。

12. 在您剛才新增的行之後設定中斷點。

13. 使 **FxApp** 成為方案的啟動應用程式。

14. 按下 F5 即可執行應用程式。

   應用程式應該會建置，並到達中斷點。 應用程式的輸出應該是 "The answer is 42."。
   
   > [!TIP]
   > 在 Windows 平台上，您可以使用 MSTest。 如需詳細資訊，請參閱[在 Windows 文件上使用 MSTest](../testing/using-mstest-on-windows.md)。

<a name="moving-a-library-from-netstandard-14-to-13"></a>將程式庫從 netstandard 1.4 移至 1.3
--------------------------------------------

1. 在方案總管中，開啟 **Library** 專案的 `project.json` 檔。

2. 將 `frameworks": { "netstandard1.4" }` 取代為 `frameworks": { "netstandard1.3" }`。

3. 在 **Library** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [還原套件]。

4. 在 [建置] 功能表上，選擇 [建置程式庫]。

5. 從 **FxApp** 移除 `Library` 參考，然後使用 ...Golden\src\Library\bin\Debug\netstandard1.3 路徑將它新增回去。 這現在會參考 1.3 版。

6. 按 F5 執行應用程式。

   一切都應該如以前一樣運作。 檢查應用程式的輸出是 "The answer is 42."、已到達中斷點，且可以檢查變數。

<a name="a-mixed-pcl-library-and-net-framework-application"></a>混合的 PCL 程式庫和 .NET Framework 應用程式
--------------------------------------------------

如果先前的方案已開啟，請將它關閉︰您會從本節起開啟新的指令碼。

### <a name="writing-the-library"></a>撰寫程式庫

1. 在 Visual Studio 中，依序選擇 [檔案]、[新增]、[專案]。 在 [新增專案] 對話方塊中，展開 [Visual C#] 節點，然後選擇 [類別庫 (可移植到 iOS、Android 及 Windows)]。 

2. 將專案命名為 "PCLLibrary"、方案命名為 "GoldenPCL"。 維持核取 [為方案建立目錄]。 按一下 [確定]。

3. 在方案總管中，開啟 [參考] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。

4. 選擇 "nuget.org" 作為 [套件來源]，然後選擇 [瀏覽] 索引標籤。 核取 [包括發行前版本] 核取方塊，然後瀏覽 **Newtonsoft.Json**。 按一下 [安裝] 。 

5. 將類別重新命名為 "Thing" 並新增一個方法：`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

6. 在 [建置] 功能表上，選擇 [建置方案]，並確認方案可順利建置。

### <a name="writing-the-console-app"></a>撰寫主控台應用程式

1. 在方案總管中，開啟 [方案 'GoldenPCL'] 節點的操作功能表，然後選擇 [新增]。 **新增專案**。 在 [新增專案] 對話方塊中，展開 [Visual C#] 節點、選擇 [主控台應用程式]，然後將專案命名為 "App"。 

2. 在 **App** 專案中，開啟 [參考] 節點的操作功能表，然後選擇 [新增參考]。 

3. 在 [參考管理員] 對話方塊中，選擇 [瀏覽] 並瀏覽到內建 `PCLLibrary.dll` 的位置 (在 ..\GoldenPCL\PCLLibrary\bin\Debug 路徑下)，然後按一下 [新增]。 

4. 在 **App** 專案中，開啟 `Program.cs` 檔案，並將 `using PCLLibrary;` 指示詞新增至檔案的頂端，將 `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` 新增至程式的 `Main` 方法。

5. 在您剛才新增的行之後設定中斷點。

6. 在方案總管中，開啟 **App** 節點的操作功能表，然後選擇 [設定為啟始專案]。

7. 按下 F5 即可執行應用程式。

   應用程式應該順利建置、執行並在輸出 "The answer is 42." 之後到達中斷點。

<a name="moving-a-pcl-to-a-netstandard-library"></a>將 PCL 移至 NetStandard 程式庫
-------------------------------------
可攜式類別庫工具可以自動修改您的 PCL，以 .NET 標準為目標。 

1.    按兩下 [屬性] 節點，開啟專案屬性頁面

2.    在 [目標] 標題下，按一下超連結 [以 .NET 平台標準為目標]

3.    要求確認時按一下 [是]

這項工具會自動選取 .NET 標準的版本，其中包含所有您 PCL 最初設為目標的所有目標。 您可以在專案屬性頁中，使用 .NET 標準下拉式清單，將不同版本的 .NET 標準設為目標。
 
* 如果您先前已有 packages.config，可能會提示您解除安裝任何已安裝的套件，才能進行轉換。

### <a name="manually-edit-projectjson-to-target-net-standard-from-an-existing-portable-class-library"></a>手動編輯 project.json，以來自現有可攜式類別庫的 .NET 標準為目標

1.    如果您的 project.json 在 “supports” 元素中包含 “dnxcore50”，請移除它。

2.    移除對 “Microsoft.NETCore” 的相依性

3.    將對 “Microsoft.NETCore.Portable.Compatibility” “1.0.0” 版的相依性改為 “1.0.1” 版

4.    新增對 “NETStandard.Library” “1.6.0” 版的相依性

5.    從 “frameworks” 元素，移除 “dotnet” 架構 (及其內的 “imports” 元素)

6.    將 ` "netstandard1.x” : { } ` 新增至 frameworks 元素，其中 x 取代為您要設為目標的 .NET 標準版本

### <a name="example-projectjson"></a>範例 project.json

此 project.json 包含 UWP 以及 .NET 4.6 的 supports 子句，並以 netstandard1.3 為目標︰
```
{
  "supports": {
    "net46.app": {},
    "uwp.10.0.app": {},
  },
  "dependencies": {
    "NETStandard.Library": "1.6.0",
    "Microsoft.NETCore.Portable.Compatibility": "1.0.1"
  },
  "frameworks": {
    "netstandard1.3" : {}
  }
}
```





<!--HONumber=Feb17_HO2-->


