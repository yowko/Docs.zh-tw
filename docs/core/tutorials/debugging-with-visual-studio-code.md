---
title: 使用 Visual Studio Code 來調試 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio Code 來偵測 .NET Core 主控台應用程式。
ms.date: 05/26/2020
ms.openlocfilehash: 82b2798397d702aa2a50c04bf6e4d569b97e3666
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241509"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="cc97f-103">教學課程：使用 Visual Studio Code 來對 .NET Core 主控台應用程式進行 Debug</span><span class="sxs-lookup"><span data-stu-id="cc97f-103">Tutorial: Debug a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="cc97f-104">本教學課程介紹使用 .NET Core 應用程式的 Visual Studio Code 中可用的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cc97f-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET Core apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc97f-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="cc97f-105">Prerequisites</span></span>

- <span data-ttu-id="cc97f-106">本教學課程適用于您在 Visual Studio Code 中建立[.Net Core 主控台應用程式](with-visual-studio-code.md)中建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc97f-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="cc97f-107">使用 Debug build configuration</span><span class="sxs-lookup"><span data-stu-id="cc97f-107">Use Debug build configuration</span></span>

<span data-ttu-id="cc97f-108">「*調試*程式」和「*發行*」是 .net Core 的組建設定中的兩個。</span><span class="sxs-lookup"><span data-stu-id="cc97f-108">*Debug* and *Release* are two of .NET Core's build configurations.</span></span> <span data-ttu-id="cc97f-109">您可以使用 Debug 組建設定進行偵錯工具，以及發行設定進行最終發行散發。</span><span class="sxs-lookup"><span data-stu-id="cc97f-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="cc97f-110">在 Debug 設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="cc97f-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="cc97f-111">最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。</span><span class="sxs-lookup"><span data-stu-id="cc97f-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="cc97f-112">程式的發行設定沒有符號的 debug 資訊，而且已完全優化。</span><span class="sxs-lookup"><span data-stu-id="cc97f-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="cc97f-113">根據預設，Visual Studio Code 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前加以變更。</span><span class="sxs-lookup"><span data-stu-id="cc97f-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="cc97f-114">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cc97f-114">Set a breakpoint</span></span>

<span data-ttu-id="cc97f-115">「中斷點」會在含有中斷點的行執行「之前」\*\*，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-115">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="cc97f-116">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="cc97f-116">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="cc97f-117">在 Visual Studio Code 中，開啟您在[建立 .Net Core 主控台應用程式](with-visual-studio-code.md)中建立的*HelloWorld*專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="cc97f-117">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="cc97f-118">開啟*Program.cs*檔案。</span><span class="sxs-lookup"><span data-stu-id="cc97f-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="cc97f-119">在程式碼視窗的左邊界中按一下，在顯示名稱、日期和時間的行上設定*中斷點*。</span><span class="sxs-lookup"><span data-stu-id="cc97f-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="cc97f-120">左邊界位於行號的左邊。</span><span class="sxs-lookup"><span data-stu-id="cc97f-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="cc97f-121">設定中斷點的另一種方式是將游標放在程式程式碼中，然後按<kbd>F9</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="cc97f-121">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing <kbd>F9</kbd>.</span></span>

   <span data-ttu-id="cc97f-122">如下圖所示，Visual Studio Code 會藉由在左邊界顯示一個紅點，來表示設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-122">As the following image shows, Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="中斷點集":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="cc97f-124">設定終端機輸入</span><span class="sxs-lookup"><span data-stu-id="cc97f-124">Set up for terminal input</span></span>

