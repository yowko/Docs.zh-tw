---
title: 使用 Visual Studio for Mac 來對 .NET Core 主控台應用程式進行偵錯工具
description: 瞭解如何使用 Visual Studio Mac 來對 .NET Core 主控台應用程式進行 debug 錯。
ms.date: 06/08/2020
ms.openlocfilehash: 79936fb99d0bc37c1234eb8f227eb5415ae48b93
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867564"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="4791a-103">教學課程：使用 Visual Studio for Mac 對 .NET Core 主控台應用程式進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="4791a-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="4791a-104">本教學課程介紹 Visual Studio for Mac 中提供的調試工具。</span><span class="sxs-lookup"><span data-stu-id="4791a-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4791a-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="4791a-105">Prerequisites</span></span>

- <span data-ttu-id="4791a-106">本教學課程適用于您 [使用 Visual Studio for Mac 建立 .Net Core 主控台應用程式](with-visual-studio-mac.md)中所建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4791a-106">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="4791a-107">使用 Debug build configuration</span><span class="sxs-lookup"><span data-stu-id="4791a-107">Use Debug build configuration</span></span>

<span data-ttu-id="4791a-108">*Debug* 和 *Release* 是 Visual Studio 的內建組建設定。</span><span class="sxs-lookup"><span data-stu-id="4791a-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="4791a-109">您可以使用 Debug 組建設定進行偵錯工具，並使用發行設定來進行最終發行散發。</span><span class="sxs-lookup"><span data-stu-id="4791a-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="4791a-110">在「偵錯工具」設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="4791a-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="4791a-111">最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。</span><span class="sxs-lookup"><span data-stu-id="4791a-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="4791a-112">程式的發行設定沒有符號的 debug 資訊，而且已完全優化。</span><span class="sxs-lookup"><span data-stu-id="4791a-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="4791a-113">根據預設，Visual Studio 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前進行變更。</span><span class="sxs-lookup"><span data-stu-id="4791a-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="4791a-114">開始 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="4791a-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="4791a-115">開啟您在 [使用 Visual Studio for Mac 建立 .Net Core 主控台應用程式](with-visual-studio-mac.md)中建立的專案。</span><span class="sxs-lookup"><span data-stu-id="4791a-115">Open the project that you created in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="4791a-116">目前的組建組態會顯示在工具列上。</span><span class="sxs-lookup"><span data-stu-id="4791a-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="4791a-117">下列工具列影像顯示 Visual Studio 設定為編譯應用程式的偵錯工具版本：</span><span class="sxs-lookup"><span data-stu-id="4791a-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="醒目提示反白顯示的 Visual Studio 工具列":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="4791a-119">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="4791a-119">Set a breakpoint</span></span>

<span data-ttu-id="4791a-120">「中斷點」\*\* 會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="4791a-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="4791a-121">在顯示名稱、日期和時間的行上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="4791a-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="4791a-122">若要這樣做，請將游標放在程式程式碼中，然後按<kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>命令</kbd> + <kbd>\\</kbd>) 。</span><span class="sxs-lookup"><span data-stu-id="4791a-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="4791a-123">設定中斷點的另一種方式是， **Run**  >  從功能表中選取 [執行**切換中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="4791a-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="4791a-124">Visual Studio 表示藉由反白顯示中斷點，並在左邊界中顯示紅點，來設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="4791a-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="已設定中斷點的 Visual Studio 程式視窗":::

1. <span data-ttu-id="4791a-126">按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) ，以在偵測模式中啟動程式。</span><span class="sxs-lookup"><span data-stu-id="4791a-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="4791a-127">啟動偵錯工具的另一種方式是從功能表中選擇 [**執行**  >  **開始調試**程式]。</span><span class="sxs-lookup"><span data-stu-id="4791a-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="4791a-128">當程式提示您輸入名稱時，在終端機視窗中輸入字串，然後按 <kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="4791a-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="4791a-129">在方法執行之前，程式執行會在到達中斷點時停止 `Console.WriteLine` 。</span><span class="sxs-lookup"><span data-stu-id="4791a-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio 中中斷點的螢幕擷取畫面":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="4791a-131">使用即時運算視窗</span><span class="sxs-lookup"><span data-stu-id="4791a-131">Use the Immediate window</span></span>

