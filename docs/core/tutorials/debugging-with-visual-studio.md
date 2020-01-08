---
title: 使用 Visual Studio 來進行 Hello World .NET Core 應用程式的 Debug
description: 瞭解如何在 Visual Studio 中C# ，對以或 Visual Basic 撰寫的 Hello World 應用程式進行 debug。
ms.date: 12/05/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 016b677639543c749a9940856f01b86e9a70859c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340102"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a><span data-ttu-id="e23d3-103">使用 Visual Studio C#來 Debug 或 Visual Basic .net Core Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="e23d3-103">Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio</span></span>

<span data-ttu-id="e23d3-104">到目前為止，您已遵循在[Visual Studio 2019 中建立您的第一個 .Net Core 主控台應用程式](with-visual-studio.md)中的步驟，來建立和執行簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e23d3-104">So far, you've followed the steps in [Create your first .NET Core console application in Visual Studio 2019](with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="e23d3-105">在您撰寫並編譯應用程式之後，便可以開始測試它。</span><span class="sxs-lookup"><span data-stu-id="e23d3-105">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="e23d3-106">Visual Studio 包含一組完整的偵錯工具，可讓您用來針對應用程式進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="e23d3-106">Visual Studio includes a comprehensive set of debugging tools that you can use to troubleshoot your application.</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="e23d3-107">Debug 組建設定</span><span class="sxs-lookup"><span data-stu-id="e23d3-107">Debug build configuration</span></span>

<span data-ttu-id="e23d3-108">[偵錯] 和 [發行] 是 Visual Studio 其中兩個預設的組建組態。</span><span class="sxs-lookup"><span data-stu-id="e23d3-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="e23d3-109">目前的組建組態會顯示在工具列上。</span><span class="sxs-lookup"><span data-stu-id="e23d3-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="e23d3-110">下列工具列影像顯示 Visual Studio 設定為編譯應用程式的 Debug 版本：</span><span class="sxs-lookup"><span data-stu-id="e23d3-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![已反白顯示 debug 的 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="e23d3-112">從執行應用程式的 Debug 版本開始。</span><span class="sxs-lookup"><span data-stu-id="e23d3-112">Begin by running the Debug version of your app.</span></span> <span data-ttu-id="e23d3-113">「偵錯工具」組建設定會關閉大部分的編譯器優化，並在建立程式期間提供更豐富的資訊。</span><span class="sxs-lookup"><span data-stu-id="e23d3-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="e23d3-114">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="e23d3-114">Set a breakpoint</span></span>

