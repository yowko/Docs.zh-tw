---
title: 使用 Visual Studio for Mac 來調試 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio Mac 來偵測 .NET Core 主控台應用程式。
ms.date: 06/08/2020
ms.openlocfilehash: 7e2a25266fab40b5ef1d0a38b8bbf06a6843746b
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416020"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="791ac-103">教學課程：使用 Visual Studio for Mac 來對 .NET Core 主控台應用程式進行 Debug</span><span class="sxs-lookup"><span data-stu-id="791ac-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="791ac-104">本教學課程介紹 Visual Studio for Mac 中提供的調試工具。</span><span class="sxs-lookup"><span data-stu-id="791ac-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="791ac-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="791ac-105">Prerequisites</span></span>

- <span data-ttu-id="791ac-106">本教學課程適用于您在 Visual Studio for Mac 中建立[.Net Core 主控台應用程式](with-visual-studio-mac.md)中建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="791ac-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="791ac-107">使用 Debug build configuration</span><span class="sxs-lookup"><span data-stu-id="791ac-107">Use Debug build configuration</span></span>

<span data-ttu-id="791ac-108">*Debug*和*Release*是 Visual Studio 的內建組建設定。</span><span class="sxs-lookup"><span data-stu-id="791ac-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="791ac-109">您可以使用 Debug 組建設定進行偵錯工具，以及發行設定進行最終發行散發。</span><span class="sxs-lookup"><span data-stu-id="791ac-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="791ac-110">在 Debug 設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="791ac-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="791ac-111">最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。</span><span class="sxs-lookup"><span data-stu-id="791ac-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="791ac-112">程式的發行設定沒有符號的 debug 資訊，而且已完全優化。</span><span class="sxs-lookup"><span data-stu-id="791ac-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="791ac-113">根據預設，Visual Studio 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前加以變更。</span><span class="sxs-lookup"><span data-stu-id="791ac-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="791ac-114">啟動 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="791ac-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="791ac-115">在 Visual Studio for Mac 中，開啟您在[建立 .Net Core 主控台應用程式](with-visual-studio-mac.md)中建立的專案。</span><span class="sxs-lookup"><span data-stu-id="791ac-115">Open the project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="791ac-116">目前的組建組態會顯示在工具列上。</span><span class="sxs-lookup"><span data-stu-id="791ac-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="791ac-117">下列工具列影像顯示 Visual Studio 設定為編譯應用程式的 Debug 版本：</span><span class="sxs-lookup"><span data-stu-id="791ac-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="已反白顯示 debug 的 Visual Studio 工具列":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="791ac-119">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="791ac-119">Set a breakpoint</span></span>

<span data-ttu-id="791ac-120">「中斷點」\*\* 會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="791ac-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="791ac-121">在顯示名稱、日期和時間的程式程式碼上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="791ac-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="791ac-122">若要這麼做，請將游標放在程式程式碼中，然後按<kbd>則是⌘</kbd> <kbd>\\</kbd> （<kbd>command</kbd> + <kbd>\\</kbd> ）。</span><span class="sxs-lookup"><span data-stu-id="791ac-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="791ac-123">設定中斷點的另一種方式是**Run**  >  從功能表中選取 [執行] [**切換中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="791ac-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="791ac-124">Visual Studio 表示藉由反白顯示中斷點，並在左邊界顯示一個紅點，來設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="791ac-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="已設定中斷點的 Visual Studio 程式視窗":::

1. <span data-ttu-id="791ac-126">按<kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>命令</kbd> + <kbd>enter</kbd>）以在偵錯工具模式中啟動程式。</span><span class="sxs-lookup"><span data-stu-id="791ac-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="791ac-127">另一個開始進行偵錯工具的方式，是從功能表中選擇 [**執行**] [  >  **開始調試**]。</span><span class="sxs-lookup"><span data-stu-id="791ac-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="791ac-128">當程式提示您輸入名稱時，請在終端機視窗中輸入字串，然後按<kbd>enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="791ac-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="791ac-129">在方法執行之前，程式執行會在到達中斷點時停止 `Console.WriteLine` 。</span><span class="sxs-lookup"><span data-stu-id="791ac-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio 中中斷點的螢幕擷取畫面":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="791ac-131">使用即時運算視窗</span><span class="sxs-lookup"><span data-stu-id="791ac-131">Use the Immediate window</span></span>

<span data-ttu-id="791ac-132">[即時運算 **] 視窗可**讓您與正在調試的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="791ac-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="791ac-133">您可以互動方式變更變數的值，以查看它對您的程式有何影響。</span><span class="sxs-lookup"><span data-stu-id="791ac-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="791ac-134">如果看**不到 [** 即時運算] 視窗，請選擇 [立即**觀看**] [  >  **Debug pad**] 來顯示  >  \*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="791ac-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="791ac-135">`name = "Gracie"`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="791ac-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="791ac-136">`date = date.AddDays(1)`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="791ac-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="791ac-137">[即時**運算] 視窗**會顯示字串變數的新值和值的屬性 <xref:System.DateTime> 。</span><span class="sxs-lookup"><span data-stu-id="791ac-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio 中的 [即時運算] 視窗":::

   <span data-ttu-id="791ac-139">[區域變數]\*\*\*\* 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="791ac-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="791ac-140">您剛變更的變數值會在 [**區域變數**] 視窗中更新。</span><span class="sxs-lookup"><span data-stu-id="791ac-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio 中的 [區域變數] 視窗":::