<span data-ttu-id="4791a-132">[即時 **運算] 視窗** 可讓您與您要進行偵錯工具的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="4791a-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="4791a-133">您可以互動方式變更變數的值，以查看它對您的程式有何影響。</span><span class="sxs-lookup"><span data-stu-id="4791a-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="4791a-134">如果看**不到 [** 即時運算] 視窗，請選擇 [立即**觀看**  >  **Debug pad**] 來顯示它  >  \*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="4791a-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="4791a-135">`name = "Gracie"`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="4791a-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="4791a-136">`date = date.AddDays(1)`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="4791a-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="4791a-137">[即時 **運算] 視窗** 會顯示字串變數的新值和值的屬性 <xref:System.DateTime> 。</span><span class="sxs-lookup"><span data-stu-id="4791a-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio 中的 [即時運算] 視窗":::

   <span data-ttu-id="4791a-139">[區域變數]\*\*\*\* 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="4791a-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="4791a-140">您剛剛變更之變數的值會在 [ **區域變數** ] 視窗中更新。</span><span class="sxs-lookup"><span data-stu-id="4791a-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio 中的 [區域變數] 視窗":::

1. <span data-ttu-id="4791a-142">按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以繼續進行調試。</span><span class="sxs-lookup"><span data-stu-id="4791a-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="4791a-143">顯示在終端機中的值會對應到您在 [即時 **運算] 視窗** 中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="4791a-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="4791a-144">如果您看不到終端機，請選取底部導覽列中的 [ **終端機-HelloWorld** ]。</span><span class="sxs-lookup"><span data-stu-id="4791a-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="底部導覽列中的終端 Hello World":::

1. <span data-ttu-id="4791a-146">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="4791a-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="4791a-147">關閉終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="4791a-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="4791a-148">設定條件式中斷點</span><span class="sxs-lookup"><span data-stu-id="4791a-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="4791a-149">程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="4791a-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="4791a-150">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="4791a-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="4791a-151">您可以使用稱為 *條件式中斷點*的實用調試功能來進行測試。</span><span class="sxs-lookup"><span data-stu-id="4791a-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="4791a-152"><kbd>ctrl</kbd>-按一下代表中斷點的紅點。</span><span class="sxs-lookup"><span data-stu-id="4791a-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="4791a-153">在內容功能表中，選取 [ **編輯中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="4791a-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="4791a-154">在 [ **編輯中斷點** ] 對話方塊中，在下欄欄位中輸入下列程式碼， **並將下列條件設為 true**， **然後選取**[套用]。</span><span class="sxs-lookup"><span data-stu-id="4791a-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="顯示中斷點設定面板的編輯器":::

   <span data-ttu-id="4791a-156">每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在此行上中斷 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4791a-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="4791a-157">您可以指定叫用 *計數*（而不是條件運算式），以在指定的次數執行語句之前中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="4791a-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="4791a-158">按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以開始進行調試。</span><span class="sxs-lookup"><span data-stu-id="4791a-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="4791a-159">當系統提示您輸入名稱時，請在終端機視窗中按下 <kbd>enter</kbd> 。</span><span class="sxs-lookup"><span data-stu-id="4791a-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="4791a-160">因為您 (指定的條件 `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>) 已滿足，所以程式執行會在到達中斷點時停止。</span><span class="sxs-lookup"><span data-stu-id="4791a-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="4791a-161">選取 [ **區域變數** ] 視窗，此視窗會顯示目前正在執行之方法的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="4791a-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="4791a-162">在此案例中， `Main` 是目前執行的方法。</span><span class="sxs-lookup"><span data-stu-id="4791a-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="4791a-163">請注意，變數的值 `name` 是 `""` ，也就是 <xref:System.String.Empty?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4791a-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="4791a-164">您也可以 `name` 在 [即時運算] 視窗中輸入變數名稱，然後按<kbd>enter</kbd>， **Immediate**以查看值是否為空字串。</span><span class="sxs-lookup"><span data-stu-id="4791a-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="顯示名稱為空字串的 [即時運算] 視窗":::

1. <span data-ttu-id="4791a-166">按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以繼續進行調試。</span><span class="sxs-lookup"><span data-stu-id="4791a-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="4791a-167">在終端機視窗中，按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="4791a-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="4791a-168">關閉終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="4791a-168">Close the terminal window.</span></span>

1. <span data-ttu-id="4791a-169">按一下程式碼視窗左邊界的紅點，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="4791a-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="4791a-170">清除中斷點的另一種方式是在選取程式程式碼時，選擇 [ **執行] > 切換中斷點** 。</span><span class="sxs-lookup"><span data-stu-id="4791a-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="4791a-171">逐步執行程式</span><span class="sxs-lookup"><span data-stu-id="4791a-171">Step through a program</span></span>