<span data-ttu-id="e23d3-115">執行您的程式並嘗試幾個偵錯工具功能：</span><span class="sxs-lookup"><span data-stu-id="e23d3-115">Run your program and try a few debugging features:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="e23d3-116">C#</span><span class="sxs-lookup"><span data-stu-id="e23d3-116">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e23d3-117">在程式碼視窗的左邊界按一下該行，在讀取 `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` 的那一行上設定*中斷點*。</span><span class="sxs-lookup"><span data-stu-id="e23d3-117">Set a *breakpoint* on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="e23d3-118">您也可以設定中斷點，方法是將插入號放在程式程式碼中，然後按**F9** ，或從功能表列選擇 [ **Debug** ] > [**切換中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="e23d3-118">You can also set a breakpoint by placing the caret in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="e23d3-119">中斷點會在執行中斷點的行*之前*，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-119">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="e23d3-120">如下圖所示，Visual Studio 會藉由反白顯示中斷點，並在左邊界顯示紅色圓圈，來指出其所在的行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-120">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="e23d3-122">在 [Debug] 模式中執行程式，方法是選取工具列上具有綠色箭號的 [ **HelloWorld** ] 按鈕，按**F5**，或選擇 [ **Debug** ] > **開始進行調試**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-122">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing **F5**, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="e23d3-123">當程式提示您輸入名稱時，在主控台視窗中輸入字串，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-123">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="e23d3-124">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-124">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="e23d3-125">[區域變數] 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-125">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio 中中斷點的螢幕擷取畫面](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="e23d3-127">[即時運算 **] 視窗可**讓您與正在調試的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="e23d3-127">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="e23d3-128">您可以互動方式變更變數的值，以查看它對您的程式有何影響。</span><span class="sxs-lookup"><span data-stu-id="e23d3-128">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="e23d3-129">如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug** > **Windows** > **Immediate**] 加以顯示。</span><span class="sxs-lookup"><span data-stu-id="e23d3-129">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="e23d3-130">**在 [即時**運算] 視窗中輸入 `name = "Gracie"`，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-130">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="e23d3-131">**在 [即時**運算] 視窗中輸入 `date = DateTime.Parse("11/16/2019 5:25 PM")`，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-131">Enter `date = DateTime.Parse("11/16/2019 5:25 PM")` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="e23d3-132">[即時**運算] 視窗**會顯示字串變數的值和 <xref:System.DateTime> 值的屬性。</span><span class="sxs-lookup"><span data-stu-id="e23d3-132">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="e23d3-133">此外，變數的值會在 [**區域變數**] 視窗中更新。</span><span class="sxs-lookup"><span data-stu-id="e23d3-133">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Visual Studio 2019 中的區域變數和即時運算視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="e23d3-135">選取工具列中的 [**繼續**] 按鈕，或選取 [ **Debug** **] > [繼續]** ，以繼續執行程式。</span><span class="sxs-lookup"><span data-stu-id="e23d3-135">Continue program execution by selecting the **Continue** button in the toolbar or by selecting **Debug** > **Continue**.</span></span> <span data-ttu-id="e23d3-136">主控台視窗中顯示的值會對應至**您在 [即時運算] 視窗**中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="e23d3-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![主控台視窗顯示輸入的值](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="e23d3-138">按任意鍵以結束應用程式，並停止進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e23d3-138">Press any key to exit the application and stop debugging.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="e23d3-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e23d3-139">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e23d3-140">在程式碼視窗的左邊界按一下該行，在讀取 `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` 的那一行上設定*中斷點*。</span><span class="sxs-lookup"><span data-stu-id="e23d3-140">Set a *breakpoint* on the line that reads `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="e23d3-141">您也可以設定中斷點，方法是將插入號放在想要的行上，然後從功能表列選擇 [ **Debug** ] > [**切換中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="e23d3-141">You can also set a breakpoint by placing the caret on the desired line and then choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="e23d3-142">中斷點會在執行中斷點的行*之前*，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-142">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>
   
   <span data-ttu-id="e23d3-143">如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-143">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. <span data-ttu-id="e23d3-145">在 [Debug] 模式中執行程式，方法是選取工具列上具有綠色箭號的 [ **HelloWorld** ] 按鈕，按**F5**，或選擇 [ **Debug** ] > **開始進行調試**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-145">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing **F5**, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="e23d3-146">當程式提示您輸入名稱，然後按**enter**鍵時，請在主控台視窗中輸入字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-146">Enter a string in the console window when the program prompts for a name and press **Enter**.</span></span>

1. <span data-ttu-id="e23d3-147">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-147">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="e23d3-148">[區域變數] 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-148">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

1. <span data-ttu-id="e23d3-149">[即時運算 **] 視窗可**讓您與正在調試的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="e23d3-149">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="e23d3-150">您可以互動方式變更變數的值，以查看它對您的程式有何影響。</span><span class="sxs-lookup"><span data-stu-id="e23d3-150">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="e23d3-151">如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug** > **Windows** > **Immediate**] 加以顯示。</span><span class="sxs-lookup"><span data-stu-id="e23d3-151">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="e23d3-152">**在 [即時**運算] 視窗中輸入 `name = "Gracie"`，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-152">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="e23d3-153">**在 [即時**運算] 視窗中輸入 `date = DateTime.Parse("11/16/2019 5:25 PM")`，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-153">Enter `date = DateTime.Parse("11/16/2019 5:25 PM")` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="e23d3-154">變數的值會在 [**區域變數**] 視窗中更新。</span><span class="sxs-lookup"><span data-stu-id="e23d3-154">The values of the variables are updated in the **Locals** window.</span></span>