1. <span data-ttu-id="791ac-142">按<kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>命令</kbd> + <kbd>enter</kbd>）以繼續進行調試。</span><span class="sxs-lookup"><span data-stu-id="791ac-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="791ac-143">終端機中顯示的值會對應至**您在 [即時運算] 視窗**中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="791ac-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="791ac-144">如果您沒有看到終端機，請選取下方導覽列中的 [**終端機-HelloWorld** ]。</span><span class="sxs-lookup"><span data-stu-id="791ac-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="底部導覽列中的終端機 Hello World":::

1. <span data-ttu-id="791ac-146">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="791ac-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="791ac-147">關閉終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="791ac-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="791ac-148">設定條件式中斷點</span><span class="sxs-lookup"><span data-stu-id="791ac-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="791ac-149">程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="791ac-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="791ac-150">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="791ac-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="791ac-151">您可以使用稱為*條件式中斷點*的實用調試功能來測試此項。</span><span class="sxs-lookup"><span data-stu-id="791ac-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="791ac-152"><kbd>ctrl</kbd>-按一下代表中斷點的紅點。</span><span class="sxs-lookup"><span data-stu-id="791ac-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="791ac-153">在內容功能表中，選取 [**編輯中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="791ac-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="791ac-154">在 [**編輯中斷點**] 對話方塊中，于後面的欄位中輸入下列程式碼，**而且下列條件為 true**，**然後選取**[套用]。</span><span class="sxs-lookup"><span data-stu-id="791ac-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="顯示中斷點設定面板的編輯器":::

   <span data-ttu-id="791ac-156">每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在這一行上中斷 `true` 。</span><span class="sxs-lookup"><span data-stu-id="791ac-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="791ac-157">除了條件運算式之外，您還可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="791ac-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="791ac-158">按<kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>命令</kbd> + <kbd>enter</kbd>）以開始進行調試。</span><span class="sxs-lookup"><span data-stu-id="791ac-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="791ac-159">當系統提示您輸入名稱時，請在終端機視窗中按下<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="791ac-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="791ac-160">因為已滿足您指定的條件（ `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> ），所以程式會在到達中斷點時停止執行。</span><span class="sxs-lookup"><span data-stu-id="791ac-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="791ac-161">選取 [**區域變數**] 視窗，其中會顯示目前執行之方法的本機變數值。</span><span class="sxs-lookup"><span data-stu-id="791ac-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="791ac-162">在此情況下， `Main` 是目前正在執行的方法。</span><span class="sxs-lookup"><span data-stu-id="791ac-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="791ac-163">請觀察變數的值 `name` 是 `""` ，也就是 <xref:System.String.Empty?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="791ac-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="791ac-164">您也可以 `name` 在 [即時運算] 視窗中輸入變數名稱，然後按<kbd>enter</kbd>鍵**Immediate** ，以查看值是否為空字串。</span><span class="sxs-lookup"><span data-stu-id="791ac-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="顯示名稱的即時運算視窗是空字串":::

1. <span data-ttu-id="791ac-166">按<kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>命令</kbd> + <kbd>enter</kbd>）以繼續進行調試。</span><span class="sxs-lookup"><span data-stu-id="791ac-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="791ac-167">在終端機視窗中，按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="791ac-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="791ac-168">關閉終端機視窗。</span><span class="sxs-lookup"><span data-stu-id="791ac-168">Close the terminal window.</span></span>

1. <span data-ttu-id="791ac-169">按一下程式碼視窗左邊界中的紅色點，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="791ac-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="791ac-170">清除中斷點的另一種方法是在選取程式程式碼時，選擇 [**執行] > 切換中斷點**。</span><span class="sxs-lookup"><span data-stu-id="791ac-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="791ac-171">逐步執行程式</span><span class="sxs-lookup"><span data-stu-id="791ac-171">Step through a program</span></span>

<span data-ttu-id="791ac-172">Visual Studio 也可讓您逐行執行程式並監視其執行情況。</span><span class="sxs-lookup"><span data-stu-id="791ac-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="791ac-173">一般來說，您會設定中斷點，並在程式碼的一小部分追蹤程式流程。</span><span class="sxs-lookup"><span data-stu-id="791ac-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="791ac-174">因為此程式很小，所以您可以逐步執行整個程式。</span><span class="sxs-lookup"><span data-stu-id="791ac-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="791ac-175">在用來標記方法開頭的大括弧上設定中斷點 `Main` （按下<kbd>命令</kbd> + <kbd>\\</kbd> ）。</span><span class="sxs-lookup"><span data-stu-id="791ac-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="791ac-176">按<kbd>則是⌘</kbd><kbd>↵</kbd> （<kbd>命令</kbd> + <kbd>enter</kbd>）以開始進行調試。</span><span class="sxs-lookup"><span data-stu-id="791ac-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="791ac-177">Visual Studio 會在含有中斷點的行上停止。</span><span class="sxs-lookup"><span data-stu-id="791ac-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="791ac-178">按<kbd>⇧</kbd><kbd>則是⌘</kbd><kbd>I</kbd> （<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>），或選取 [**執行**] [  >  **逐步**執行] 以推進一行。</span><span class="sxs-lookup"><span data-stu-id="791ac-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="791ac-179">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="791ac-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio 逐步執行方法":::

   <span data-ttu-id="791ac-181">此時，[**區域變數**] 視窗 `args` 會顯示陣列是空的，而且 `name` 和 `date` 都有預設值。</span><span class="sxs-lookup"><span data-stu-id="791ac-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="791ac-182">此外，Visual Studio 已開啟空白的終端機。</span><span class="sxs-lookup"><span data-stu-id="791ac-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="791ac-183">按<kbd>⇧</kbd><kbd>則是⌘</kbd><kbd>I</kbd> （<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>）。</span><span class="sxs-lookup"><span data-stu-id="791ac-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="791ac-184">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="791ac-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="791ac-185">[**區域變數**] 視窗 `name` 會顯示為 `null` ，而終端機會顯示「您的名稱是什麼？」字串。</span><span class="sxs-lookup"><span data-stu-id="791ac-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="791ac-186">在主控台視窗中輸入字串，然後按<kbd>enter</kbd>，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="791ac-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="791ac-187">按<kbd>⇧</kbd><kbd>則是⌘</kbd><kbd>I</kbd> （<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>）。</span><span class="sxs-lookup"><span data-stu-id="791ac-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="791ac-188">Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="791ac-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="791ac-189">[**區域變數**] 視窗會顯示呼叫方法時所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="791ac-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="791ac-190">終端機會顯示您在提示字元中輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="791ac-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="791ac-191">按<kbd>⇧</kbd><kbd>則是⌘</kbd><kbd>I</kbd> （<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>）。</span><span class="sxs-lookup"><span data-stu-id="791ac-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="791ac-192">[**區域變數**] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="791ac-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="791ac-193">終端機不變。</span><span class="sxs-lookup"><span data-stu-id="791ac-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="791ac-194">按<kbd>⇧</kbd><kbd>則是⌘</kbd><kbd>I</kbd> （<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>）。</span><span class="sxs-lookup"><span data-stu-id="791ac-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="791ac-195">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="791ac-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="791ac-196">終端機會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="791ac-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="791ac-197">按<kbd>⇧</kbd><kbd>則是⌘</kbd><kbd>U</kbd> （<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>U</kbd>）或選取 [**執行**  >  \*\* \*\*] [跳出]。</span><span class="sxs-lookup"><span data-stu-id="791ac-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="791ac-198">終端機會顯示一則訊息，並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="791ac-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="791ac-199">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="791ac-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="791ac-200">使用發行組建設定</span><span class="sxs-lookup"><span data-stu-id="791ac-200">Use Release build configuration</span></span>

<span data-ttu-id="791ac-201">測試過應用程式的 Debug 版本之後，您也應該編譯和測試發行版本。</span><span class="sxs-lookup"><span data-stu-id="791ac-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="791ac-202">發行版本包含可能會對應用程式行為造成負面影響的編譯器優化。</span><span class="sxs-lookup"><span data-stu-id="791ac-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="791ac-203">例如，針對改善效能而設計的編譯器優化，可以在多執行緒應用程式中建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="791ac-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="791ac-204">若要建立並測試主控台應用程式的發行版本，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="791ac-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="791ac-205">將工具列上的組建設定從 [**調試**] 變更為 [**發行**]。</span><span class="sxs-lookup"><span data-stu-id="791ac-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="醒目提示 [偵錯] 的預設 Visual Studio 工具列":::

1. <span data-ttu-id="791ac-207">按 [ <kbd>⌥</kbd><kbd>則是⌘</kbd><kbd>↵</kbd> ] （<kbd>選項</kbd> + <kbd>命令</kbd> + <kbd>enter</kbd>）以在不進行調試的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="791ac-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="791ac-208">後續步驟</span><span class="sxs-lookup"><span data-stu-id="791ac-208">Next steps</span></span>

<span data-ttu-id="791ac-209">在本教學課程中，您已使用 Visual Studio 調試工具。</span><span class="sxs-lookup"><span data-stu-id="791ac-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="791ac-210">在下一個教學課程中，您會發佈可部署的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="791ac-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="791ac-211">使用 Visual Studio for Mac 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="791ac-211">Publish a .NET Core console application with Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
