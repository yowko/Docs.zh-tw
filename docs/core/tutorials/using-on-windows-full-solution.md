---
title: 使用 Visual Studio 2017 在 Windows 上建置完整的 .NET Core 解決方案
description: 了解如何在 Windows 上的 Visual Studio 2017 中建置完整的 .NET Core 方案。
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8e37eb578f9c4ac63fbc120e6227098ea69d169d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="65aab-103">使用 Visual Studio 2017 在 Windows 上建置完整的 .NET Core 解決方案</span><span class="sxs-lookup"><span data-stu-id="65aab-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="65aab-104">Visual Studio 2017 提供功能完整的開發環境來開發 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="65aab-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="65aab-105">本文件中的程序說明建置一般 .NET Core 解決方案所需的步驟，其中包含可重複使用的程式庫、測試，以及使用協力廠商程式庫。</span><span class="sxs-lookup"><span data-stu-id="65aab-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="65aab-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="65aab-106">Prerequisites</span></span>

<span data-ttu-id="65aab-107">請依照[我們的必要條件頁面](../windows-prerequisites.md)上的指示進行，更新您的環境。</span><span class="sxs-lookup"><span data-stu-id="65aab-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="65aab-108">只使用 .NET Core 專案的方案</span><span class="sxs-lookup"><span data-stu-id="65aab-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="65aab-109">撰寫程式庫</span><span class="sxs-lookup"><span data-stu-id="65aab-109">Writing the library</span></span>

1. <span data-ttu-id="65aab-110">在 Visual Studio 中，依序選擇 [檔案]、[新增]、[專案]。</span><span class="sxs-lookup"><span data-stu-id="65aab-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="65aab-111">在 [新增專案] 對話方塊中，展開 [Visual C#] 節點，然後依序選擇 [.NET Standard] 節點和 [類別庫 (.NET 標準)]。</span><span class="sxs-lookup"><span data-stu-id="65aab-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="65aab-112">將專案命名為 "Library"、方案命名為 "Golden"。</span><span class="sxs-lookup"><span data-stu-id="65aab-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="65aab-113">維持核取 [為方案建立目錄]。</span><span class="sxs-lookup"><span data-stu-id="65aab-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="65aab-114">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="65aab-114">Click **OK**.</span></span>

3. <span data-ttu-id="65aab-115">在 [方案總管] 中，開啟 [相依性] 節點的操作功能表，然後選擇 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="65aab-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="65aab-116">選擇 "nuget.org" 作為 [套件來源]，然後選擇 [瀏覽] 索引標籤。瀏覽 **Newtonsoft.Json**。</span><span class="sxs-lookup"><span data-stu-id="65aab-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="65aab-117">按一下 [安裝]，然後接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="65aab-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="65aab-118">套件現在應該會出現在 [相依性/NuGet] 下方且會自動還原。</span><span class="sxs-lookup"><span data-stu-id="65aab-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="65aab-119">將檔案 `Class1.cs` 重新命名為 `Thing.cs`。</span><span class="sxs-lookup"><span data-stu-id="65aab-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="65aab-120">接受類別的重新命名。</span><span class="sxs-lookup"><span data-stu-id="65aab-120">Accept the rename of the class.</span></span> <span data-ttu-id="65aab-121">新增方法：`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="65aab-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="65aab-122">在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="65aab-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="65aab-123">方案應該會建置而無錯誤。</span><span class="sxs-lookup"><span data-stu-id="65aab-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="65aab-124">撰寫測試專案</span><span class="sxs-lookup"><span data-stu-id="65aab-124">Writing the test project</span></span>

1. <span data-ttu-id="65aab-125">在 [方案總管] 中，開啟 [方案] 節點的操作功能表，然後依序選擇 [新增] 和 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="65aab-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="65aab-126">在 [新增專案] 對話方塊的 [Visual C# / .NET Core] 下方，選擇 [單元測試專案 (.NET Core)]。</span><span class="sxs-lookup"><span data-stu-id="65aab-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="65aab-127">將它命名為 "TestLibrary"，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="65aab-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="65aab-128">在 **TestLibrary** 專案中，開啟 [相依性] 節點的操作功能表，然後選擇 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="65aab-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="65aab-129">按一下 [專案]，接著檢查程式庫專案，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="65aab-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="65aab-130">這會從測試專案中新增對您程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="65aab-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="65aab-131">將 `UnitTest1.cs` 檔案重新命名為 `LibraryTests.cs` 並接受類別重新命名。</span><span class="sxs-lookup"><span data-stu-id="65aab-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="65aab-132">將 `using Library;` 新增至檔案頂端，並使用下列程式碼取代 `TestMethod1` 方法：</span><span class="sxs-lookup"><span data-stu-id="65aab-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="65aab-133">您現在應該能夠建置方案。</span><span class="sxs-lookup"><span data-stu-id="65aab-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="65aab-134">在 [測試] 功能表上，依序選擇 [Windows] 和 [測試總管]，以便進入工作區中的 [測試總管] 視窗。</span><span class="sxs-lookup"><span data-stu-id="65aab-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="65aab-135">幾秒鐘後，`ThingGetsObjectValFromNumber` 測試應該就會出現在 [測試總管] 中。</span><span class="sxs-lookup"><span data-stu-id="65aab-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="65aab-136">選擇 [ **全部執行**]。</span><span class="sxs-lookup"><span data-stu-id="65aab-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="65aab-137">測試應該會順利通過。</span><span class="sxs-lookup"><span data-stu-id="65aab-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="65aab-138">撰寫主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="65aab-138">Writing the console app</span></span>

1. <span data-ttu-id="65aab-139">在 [方案總管] 中，開啟方案的操作功能表，並新增一個新的 [主控台應用程式 (.NET Core)] 專案。</span><span class="sxs-lookup"><span data-stu-id="65aab-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="65aab-140">將它命名為「應用程式」。</span><span class="sxs-lookup"><span data-stu-id="65aab-140">Name it "App".</span></span>

2. <span data-ttu-id="65aab-141">在 [應用程式] 專案中，開啟 [相依性] 節點的操作功能表，然後依序選擇 [新增] 和 [參考]。</span><span class="sxs-lookup"><span data-stu-id="65aab-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="65aab-142">在 [參考管理員] 對話方塊中，分別核取 [專案] 下的 [程式庫]、[方案] 節點，然後再按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="65aab-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="65aab-143">開啟 **App** 節點的操作功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="65aab-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="65aab-144">這確保在按下 F5 或 CTRL+F5 時，將會啟動主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="65aab-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="65aab-145">開啟 `Program.cs` 檔案、將 `using Library;` 指示詞新增至檔案的頂端，然後將 `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` 新增至 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="65aab-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="65aab-146">在您剛才新增的行之後設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="65aab-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="65aab-147">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="65aab-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="65aab-148">應用程式應該會建置且不會發生錯誤，並且應該到達中斷點。</span><span class="sxs-lookup"><span data-stu-id="65aab-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="65aab-149">您也應該能夠確認應用程式輸出 "The answer is 42."。</span><span class="sxs-lookup"><span data-stu-id="65aab-149">You should also be able to check that the application output "The answer is 42.".</span></span>