<span data-ttu-id="cc97f-125">中斷點位於 `Console.ReadLine` 方法呼叫之後。</span><span class="sxs-lookup"><span data-stu-id="cc97f-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="cc97f-126">**偵錯主控台**不接受執行中程式的終端機輸入。</span><span class="sxs-lookup"><span data-stu-id="cc97f-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="cc97f-127">若要在進行偵錯工具時處理終端機輸入，您可以使用整合式終端機（其中一個 Visual Studio Code 視窗）或外部終端機。</span><span class="sxs-lookup"><span data-stu-id="cc97f-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="cc97f-128">在本教學課程中，您會使用整合式終端機。</span><span class="sxs-lookup"><span data-stu-id="cc97f-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="cc97f-129">開啟 *. vscode/啟動 json*。</span><span class="sxs-lookup"><span data-stu-id="cc97f-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="cc97f-130">將 `console` 設定變更為 `integratedTerminal` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-130">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="cc97f-131">寄件者: </span><span class="sxs-lookup"><span data-stu-id="cc97f-131">From:</span></span>

   ```
   "console": "internalConsole",
   ```

   <span data-ttu-id="cc97f-132">變更為：</span><span class="sxs-lookup"><span data-stu-id="cc97f-132">To:</span></span>

   ```
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="cc97f-133">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="cc97f-133">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="cc97f-134">開始偵錯</span><span class="sxs-lookup"><span data-stu-id="cc97f-134">Start debugging</span></span>

1. <span data-ttu-id="cc97f-135">選取左側功能表上的 [偵錯工具] 圖示，以開啟 [Debug] 視圖。</span><span class="sxs-lookup"><span data-stu-id="cc97f-135">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="在 Visual Studio Code 中開啟 [偵錯] 索引標籤":::

1. <span data-ttu-id="cc97f-137">選取窗格頂端的綠色箭號（在 [ **.Net Core 啟動（主控台）**] 旁邊），開始進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cc97f-137">Start debugging by selecting the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span>  <span data-ttu-id="cc97f-138">另一個開始進行偵錯工具的方式是按<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-138">Another way to start debugging is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="開始偵錯":::

1. <span data-ttu-id="cc97f-140">選取 [**終端**機] 索引標籤，以查看「您的名稱是什麼？」</span><span class="sxs-lookup"><span data-stu-id="cc97f-140">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="cc97f-141">提示程式在等候回應之前顯示。</span><span class="sxs-lookup"><span data-stu-id="cc97f-141">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="選取 [終端機] 索引標籤":::

1. <span data-ttu-id="cc97f-143">在**終端**機視窗中輸入字串，以回應名稱的提示，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="cc97f-143">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="cc97f-144">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-144">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="cc97f-145">[**變數**] 視窗的 [**區域變數**] 區段會顯示目前正在執行的方法中所定義的變數值。</span><span class="sxs-lookup"><span data-stu-id="cc97f-145">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="命中中斷點，顯示區域變數":::

## <a name="change-variable-values"></a><span data-ttu-id="cc97f-147">變更變數值</span><span class="sxs-lookup"><span data-stu-id="cc97f-147">Change variable values</span></span>

<span data-ttu-id="cc97f-148">[**偵錯主控台**] 視窗可讓您與正在進行偵錯工具的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="cc97f-148">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="cc97f-149">您可以變更變數的值，以查看它對您的程式有何影響。</span><span class="sxs-lookup"><span data-stu-id="cc97f-149">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="cc97f-150">選取 [**偵錯主控台**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cc97f-150">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="cc97f-151">在 [ `name = "Gracie"` **偵錯主控台**] 視窗底部的提示中輸入，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="cc97f-151">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="變更變數值":::

1. <span data-ttu-id="cc97f-153">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`在 [**偵錯主控台**] 視窗底部輸入，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="cc97f-153">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="cc97f-154">[**變數**] 視窗會顯示和變數的新值 `name` `date` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-154">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="cc97f-155">選取工具列中的 [**繼續**] 按鈕，繼續執行程式。</span><span class="sxs-lookup"><span data-stu-id="cc97f-155">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="cc97f-156">另一個繼續的方式是按<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-156">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="繼續進行調試":::

1. <span data-ttu-id="cc97f-158">再次選取 [**終端**機] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cc97f-158">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="cc97f-159">主控台視窗中顯示的值會對應至您在**偵錯主控台**中進行的變更。</span><span class="sxs-lookup"><span data-stu-id="cc97f-159">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="顯示輸入值的終端機":::

1. <span data-ttu-id="cc97f-161">按任意鍵以結束應用程式，並停止進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cc97f-161">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="cc97f-162">設定條件式中斷點</span><span class="sxs-lookup"><span data-stu-id="cc97f-162">Set a conditional breakpoint</span></span>