1. <span data-ttu-id="e23d3-155">選取工具列中的 [繼續] 按鈕，或選取 [偵錯] >  [繼續] 功能表項目，以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-155">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="e23d3-156">主控台視窗中顯示的值會對應至**您在 [即時運算] 視窗**中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="e23d3-156">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![主控台視窗顯示輸入的值](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="e23d3-158">按任意鍵以結束應用程式，並停止進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e23d3-158">Press any key to exit the application and stop debugging.</span></span>

---

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="e23d3-159">設定條件式中斷點</span><span class="sxs-lookup"><span data-stu-id="e23d3-159">Set a conditional breakpoint</span></span>

<span data-ttu-id="e23d3-160">您的程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-160">Your program displays the string that the user enters.</span></span> <span data-ttu-id="e23d3-161">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="e23d3-161">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="e23d3-162">您可以使用稱為「*條件式中斷點*」的實用偵錯工具來測試此功能，以在符合一或多個條件時中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-162">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="e23d3-163">若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e23d3-163">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="e23d3-164">C#</span><span class="sxs-lookup"><span data-stu-id="e23d3-164">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e23d3-165">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-165">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="e23d3-166">在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e23d3-166">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="e23d3-167">勾選 [**條件**] 方塊（如果尚未選取）。</span><span class="sxs-lookup"><span data-stu-id="e23d3-167">Check the box for **Conditions** if it's not already selected.</span></span>

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="e23d3-169">針對**條件運算式**，將 "（例如 x = = 5"）取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="e23d3-169">For the **Conditional Expression**, replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="e23d3-170">您正在測試程式碼條件，`String.IsNullOrEmpty(name)` 方法呼叫 `true` 的原因可能是 `name` 尚未指派值，或其值為空字串（""）。</span><span class="sxs-lookup"><span data-stu-id="e23d3-170">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because `name` has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="e23d3-171">除了條件運算式之外，您也可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行; 或*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-171">Instead of a conditional expression, you can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="e23d3-172">選取 [**關閉**] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e23d3-172">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="e23d3-173">按**F5**鍵以進行偵錯工具啟動。</span><span class="sxs-lookup"><span data-stu-id="e23d3-173">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="e23d3-174">當系統提示您輸入名稱時，請在主控台視窗中按下**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-174">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="e23d3-175">因為已滿足您指定的條件，`name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>，所以程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前停止執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-175">Because the condition you specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="e23d3-176">選取 [**區域變數**] 視窗，其中會顯示目前執行之方法的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-176">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="e23d3-177">在此情況下，`Main` 是目前正在執行的方法。</span><span class="sxs-lookup"><span data-stu-id="e23d3-177">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="e23d3-178">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e23d3-178">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="e23d3-179">**在 [即時**運算] 視窗中輸入下列語句，然後按**enter**鍵，以確認此值為空字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-179">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="e23d3-180">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e23d3-180">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="e23d3-182">選取工具列上的 [繼續] 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-182">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="e23d3-183">按任意鍵以關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="e23d3-183">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="e23d3-184">按一下程式碼視窗左邊界中的點，或在選取程式程式碼時選擇 [ **Debug] > [切換中斷點**]，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="e23d3-184">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="e23d3-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e23d3-185">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e23d3-186">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-186">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="e23d3-187">在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e23d3-187">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="e23d3-188">核取 [條件] 的方塊。</span><span class="sxs-lookup"><span data-stu-id="e23d3-188">Check the box for **Conditions**.</span></span>

   ![顯示中斷點設定面板的編輯器 - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="e23d3-190">對於 [條件運算式]，請以下列內容取代 "e.g. x == 5"：</span><span class="sxs-lookup"><span data-stu-id="e23d3-190">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="e23d3-191">您正在測試程式碼條件，`String.IsNullOrEmpty(name)` 方法呼叫 `true` 的原因可能是 `name` 尚未指派值，或其值為空字串（""）。</span><span class="sxs-lookup"><span data-stu-id="e23d3-191">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because `name` has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="e23d3-192">除了條件運算式之外，您也可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行; 或*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-192">Instead of a conditional expression, you can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="e23d3-193">選取 [**關閉**] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e23d3-193">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="e23d3-194">按**F5**鍵以進行偵錯工具啟動。</span><span class="sxs-lookup"><span data-stu-id="e23d3-194">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="e23d3-195">當系統提示您輸入名稱時，請在主控台視窗中按下**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-195">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="e23d3-196">因為已滿足您指定的條件，`name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>，所以程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前停止執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-196">Because the condition you specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="e23d3-197">選取 [**區域變數**] 視窗，其中會顯示目前執行之方法的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-197">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="e23d3-198">在此情況下，`Main` 是目前正在執行的方法。</span><span class="sxs-lookup"><span data-stu-id="e23d3-198">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="e23d3-199">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e23d3-199">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="e23d3-200">**在 [即時**運算] 視窗中輸入下列語句，然後按**enter**鍵，以確認此值為空字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-200">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="e23d3-201">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e23d3-201">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. <span data-ttu-id="e23d3-203">選取工具列上的 [繼續] 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-203">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="e23d3-204">按任意鍵以關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="e23d3-204">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="e23d3-205">按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點] 功能表項目，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="e23d3-205">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>

---
## <a name="step-through-a-program"></a><span data-ttu-id="e23d3-206">逐步執行程式</span><span class="sxs-lookup"><span data-stu-id="e23d3-206">Step through a program</span></span>

<span data-ttu-id="e23d3-207">Visual Studio 也可讓您逐行執行程式並監視其執行情況。</span><span class="sxs-lookup"><span data-stu-id="e23d3-207">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="e23d3-208">通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。</span><span class="sxs-lookup"><span data-stu-id="e23d3-208">Ordinarily, you'd set a breakpoint and use this feature to follow program flow through a small part of your program code.</span></span> <span data-ttu-id="e23d3-209">因為您的程式很小，您可以逐步執行整個程式：</span><span class="sxs-lookup"><span data-stu-id="e23d3-209">Since your program is small, you can step through the entire program:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="e23d3-210">C#</span><span class="sxs-lookup"><span data-stu-id="e23d3-210">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e23d3-211">在功能表列上，選擇 [ **Debug** ] > [**逐步**執行]，或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-211">On the menu bar, choose **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-212">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="e23d3-212">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="e23d3-214">此時，[**區域變數**] 視窗會顯示您的程式已只定義一個變數，`args`。</span><span class="sxs-lookup"><span data-stu-id="e23d3-214">At this point, the **Locals** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="e23d3-215">由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="e23d3-215">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="e23d3-216">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="e23d3-216">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="e23d3-217">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-217">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-218">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-218">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="e23d3-219">如圖所示，在最後一個語句與這個語句之間執行程式碼所花費的時間不到一毫秒。</span><span class="sxs-lookup"><span data-stu-id="e23d3-219">As the image shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="e23d3-220">`args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。</span><span class="sxs-lookup"><span data-stu-id="e23d3-220">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. <span data-ttu-id="e23d3-222">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-222">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-223">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e23d3-223">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="e23d3-224">[**區域變數**] 視窗會顯示 `null`的 `name`，而主控台視窗會顯示「您的名稱是什麼？」字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-224">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="e23d3-225">在主控台視窗中輸入字串，然後按**enter**，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="e23d3-225">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="e23d3-226">主控台沒有回應，而且您輸入的字串不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍會捕捉您的輸入。</span><span class="sxs-lookup"><span data-stu-id="e23d3-226">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="e23d3-227">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-227">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-228">Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e23d3-228">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="e23d3-229">[**區域變數**] 視窗會顯示呼叫 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法時所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-229">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e23d3-230">主控台視窗也會顯示您在提示字元中輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-230">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="e23d3-231">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-231">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-232">[**區域變數**] 視窗會顯示從 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性指派之後，`date` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-232">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e23d3-233">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="e23d3-233">The console window is unchanged.</span></span>

1. <span data-ttu-id="e23d3-234">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-234">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-235">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="e23d3-235">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e23d3-236">主控台視窗會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-236">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="e23d3-237">選取 [ **Debug** > **跳出**] 或按**Shift**+**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-237">Select **Debug** > **Step Out** or press **Shift**+**F11**.</span></span> <span data-ttu-id="e23d3-238">這會停止逐步執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-238">This stops step-by-step execution.</span></span> <span data-ttu-id="e23d3-239">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-239">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="e23d3-240">按任意鍵以關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="e23d3-240">Press any key to close the console window and stop debugging.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="e23d3-241">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e23d3-241">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e23d3-242">在功能表列上，選擇 [ **Debug** ] > [**逐步**執行]，或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-242">On the menu bar, choose **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-243">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="e23d3-243">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="e23d3-245">此時，[**區域變數**] 視窗會顯示您的程式已只定義一個變數，`args`。</span><span class="sxs-lookup"><span data-stu-id="e23d3-245">At this point, the **Locals** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="e23d3-246">由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="e23d3-246">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="e23d3-247">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="e23d3-247">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="e23d3-248">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-248">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-249">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-249">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="e23d3-250">如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。</span><span class="sxs-lookup"><span data-stu-id="e23d3-250">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="e23d3-251">`args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。</span><span class="sxs-lookup"><span data-stu-id="e23d3-251">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="e23d3-253">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-253">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-254">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e23d3-254">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="e23d3-255">[**區域變數**] 視窗會顯示 `Nothing`的 `name`，而主控台視窗會顯示「您的名稱是什麼？」字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-255">The **Locals** window shows that `name` is `Nothing`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="e23d3-256">在主控台視窗中輸入字串，然後按**enter**，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="e23d3-256">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="e23d3-257">主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會擷取您的輸入。</span><span class="sxs-lookup"><span data-stu-id="e23d3-257">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="e23d3-258">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-258">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-259">Visual Studio 會醒目提示包含 `currentDate` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e23d3-259">Visual Studio highlights the statement that includes the `currentDate` variable assignment.</span></span> <span data-ttu-id="e23d3-260">[**區域變數**] 視窗會顯示呼叫 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法時所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e23d3-260">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e23d3-261">主控台視窗也會顯示在主控台提示輸入時輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-261">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="e23d3-262">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-262">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-263">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="e23d3-263">The console window is unchanged.</span></span>

1. <span data-ttu-id="e23d3-264">選取 [ **Debug** > **逐步**執行] 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-264">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="e23d3-265">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="e23d3-265">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e23d3-266">主控台視窗會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="e23d3-266">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="e23d3-267">選取 [ **Debug** > **跳出**] 或按**Shift**+**F11**。</span><span class="sxs-lookup"><span data-stu-id="e23d3-267">Select **Debug** > **Step Out** or press **Shift**+**F11**.</span></span> <span data-ttu-id="e23d3-268">這會停止逐步執行。</span><span class="sxs-lookup"><span data-stu-id="e23d3-268">This stops step-by-step execution.</span></span> <span data-ttu-id="e23d3-269">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="e23d3-269">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="e23d3-270">按任意鍵以關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="e23d3-270">Press any key to close the console window and stop debugging.</span></span>

---

## <a name="build-a-release-version"></a><span data-ttu-id="e23d3-271">建立發行版本</span><span class="sxs-lookup"><span data-stu-id="e23d3-271">Build a Release version</span></span>

<span data-ttu-id="e23d3-272">測試過應用程式的 Debug 版本之後，您也應該編譯和測試發行版本。</span><span class="sxs-lookup"><span data-stu-id="e23d3-272">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="e23d3-273">發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="e23d3-273">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="e23d3-274">例如，針對改善效能而設計的編譯器優化，可以在多執行緒應用程式中建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="e23d3-274">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="e23d3-275">若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="e23d3-275">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="e23d3-277">當您按下**F5**或從 [**建立**] 功能表選擇 [**建立方案**] 時，Visual Studio 會編譯應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="e23d3-277">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="e23d3-278">您可以像執行 Debug 錯版本一樣進行測試。</span><span class="sxs-lookup"><span data-stu-id="e23d3-278">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e23d3-279">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e23d3-279">Next steps</span></span>

<span data-ttu-id="e23d3-280">在您完成應用程式的調試之後，下一步就是發佈可部署的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="e23d3-280">Once you've debugged your application, the next step is to publish a deployable version of the app.</span></span> <span data-ttu-id="e23d3-281">如需如何執行此動作的詳細資訊，請參閱[使用 Visual Studio 發佈您的 .Net Core Hello World 應用程式](publishing-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e23d3-281">For information on how to do this, see [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>
