---
title: 使用 Visual Studio 2017 在 Windows 上建置完整的 .NET Core 解決方案
description: 了解如何在 Windows 上的 Visual Studio 2017 中建置完整的 .NET Core 方案。
author: bleroy
ms.date: 11/16/2016
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0130ae10cc3bac445892faf0f9a18cf2f23dc036
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170518"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>使用 Visual Studio 2017 在 Windows 上建置完整的 .NET Core 解決方案

Visual Studio 2017 提供功能完整的開發環境來開發 .NET Core 應用程式。 本文件中的程序說明建置一般 .NET Core 解決方案所需的步驟，其中包含可重複使用的程式庫、測試，以及使用協力廠商程式庫。 

## <a name="prerequisites"></a>必要條件

請依照[我們的必要條件頁面](../windows-prerequisites.md)上的指示進行，更新您的環境。

## <a name="a-solution-using-only-net-core-projects"></a>只使用 .NET Core 專案的方案

### <a name="writing-the-library"></a>撰寫程式庫

1. 在 Visual Studio 中，依序選擇 [檔案]、[新增]、[專案]。 在 [新增專案] 對話方塊中，展開 [Visual C#] 節點，然後依序選擇 [.NET Standard] 節點和 [類別庫 (.NET Standard)]。 這樣會建立 .NET Standard 程式庫，它會以 .NET Core 和支援 [.NET Standard](../../standard/net-standard.md) 2.0 版的任何其他 .NET 實作為目標。

2. 將專案命名為 "Library"、方案命名為 "Golden"。 維持核取 [為方案建立目錄]。 按一下 [確定 **Deploying Office Solutions**]。

3. 在 [方案總管] 中，開啟 [相依性] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。

4. 選擇 "nuget.org" 作為 [套件來源]，然後選擇 [瀏覽] 索引標籤。瀏覽 **Newtonsoft.Json**。 按一下 [安裝]，然後接受授權合約。 套件現在應該會出現在 [相依性/NuGet] 下方且會自動還原。

5. 將檔案 `Class1.cs` 重新命名為 `Thing.cs`。 接受類別的重新命名。 新增方法：`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

   方案應該會建置而無錯誤。

### <a name="writing-the-test-project"></a>撰寫測試專案

1. 在 [方案總管] 中，開啟 [方案] 節點的操作功能表，然後依序選擇 [新增] 和 [新增專案]。 在 [新增專案] 對話方塊的 [Visual C# / .NET Core] 下方，選擇 [單元測試專案 (.NET Core)]。 將它命名為 "TestLibrary"，然後按一下 [確定]。 

2. 在 **TestLibrary** 專案中，開啟 [相依性] 節點的操作功能表，然後選擇 [新增參考]。 按一下 [專案]，接著檢查程式庫專案，然後按一下 [確定]。 這會從測試專案中新增對您程式庫的參考。

3. 將 `UnitTest1.cs` 檔案重新命名為 `LibraryTests.cs` 並接受類別重新命名。 將 `using Library;` 新增至檔案頂端，並使用下列程式碼取代 `TestMethod1` 方法：
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   您現在應該能夠建置方案。 
   
4. 在 [測試] 功能表上，依序選擇 [Windows] 和 [測試總管]，以便進入工作區中的 [測試總管] 視窗。 幾秒鐘後，`ThingGetsObjectValFromNumber` 測試應該就會出現在 [測試總管] 中。 選擇 [ **全部執行**]。
   
   測試應該會順利通過。

### <a name="writing-the-console-app"></a>撰寫主控台應用程式

1. 在 [方案總管] 中，開啟方案的操作功能表，並新增一個新的 [主控台應用程式 (.NET Core)] 專案。 將它命名為「應用程式」。

2. 在 [應用程式] 專案中，開啟 [相依性] 節點的操作功能表，然後依序選擇 [新增] 和 [參考]。 

3. 在 [參考管理員] 對話方塊中，分別核取 [專案] 下的 [程式庫]、[方案] 節點，然後再按一下 [確定]。

6. 開啟 **App** 節點的操作功能表，然後選擇 [設定為啟始專案]。 這確保在按下 F5 或 CTRL+F5 時，將會啟動主控台應用程式。

7. 開啟 `Program.cs` 檔案、將 `using Library;` 指示詞新增至檔案的頂端，然後將 `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` 新增至 `Main` 方法。

8. 在您剛才新增的行之後設定中斷點。

9. 按 F5 執行應用程式。

   應用程式應該會建置且不會發生錯誤，並且應該到達中斷點。 您也應該能夠確認應用程式輸出 "The answer is 42."。