<span data-ttu-id="cc97f-163">程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="cc97f-163">The program displays the string that the user enters.</span></span> <span data-ttu-id="cc97f-164">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="cc97f-164">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="cc97f-165">您可以使用稱為*條件式中斷點*的實用調試功能來測試此項。</span><span class="sxs-lookup"><span data-stu-id="cc97f-165">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="cc97f-166">在代表中斷點的紅點上按一下滑鼠右鍵（<kbd>Ctrl</kbd>+ 按一下 [macOS]）。</span><span class="sxs-lookup"><span data-stu-id="cc97f-166">Right-click (<kbd>Ctrl</kbd>+click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="cc97f-167">在內容功能表中，選取 [**編輯中斷點**] 以開啟對話方塊，讓您輸入條件運算式。</span><span class="sxs-lookup"><span data-stu-id="cc97f-167">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="[中斷點] 操作功能表":::

1. <span data-ttu-id="cc97f-169">`Expression`在下拉式選單中，輸入下列條件運算式，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="cc97f-169">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="輸入條件運算式":::

   <span data-ttu-id="cc97f-171">每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在這一行上中斷 `true` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-171">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="cc97f-172">除了條件運算式以外，您還可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行，或*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-172">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="cc97f-173">按<kbd>F5</kbd>鍵以進行偵錯工具啟動。</span><span class="sxs-lookup"><span data-stu-id="cc97f-173">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="cc97f-174">在 [**終端**機] 索引標籤中，當系統提示您輸入您的名稱時，按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="cc97f-174">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="cc97f-175">由於已滿足您指定的條件（ `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> ），因此程式會在到達中斷點且在方法執行之前停止執行 `Console.WriteLine` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-175">Because the condition you specified (`name` is `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="cc97f-176">[**變數**] 視窗會顯示變數的值 `name` 為 `""` 、或 <xref:System.String.Empty?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-176">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="cc97f-177">在**偵錯主控台**提示字元中輸入下列語句，然後按<kbd>enter</kbd>，以確認此值為空字串。</span><span class="sxs-lookup"><span data-stu-id="cc97f-177">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="cc97f-178">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="cc97f-178">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="在執行語句之後，偵錯主控台傳回 true 的值":::

1. <span data-ttu-id="cc97f-180">選取工具列上的 [繼續]\*\*\*\* 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-180">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="cc97f-181">選取 [**終端**機] 索引標籤，然後按任意鍵以結束程式並停止偵測。</span><span class="sxs-lookup"><span data-stu-id="cc97f-181">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="cc97f-182">按一下程式碼視窗左邊界中的點，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="cc97f-182">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="cc97f-183">清除中斷點的另一種方法是在選取程式程式碼時按<kbd>F9</kbd> 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-183">Another way to clear a breakpoint is by pressing <kbd>F9</kbd> while the line of code is selected.</span></span>

1. <span data-ttu-id="cc97f-184">如果您收到中斷點條件將遺失的警告，請選取 [**移除中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="cc97f-184">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="cc97f-185">逐步執行程式</span><span class="sxs-lookup"><span data-stu-id="cc97f-185">Step through a program</span></span>

<span data-ttu-id="cc97f-186">Visual Studio Code 也可讓您逐行執行程式並監視其執行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-186">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="cc97f-187">一般來說，您會設定中斷點，並在程式碼的一小部分追蹤程式流程。</span><span class="sxs-lookup"><span data-stu-id="cc97f-187">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="cc97f-188">因為此程式很小，所以您可以逐步執行整個程式。</span><span class="sxs-lookup"><span data-stu-id="cc97f-188">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="cc97f-189">在方法的左大括弧上設定中斷點 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-189">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="cc97f-190">按 <kbd>F5</kbd> 開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="cc97f-190">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="cc97f-191">Visual Studio Code 會反白顯示中斷點行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-191">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="cc97f-192">此時，[**變數**] 視窗 `args` 會顯示陣列是空的，而且 `name` 和 `date` 都有預設值。</span><span class="sxs-lookup"><span data-stu-id="cc97f-192">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="cc97f-193">選取 [**逐步執行**] 或按<kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-193">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="[逐步執行] 按鈕":::

   <span data-ttu-id="cc97f-195">Visual Studio Code 會反白顯示下一行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-195">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="cc97f-196">選取 [**逐步執行**] 或按<kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-196">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="cc97f-197">Visual Studio Code 會 `Console.WriteLine` 針對名稱提示執行，並反白顯示下一行執行。</span><span class="sxs-lookup"><span data-stu-id="cc97f-197">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="cc97f-198">下一行是的 `Console.ReadLine` `name` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-198">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="cc97f-199">[**變數**] 視窗不變，而且 [**終端**機] 索引標籤會顯示「您的名稱是什麼？」</span><span class="sxs-lookup"><span data-stu-id="cc97f-199">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="cc97f-200">及時.</span><span class="sxs-lookup"><span data-stu-id="cc97f-200">prompt.</span></span>

1. <span data-ttu-id="cc97f-201">選取 [**逐步執行**] 或按<kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-201">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="cc97f-202">Visual Studio 會反白顯示 `name` 變數指派。</span><span class="sxs-lookup"><span data-stu-id="cc97f-202">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="cc97f-203">[**變數**] 視窗 `name` 會顯示仍然是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-203">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="cc97f-204">在 [終端機] 索引標籤中輸入字串，然後按<kbd>enter</kbd>鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="cc97f-204">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="cc97f-205">當您輸入時，[**終端**機] 索引標籤可能不會顯示您輸入的字串，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法會抓取您的輸入。</span><span class="sxs-lookup"><span data-stu-id="cc97f-205">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="cc97f-206">選取 [**逐步執行**] 或按<kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-206">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="cc97f-207">Visual Studio Code 會反白顯示 `date` 變數指派。</span><span class="sxs-lookup"><span data-stu-id="cc97f-207">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="cc97f-208">[**變數**] 視窗會顯示呼叫方法時所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-208">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cc97f-209">[**終端**機] 索引標籤會顯示您在提示字元中輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="cc97f-209">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="cc97f-210">選取 [**逐步執行**] 或按<kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-210">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="cc97f-211">[**變數**] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="cc97f-211">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="cc97f-212">選取 [**逐步執行**] 或按<kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-212">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="cc97f-213">Visual Studio Code 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cc97f-213">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cc97f-214">主控台視窗會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="cc97f-214">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="cc97f-215">選取 [**跳出**] 或按<kbd>Shift</kbd> + <kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc97f-215">Select **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="跳出按鈕":::

1. <span data-ttu-id="cc97f-217">選取 [**終端**機] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cc97f-217">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="cc97f-218">終端機會顯示「按任意鍵結束 ...」</span><span class="sxs-lookup"><span data-stu-id="cc97f-218">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="cc97f-219">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="cc97f-219">Press any key to exit the program.</span></span>

## <a name="select-release-build-configuration"></a><span data-ttu-id="cc97f-220">選取發行組建設定</span><span class="sxs-lookup"><span data-stu-id="cc97f-220">Select Release build configuration</span></span>

<span data-ttu-id="cc97f-221">測試過應用程式的 Debug 版本之後，您也應該編譯和測試發行版本。</span><span class="sxs-lookup"><span data-stu-id="cc97f-221">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="cc97f-222">發行版本包含可能會影響應用程式行為的編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="cc97f-222">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="cc97f-223">例如，針對改善效能而設計的編譯器優化，可以在多執行緒應用程式中建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="cc97f-223">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="cc97f-224">若要建立並測試主控台應用程式的發行版本，請開啟**終端**機並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="cc97f-224">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="cc97f-225">其他資源</span><span class="sxs-lookup"><span data-stu-id="cc97f-225">Additional resources</span></span>

* [<span data-ttu-id="cc97f-226">在 Visual Studio Code 中偵錯</span><span class="sxs-lookup"><span data-stu-id="cc97f-226">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="cc97f-227">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cc97f-227">Next steps</span></span>

<span data-ttu-id="cc97f-228">在本教學課程中，您已使用 Visual Studio Code 調試工具。</span><span class="sxs-lookup"><span data-stu-id="cc97f-228">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="cc97f-229">在下一個教學課程中，您會發佈可部署的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="cc97f-229">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc97f-230">使用 Visual Studio Code 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cc97f-230">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
