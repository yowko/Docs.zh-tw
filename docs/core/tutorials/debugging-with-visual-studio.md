---
title: 使用 Visual Studio 來對 .NET Core 主控台應用程式進行偵錯工具
description: 瞭解如何使用 Visual Studio 來進行 .NET Core 主控台應用程式的偵錯工具。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4e408d5bd0976d88f368615860ac373142d0fe1e
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957221"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="45ce2-103">教學課程：使用 Visual Studio 對 .NET Core 主控台應用程式進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="45ce2-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="45ce2-104">本教學課程介紹 Visual Studio 中提供的調試工具。</span><span class="sxs-lookup"><span data-stu-id="45ce2-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45ce2-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="45ce2-105">Prerequisites</span></span>

- <span data-ttu-id="45ce2-106">本教學課程適用于您 [使用 Visual Studio 建立 .Net Core 主控台應用程式](with-visual-studio.md)中所建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="45ce2-106">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="45ce2-107">使用 Debug build configuration</span><span class="sxs-lookup"><span data-stu-id="45ce2-107">Use Debug build configuration</span></span>

<span data-ttu-id="45ce2-108">*Debug* 和 *Release* 是 Visual Studio 的內建組建設定。</span><span class="sxs-lookup"><span data-stu-id="45ce2-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="45ce2-109">您可以使用 Debug 組建設定進行偵錯工具，並使用發行設定來進行最終發行散發。</span><span class="sxs-lookup"><span data-stu-id="45ce2-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="45ce2-110">在「偵錯工具」設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="45ce2-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="45ce2-111">最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。</span><span class="sxs-lookup"><span data-stu-id="45ce2-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="45ce2-112">程式的發行設定沒有符號的 debug 資訊，而且已完全優化。</span><span class="sxs-lookup"><span data-stu-id="45ce2-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="45ce2-113">根據預設，Visual Studio 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前進行變更。</span><span class="sxs-lookup"><span data-stu-id="45ce2-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="45ce2-114">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="45ce2-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="45ce2-115">開啟您在 [使用 Visual Studio 建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的專案。</span><span class="sxs-lookup"><span data-stu-id="45ce2-115">Open the project that you created in [Create a .NET Core console application using Visual Studio](with-visual-studio.md).</span></span>

   <span data-ttu-id="45ce2-116">目前的組建組態會顯示在工具列上。</span><span class="sxs-lookup"><span data-stu-id="45ce2-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="45ce2-117">下列工具列影像顯示 Visual Studio 設定為編譯應用程式的偵錯工具版本：</span><span class="sxs-lookup"><span data-stu-id="45ce2-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   ![醒目提示反白顯示的 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a><span data-ttu-id="45ce2-119">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="45ce2-119">Set a breakpoint</span></span>

<span data-ttu-id="45ce2-120">「中斷點」\*\* 會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="45ce2-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="45ce2-121">在顯示名稱、日期和時間的行上設定 *中斷點* ，方法是按一下該行程式碼視窗的左邊界。</span><span class="sxs-lookup"><span data-stu-id="45ce2-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="45ce2-122">左邊界是行號的左邊。</span><span class="sxs-lookup"><span data-stu-id="45ce2-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="45ce2-123">設定中斷點的其他方式是將游標放在程式程式碼，然後按<kbd>F9</kbd> ，或從功能表列選擇 [ **Debug**  >  **切換中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="45ce2-123">Other ways to set a breakpoint are by placing the cursor in the line of code and then pressing <kbd>F9</kbd> or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="45ce2-124">如下圖所示，Visual Studio 表示藉由反白顯示中斷點，並在左邊界中顯示紅點，來設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="45ce2-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="45ce2-126">按下 <kbd>F5</kbd> 鍵，在「偵測模式」中執行程式。</span><span class="sxs-lookup"><span data-stu-id="45ce2-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="45ce2-127">啟動偵錯工具的另一種方式是從功能表中選擇 [ **Debug**  >  **開始調試**程式]。</span><span class="sxs-lookup"><span data-stu-id="45ce2-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="45ce2-128">當程式提示您輸入名稱時，在主控台視窗中輸入字串，然後按 <kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="45ce2-129">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="45ce2-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="45ce2-130">[區域變數]\*\*\*\* 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="45ce2-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio 中中斷點的螢幕擷取畫面](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a><span data-ttu-id="45ce2-132">使用即時運算視窗</span><span class="sxs-lookup"><span data-stu-id="45ce2-132">Use the Immediate window</span></span>

<span data-ttu-id="45ce2-133">[即時 **運算] 視窗** 可讓您與您要進行偵錯工具的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="45ce2-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="45ce2-134">您可以互動方式變更變數的值，以查看它對您的程式有何影響。</span><span class="sxs-lookup"><span data-stu-id="45ce2-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="45ce2-135">如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug**  >  **Windows**  >  **Immediate**] 來顯示。</span><span class="sxs-lookup"><span data-stu-id="45ce2-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="45ce2-136">`name = "Gracie"`在 [即時**Immediate**運算] 視窗中輸入，然後按下<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="45ce2-137">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`在 [即時**Immediate**運算] 視窗中輸入，然後按下<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="45ce2-138">[即時 **運算] 視窗** 會顯示字串變數的值和值的屬性 <xref:System.DateTime> 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="45ce2-139">此外，[ **區域變數** ] 視窗中的變數值也會更新。</span><span class="sxs-lookup"><span data-stu-id="45ce2-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Visual Studio 2019 中的區域變數和立即視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="45ce2-141">按 <kbd>F5</kbd> 繼續執行程式。</span><span class="sxs-lookup"><span data-stu-id="45ce2-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="45ce2-142">另一個繼續的方法是從功能表中選擇 [ **Debug**  >  **continue** ]。</span><span class="sxs-lookup"><span data-stu-id="45ce2-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="45ce2-143">[主控台] 視窗中顯示的值會對應到您在 [即時 **運算] 視窗** 中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="45ce2-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![顯示輸入值的主控台視窗](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="45ce2-145">按任意鍵以結束應用程式，並停止偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="45ce2-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="45ce2-146">設定條件式中斷點</span><span class="sxs-lookup"><span data-stu-id="45ce2-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="45ce2-147">程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="45ce2-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="45ce2-148">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="45ce2-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="45ce2-149">您可以使用稱為 *條件式中斷點*的實用調試功能來進行測試。</span><span class="sxs-lookup"><span data-stu-id="45ce2-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="45ce2-150">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="45ce2-151">在內容功能表中，選取 [ **條件** ] 以開啟 [ **中斷點設定** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="45ce2-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="45ce2-152">如果尚未選取 [ **條件** ] 方塊，請選取該方塊。</span><span class="sxs-lookup"><span data-stu-id="45ce2-152">Select the box for **Conditions** if it's not already selected.</span></span>

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="45ce2-154">在 **條件運算式**的欄位中，輸入下列程式碼，以顯示測試是否為5的範例程式碼 `x` 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="45ce2-155">如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。</span><span class="sxs-lookup"><span data-stu-id="45ce2-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="45ce2-156">每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在此行上中斷 `true` 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="45ce2-157">您可以指定叫用 *計數*（而不是條件運算式），以在指定的次數執行語句之前中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="45ce2-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="45ce2-158">另一個選項是指定 *篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱，以這類屬性來中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="45ce2-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="45ce2-159">選取 [ **關閉** ] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="45ce2-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="45ce2-160">按下 <kbd>F5</kbd>來啟動程式並進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="45ce2-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="45ce2-161">當系統提示您輸入名稱時，在主控台視窗中按 <kbd>enter</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="45ce2-162">因為您 (指定的條件 `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>) 已滿足，所以程式執行會在到達中斷點時，以及 `Console.WriteLine` 方法執行之前停止。</span><span class="sxs-lookup"><span data-stu-id="45ce2-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="45ce2-163">選取 [ **區域變數** ] 視窗，此視窗會顯示目前正在執行之方法的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="45ce2-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="45ce2-164">在此案例中， `Main` 是目前執行的方法。</span><span class="sxs-lookup"><span data-stu-id="45ce2-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="45ce2-165">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="45ce2-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="45ce2-166">**在 [即時**運算] 視窗中輸入下列語句，然後按<kbd>enter</kbd>，確認值為空字串。</span><span class="sxs-lookup"><span data-stu-id="45ce2-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="45ce2-167">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="45ce2-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="45ce2-168">問號會指示 [即時運算] 視窗 [評估運算式](/visualstudio/ide/reference/immediate-window#enter-commands)。</span><span class="sxs-lookup"><span data-stu-id="45ce2-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="45ce2-170">按 <kbd>F5</kbd> 繼續執行程式。</span><span class="sxs-lookup"><span data-stu-id="45ce2-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="45ce2-171">按任意鍵以關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="45ce2-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="45ce2-172">按一下程式碼視窗左邊界中的點，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="45ce2-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="45ce2-173">清除中斷點的其他方式是按 <kbd>F9</kbd> ，或在選取程式程式碼時，選擇 [ **Debug] > 切換中斷點** 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-173">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="45ce2-174">逐步執行程式</span><span class="sxs-lookup"><span data-stu-id="45ce2-174">Step through a program</span></span>

<span data-ttu-id="45ce2-175">Visual Studio 也可讓您逐行執行程式並監視其執行情況。</span><span class="sxs-lookup"><span data-stu-id="45ce2-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="45ce2-176">一般來說，您會設定中斷點，並遵循程式流程程式碼的一小部分。</span><span class="sxs-lookup"><span data-stu-id="45ce2-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="45ce2-177">因為這個程式很小，所以您可以逐步執行整個程式。</span><span class="sxs-lookup"><span data-stu-id="45ce2-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="45ce2-178">選擇 [**調試**  >  **逐步執行**]。</span><span class="sxs-lookup"><span data-stu-id="45ce2-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="45ce2-179">另一次一次調試一個語句的另一種方式是按 <kbd>F11</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="45ce2-180">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="45ce2-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="45ce2-181">C#</span><span class="sxs-lookup"><span data-stu-id="45ce2-181">C#</span></span>

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="45ce2-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45ce2-183">Visual Basic</span></span>

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="45ce2-185">此時，[ **區域變數** ] 視窗 `args` 會顯示陣列是空的，而且 `name` `date` 具有預設值。</span><span class="sxs-lookup"><span data-stu-id="45ce2-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="45ce2-186">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="45ce2-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="45ce2-187">按 <kbd>F11</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="45ce2-188">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="45ce2-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="45ce2-189">[ **區域變數** ] 視窗會保持不變，而且主控台視窗會維持空白。</span><span class="sxs-lookup"><span data-stu-id="45ce2-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="45ce2-190">C#</span><span class="sxs-lookup"><span data-stu-id="45ce2-190">C#</span></span>

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="45ce2-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45ce2-192">Visual Basic</span></span>

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="45ce2-194">按 <kbd>F11</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="45ce2-195">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="45ce2-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="45ce2-196">[ **區域變數** ] 視窗 `name` 會顯示 `null` ，而主控台視窗則會顯示「您的名稱為何？」字串。</span><span class="sxs-lookup"><span data-stu-id="45ce2-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="45ce2-197">在主控台視窗中輸入字串，然後按 <kbd>enter</kbd>，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="45ce2-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="45ce2-198">主控台沒有回應，而且您輸入的字串不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍會捕捉您的輸入。</span><span class="sxs-lookup"><span data-stu-id="45ce2-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="45ce2-199">按 <kbd>F11</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="45ce2-200">Visual Studio 反白顯示 `date` Visual Basic) 中包含變數指派 (的語句 `currentDate` 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="45ce2-201">[ **區域變數** ] 視窗會顯示呼叫方法所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="45ce2-202">主控台視窗也會顯示您在提示字元中輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="45ce2-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="45ce2-203">按 <kbd>F11</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="45ce2-204">[ **區域變數** ] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="45ce2-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="45ce2-205">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="45ce2-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="45ce2-206">按 <kbd>F11</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="45ce2-207">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="45ce2-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="45ce2-208">主控台視窗會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="45ce2-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="45ce2-209">選擇 [ **Debug**  >  **跳出**]。停止逐步執行的另一個方法是按<kbd>Shift</kbd> + <kbd>F11</kbd>。</span><span class="sxs-lookup"><span data-stu-id="45ce2-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="45ce2-210">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="45ce2-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="45ce2-211">按任意鍵以關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="45ce2-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="45ce2-212">使用發行組建設定</span><span class="sxs-lookup"><span data-stu-id="45ce2-212">Use Release build configuration</span></span>

<span data-ttu-id="45ce2-213">測試應用程式的偵錯工具版本之後，您應該也要編譯並測試發行版本。</span><span class="sxs-lookup"><span data-stu-id="45ce2-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="45ce2-214">發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="45ce2-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="45ce2-215">例如，針對改善效能而設計的編譯器優化，可能會在多執行緒應用程式中建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="45ce2-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="45ce2-216">若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯]\*\*\*\* 變更為 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45ce2-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="45ce2-218">當您按下<kbd>F5</kbd> ，或從 [**組建**] 功能表選擇 [**組建方案**] 時，Visual Studio 會編譯應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="45ce2-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="45ce2-219">您可以進行測試，就像是執行調試版本一樣。</span><span class="sxs-lookup"><span data-stu-id="45ce2-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="45ce2-220">後續步驟</span><span class="sxs-lookup"><span data-stu-id="45ce2-220">Next steps</span></span>

<span data-ttu-id="45ce2-221">在本教學課程中，您已使用 Visual Studio 調試工具。</span><span class="sxs-lookup"><span data-stu-id="45ce2-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="45ce2-222">在下一個教學課程中，您將發行應用程式的可部署版本。</span><span class="sxs-lookup"><span data-stu-id="45ce2-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="45ce2-223">使用 Visual Studio 發佈 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="45ce2-223">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