<span data-ttu-id="4791a-172">Visual Studio 也可讓您逐行執行程式並監視其執行情況。</span><span class="sxs-lookup"><span data-stu-id="4791a-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="4791a-173">一般來說，您會設定中斷點，並遵循程式流程程式碼的一小部分。</span><span class="sxs-lookup"><span data-stu-id="4791a-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="4791a-174">因為這個程式很小，所以您可以逐步執行整個程式。</span><span class="sxs-lookup"><span data-stu-id="4791a-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="4791a-175">在大括弧上設定中斷點，以標示方法的開頭 `Main` (按下<kbd>命令</kbd> + <kbd>\\</kbd>) 。</span><span class="sxs-lookup"><span data-stu-id="4791a-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="4791a-176">按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以開始進行調試。</span><span class="sxs-lookup"><span data-stu-id="4791a-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="4791a-177">Visual Studio 在含有中斷點的行上停止。</span><span class="sxs-lookup"><span data-stu-id="4791a-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="4791a-178">按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 或選取 [**執行**  >  **逐步**執行] 以一行前進。</span><span class="sxs-lookup"><span data-stu-id="4791a-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="4791a-179">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="4791a-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio 逐步執行方法":::

   <span data-ttu-id="4791a-181">此時，[ **區域變數** ] 視窗 `args` 會顯示陣列是空的，而且 `name` `date` 具有預設值。</span><span class="sxs-lookup"><span data-stu-id="4791a-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="4791a-182">此外，Visual Studio 也開啟了空白的終端機。</span><span class="sxs-lookup"><span data-stu-id="4791a-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="4791a-183">按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。</span><span class="sxs-lookup"><span data-stu-id="4791a-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4791a-184">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4791a-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="4791a-185">[ **區域變數** ] 視窗 `name` 會顯示 `null` ，而終端機會顯示「您的姓名為何？」字串。</span><span class="sxs-lookup"><span data-stu-id="4791a-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="4791a-186">在主控台視窗中輸入字串，然後按 <kbd>enter</kbd>，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="4791a-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="4791a-187">按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。</span><span class="sxs-lookup"><span data-stu-id="4791a-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4791a-188">Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4791a-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="4791a-189">[ **區域變數** ] 視窗會顯示呼叫方法所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4791a-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4791a-190">終端機會顯示您在提示字元中輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="4791a-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="4791a-191">按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。</span><span class="sxs-lookup"><span data-stu-id="4791a-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4791a-192">[ **區域變數** ] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4791a-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4791a-193">終端機未變更。</span><span class="sxs-lookup"><span data-stu-id="4791a-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="4791a-194">按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。</span><span class="sxs-lookup"><span data-stu-id="4791a-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="4791a-195">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4791a-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4791a-196">終端機會顯示格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="4791a-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="4791a-197">按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>U</kbd>) 或選取 [**執行**  >  **跳出**]。</span><span class="sxs-lookup"><span data-stu-id="4791a-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="4791a-198">終端機會顯示一則訊息，並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="4791a-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="4791a-199">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="4791a-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="4791a-200">使用發行組建設定</span><span class="sxs-lookup"><span data-stu-id="4791a-200">Use Release build configuration</span></span>

<span data-ttu-id="4791a-201">測試應用程式的偵錯工具版本之後，您應該也要編譯並測試發行版本。</span><span class="sxs-lookup"><span data-stu-id="4791a-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="4791a-202">發行版本所併入的編譯器優化可能會對應用程式的行為造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="4791a-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="4791a-203">例如，針對改善效能而設計的編譯器優化，可能會在多執行緒應用程式中建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="4791a-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="4791a-204">若要建立並測試主控台應用程式的發行版本，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4791a-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="4791a-205">將工具列上的組建設定從 [ **Debug** ] 變更為 [ **發行**]。</span><span class="sxs-lookup"><span data-stu-id="4791a-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="醒目提示 [偵錯] 的預設 Visual Studio 工具列":::

1. <span data-ttu-id="4791a-207">按<kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>命令</kbd> + <kbd>輸入</kbd>) ，以在不進行調試的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="4791a-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4791a-208">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4791a-208">Next steps</span></span>

<span data-ttu-id="4791a-209">在本教學課程中，您已使用 Visual Studio 調試工具。</span><span class="sxs-lookup"><span data-stu-id="4791a-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="4791a-210">在下一個教學課程中，您將發行應用程式的可部署版本。</span><span class="sxs-lookup"><span data-stu-id="4791a-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4791a-211">使用 Visual Studio for Mac 發佈 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4791a-211">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
