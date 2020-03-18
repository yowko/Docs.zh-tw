---
title: 調試您的Hello世界.NET核心應用程式與視覺化工作室
description: 瞭解如何調試使用 Visual Studio 編寫的"Hello World"應用或視覺化基本版。
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156669"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a><span data-ttu-id="9b8d2-103">使用視覺化工作室調試您的 C# 或視覺化基本 .NET 核心 Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="9b8d2-103">Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio</span></span>

<span data-ttu-id="9b8d2-104">到目前為止，您已經按照在[Visual Studio 2019 中創建第一個 .NET 酷睿主控台應用程式](with-visual-studio.md)的步驟來創建和運行簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-104">So far, you've followed the steps in [Create your first .NET Core console application in Visual Studio 2019](with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="9b8d2-105">在您撰寫並編譯應用程式之後，便可以開始測試它。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-105">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="9b8d2-106">Visual Studio 包含一套全面的調試工具，可用於對應用程式進行故障排除。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-106">Visual Studio includes a comprehensive set of debugging tools that you can use to troubleshoot your application.</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="9b8d2-107">調試組建組態</span><span class="sxs-lookup"><span data-stu-id="9b8d2-107">Debug build configuration</span></span>

<span data-ttu-id="9b8d2-108">[偵錯]\*\* 和 [發行]\*\* 是 Visual Studio 其中兩個預設的組建組態。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="9b8d2-109">目前的組建組態會顯示在工具列上。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="9b8d2-110">以下工具列圖像顯示 Visual Studio 配置為編譯應用程式的調試版本：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![具有調試突出顯示的視覺化工作室工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="9b8d2-112">首先運行應用的調試版本。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-112">Begin by running the Debug version of your app.</span></span> <span data-ttu-id="9b8d2-113">調試組建組態將關閉大多數編譯器優化，並在生成過程中提供更豐富的資訊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="9b8d2-114">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="9b8d2-114">Set a breakpoint</span></span>

<span data-ttu-id="9b8d2-115">運行程式並嘗試一些調試功能：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-115">Run your program and try a few debugging features:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="9b8d2-116">C#</span><span class="sxs-lookup"><span data-stu-id="9b8d2-116">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="9b8d2-117">通過按一下該行上代碼視窗的左邊`Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");`距，在行上設置*讀取的中斷點*。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-117">Set a *breakpoint* on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="9b8d2-118">還可以設置中斷點，將撥圖放在程式碼中，然後按**F9**或從功能表列中選擇 **"調試** > **切換中斷點**"。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-118">You can also set a breakpoint by placing the caret in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="9b8d2-119">「中斷點」會在含有中斷點的行執行「之前」\*\*，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-119">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="9b8d2-120">如下圖所示，Visual Studio 通過突出顯示中斷點並在其左邊距顯示一個紅色圓圈來指示設置中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-120">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="9b8d2-122">在偵錯模式下運行程式，選擇工具列上帶有綠色箭頭的**HelloWorld**按鈕，按**F5**，或選擇**調試** > **啟動調試**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-122">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing **F5**, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="9b8d2-123">當程式提示名稱時，在主控台視窗中輸入字串，**然後按**Enter 。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-123">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="9b8d2-124">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-124">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="9b8d2-125">[區域變數]\*\*\*\* 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-125">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![視覺工作室中斷點截圖](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="9b8d2-127">**通過"立即"** 視窗，您可以與正在調試的應用程式進行交互。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-127">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="9b8d2-128">您可以以對話模式更改變數的值，以查看它如何影響程式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-128">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="9b8d2-129">如果 **"立即"** 視窗不可見，則通過選擇 **"立即調試** > **Windows"** > **Immediate**來顯示它。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-129">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="9b8d2-130">輸入`name = "Gracie"`**"立即"** 視窗並按**Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-130">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="9b8d2-131">輸入`date = DateTime.Parse("11/16/2019 5:25 PM")`**"立即"** 視窗並按**Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-131">Enter `date = DateTime.Parse("11/16/2019 5:25 PM")` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="9b8d2-132">**"立即"** 視窗顯示字串變數的值和值的屬性<xref:System.DateTime>。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-132">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="9b8d2-133">此外，變數的值在 **"區域變數"** 視窗中更新。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-133">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![2019 年視覺化工作室中的本地和即時視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="9b8d2-135">通過在工具列中選擇 **"繼續"** 按鈕或選擇 **"調試** > **繼續"** 來繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-135">Continue program execution by selecting the **Continue** button in the toolbar or by selecting **Debug** > **Continue**.</span></span> <span data-ttu-id="9b8d2-136">主控台視窗中顯示的值與您在 **"立即"** 視窗中所做的更改相對應。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![顯示輸入值的主控台視窗](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="9b8d2-138">按任意鍵退出應用程式並停止調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-138">Press any key to exit the application and stop debugging.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="9b8d2-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b8d2-139">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="9b8d2-140">通過按一下該行上代碼視窗的左邊`Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")`距，在行上設置*讀取的中斷點*。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-140">Set a *breakpoint* on the line that reads `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="9b8d2-141">還可以設置中斷點，將 care 放在所需的線路上，然後從功能表列中選擇 **"調試** > **切換中斷點**"。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-141">You can also set a breakpoint by placing the caret on the desired line and then choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="9b8d2-142">「中斷點」會在含有中斷點的行執行「之前」\*\*，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-142">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="9b8d2-143">如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-143">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. <span data-ttu-id="9b8d2-145">在偵錯模式下運行程式，選擇工具列上帶有綠色箭頭的**HelloWorld**按鈕，按**F5**，或選擇**調試** > **啟動調試**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-145">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing **F5**, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="9b8d2-146">當程式提示名稱並按 Enter 時，在主控台視窗中**輸入**字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-146">Enter a string in the console window when the program prompts for a name and press **Enter**.</span></span>

1. <span data-ttu-id="9b8d2-147">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-147">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="9b8d2-148">[區域變數]\*\*\*\* 視窗會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-148">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

1. <span data-ttu-id="9b8d2-149">**通過"立即"** 視窗，您可以與正在調試的應用程式進行交互。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-149">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="9b8d2-150">您可以以對話模式更改變數的值，以查看它如何影響程式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-150">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="9b8d2-151">如果 **"立即"** 視窗不可見，則通過選擇 **"立即調試** > **Windows"** > **Immediate**來顯示它。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-151">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="9b8d2-152">輸入`name = "Gracie"`**"立即"** 視窗並按**Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-152">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="9b8d2-153">輸入`date = DateTime.Parse("11/16/2019 5:25 PM")`**"立即"** 視窗並按**Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-153">Enter `date = DateTime.Parse("11/16/2019 5:25 PM")` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="9b8d2-154">變數的值在 **"區域變數"** 視窗中更新。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-154">The values of the variables are updated in the **Locals** window.</span></span>

1. <span data-ttu-id="9b8d2-155">選取工具列中的 [繼續]\*\*\*\* 按鈕，或選取 [偵錯]\*\*\*\* >  [繼續]\*\*\*\* 功能表項目，以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-155">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="9b8d2-156">主控台視窗中顯示的值與您在 **"立即"** 視窗中所做的更改相對應。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-156">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![顯示輸入值的主控台視窗](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="9b8d2-158">按任意鍵退出應用程式並停止調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-158">Press any key to exit the application and stop debugging.</span></span>

---

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="9b8d2-159">設置條件中斷點</span><span class="sxs-lookup"><span data-stu-id="9b8d2-159">Set a conditional breakpoint</span></span>

<span data-ttu-id="9b8d2-160">您的程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-160">Your program displays the string that the user enters.</span></span> <span data-ttu-id="9b8d2-161">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="9b8d2-161">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="9b8d2-162">您可以使用稱為*條件中斷點*的有用調試功能來測試，當滿足一個或多個條件時，該功能將中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-162">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="9b8d2-163">若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-163">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="c"></a>[<span data-ttu-id="9b8d2-164">C#</span><span class="sxs-lookup"><span data-stu-id="9b8d2-164">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="9b8d2-165">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-165">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="9b8d2-166">在內容功能表上，選取 [條件]\*\*\*\* 以開啟 [中斷點設定]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-166">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="9b8d2-167">如果尚未選中條件，請選中 **"條件**"核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-167">Check the box for **Conditions** if it's not already selected.</span></span>

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="9b8d2-169">對於**條件運算式**，將"例如 x = = 5"替換為以下內容：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-169">For the **Conditional Expression**, replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="9b8d2-170">您正在測試一個代碼條件，`String.IsNullOrEmpty(name)`方法調用是因為`true``name`尚未分配值，或者因為它的值是空字串 （""）。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-170">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because `name` has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="9b8d2-171">也可以指定*命中計數*，該計數在語句執行指定次數之前中斷程式執行，也可以指定*篩選器條件*，該條件基於執行緒識別碼、進程名稱或執行緒名稱等屬性中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-171">Instead of a conditional expression, you can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="9b8d2-172">選擇 **"關閉"** 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-172">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="9b8d2-173">通過按**F5**啟動程式以調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-173">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="9b8d2-174">在主控台視窗中，在提示輸入您的姓名時按**Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-174">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="9b8d2-175">由於您指定的`name`條件或`null`<xref:System.String.Empty?displayProperty=nameWithType>已滿足，因此程式執行在到達中斷點時和`Console.WriteLine`方法執行之前停止。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-175">Because the condition you specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="9b8d2-176">選擇 **"區域變數"** 視窗，該視窗顯示當前執行方法的區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-176">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="9b8d2-177">在這種情況下，`Main`是當前執行的方法。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-177">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="9b8d2-178">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-178">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="9b8d2-179">通過在 **"立即"** 視窗中輸入以下語句並按**Enter**， 確認該值是空字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-179">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="9b8d2-180">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-180">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="9b8d2-182">選取工具列上的 [繼續]\*\*\*\* 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-182">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="9b8d2-183">按任意鍵關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-183">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="9b8d2-184">按一下代碼視窗左邊距中的點，或在選擇程式碼時選擇 **"調試>切換中斷點**"來清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-184">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="9b8d2-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b8d2-185">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="9b8d2-186">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-186">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="9b8d2-187">在內容功能表上，選取 [條件]\*\*\*\* 以開啟 [中斷點設定]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-187">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="9b8d2-188">核取 [條件]\*\*\*\* 的方塊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-188">Check the box for **Conditions**.</span></span>

   ![顯示中斷點設定面板的編輯器 - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="9b8d2-190">對於**條件運算式**，請將"例如 x = 5"替換為以下內容：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-190">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="9b8d2-191">您正在測試一個代碼條件，`String.IsNullOrEmpty(name)`方法調用是因為`true``name`尚未分配值，或者因為它的值是空字串 （""）。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-191">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because `name` has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="9b8d2-192">也可以指定*命中計數*，該計數在語句執行指定次數之前中斷程式執行，也可以指定*篩選器條件*，該條件基於執行緒識別碼、進程名稱或執行緒名稱等屬性中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-192">Instead of a conditional expression, you can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="9b8d2-193">選擇 **"關閉"** 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-193">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="9b8d2-194">通過按**F5**啟動程式以調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-194">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="9b8d2-195">在主控台視窗中，在提示輸入您的姓名時按**Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-195">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="9b8d2-196">由於您指定的`name`條件或`null`<xref:System.String.Empty?displayProperty=nameWithType>已滿足，因此程式執行在到達中斷點時和`Console.WriteLine`方法執行之前停止。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-196">Because the condition you specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="9b8d2-197">選擇 **"區域變數"** 視窗，該視窗顯示當前執行方法的區域變數的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-197">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="9b8d2-198">在這種情況下，`Main`是當前執行的方法。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-198">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="9b8d2-199">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-199">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="9b8d2-200">通過在 **"立即"** 視窗中輸入以下語句並按**Enter**， 確認該值是空字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-200">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="9b8d2-201">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-201">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. <span data-ttu-id="9b8d2-203">選取工具列上的 [繼續]\*\*\*\* 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-203">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="9b8d2-204">按任意鍵關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-204">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="9b8d2-205">按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點]\*\*\*\* 功能表項目，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-205">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>

---
## <a name="step-through-a-program"></a><span data-ttu-id="9b8d2-206">單一步驟程式</span><span class="sxs-lookup"><span data-stu-id="9b8d2-206">Step through a program</span></span>

<span data-ttu-id="9b8d2-207">Visual Studio 也可讓您逐行執行程式並監視其執行情況。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-207">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="9b8d2-208">通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-208">Ordinarily, you'd set a breakpoint and use this feature to follow program flow through a small part of your program code.</span></span> <span data-ttu-id="9b8d2-209">由於程式很小，您可以單一步驟整個程式：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-209">Since your program is small, you can step through the entire program:</span></span>

# <a name="c"></a>[<span data-ttu-id="9b8d2-210">C#</span><span class="sxs-lookup"><span data-stu-id="9b8d2-210">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="9b8d2-211">在功能表列上，選擇 **"調試** > **步驟進入"** 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-211">On the menu bar, choose **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-212">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-212">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="9b8d2-214">此時，"**區域變數"** 視窗顯示程式只定義了一個變數`args`。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-214">At this point, the **Locals** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="9b8d2-215">由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-215">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="9b8d2-216">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-216">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="9b8d2-217">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-217">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-218">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-218">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="9b8d2-219">如圖所示，執行最後一個語句和此語句之間的代碼不到一毫秒。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-219">As the image shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="9b8d2-220">`args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-220">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. <span data-ttu-id="9b8d2-222">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-222">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-223">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-223">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="9b8d2-224">**"區域變數"** 視窗`name`顯示`null`的是 ，主控台視窗顯示字串"您的姓名是什麼？</span><span class="sxs-lookup"><span data-stu-id="9b8d2-224">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="9b8d2-225">通過在主控台視窗中輸入字串並按**Enter**回應提示。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-225">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="9b8d2-226">主控台無回應，您輸入的字串不顯示在主控台視窗中，但<xref:System.Console.ReadLine%2A?displayProperty=nameWithType>該方法仍將捕獲您的輸入。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-226">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="9b8d2-227">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-227">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-228">Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-228">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="9b8d2-229">**"區域變數"** 視窗顯示對<xref:System.Console.ReadLine%2A?displayProperty=nameWithType>方法的調用返回的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-229">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b8d2-230">主控台視窗還顯示您在提示符下輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-230">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="9b8d2-231">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-231">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-232">**"區域變數"** 視窗顯示從`date`<xref:System.DateTime.Now?displayProperty=nameWithType>屬性分配後變數的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-232">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9b8d2-233">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-233">The console window is unchanged.</span></span>

1. <span data-ttu-id="9b8d2-234">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-234">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-235">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-235">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b8d2-236">主控台視窗顯示格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-236">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="9b8d2-237">選擇**調試** > **步進或**按**Shift**+**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-237">Select **Debug** > **Step Out** or press **Shift**+**F11**.</span></span> <span data-ttu-id="9b8d2-238">這會停止逐步執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-238">This stops step-by-step execution.</span></span> <span data-ttu-id="9b8d2-239">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-239">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="9b8d2-240">按任意鍵關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-240">Press any key to close the console window and stop debugging.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="9b8d2-241">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b8d2-241">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="9b8d2-242">在功能表列上，選擇 **"調試** > **步驟進入"** 或按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-242">On the menu bar, choose **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-243">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-243">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="9b8d2-245">此時，"**區域變數"** 視窗顯示程式只定義了一個變數`args`。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-245">At this point, the **Locals** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="9b8d2-246">由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-246">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="9b8d2-247">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-247">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="9b8d2-248">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-248">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-249">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-249">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="9b8d2-250">如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-250">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="9b8d2-251">`args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-251">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="9b8d2-253">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-253">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-254">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-254">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="9b8d2-255">**"區域變數"** 視窗`name`顯示`Nothing`的是 ，主控台視窗顯示字串"您的姓名是什麼？</span><span class="sxs-lookup"><span data-stu-id="9b8d2-255">The **Locals** window shows that `name` is `Nothing`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="9b8d2-256">通過在主控台視窗中輸入字串並按**Enter**回應提示。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-256">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="9b8d2-257">主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會擷取您的輸入。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-257">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="9b8d2-258">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-258">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-259">Visual Studio 會醒目提示包含 `currentDate` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-259">Visual Studio highlights the statement that includes the `currentDate` variable assignment.</span></span> <span data-ttu-id="9b8d2-260">**"區域變數"** 視窗顯示對<xref:System.Console.ReadLine%2A?displayProperty=nameWithType>方法的調用返回的值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-260">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b8d2-261">主控台視窗也會顯示在主控台提示輸入時輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-261">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="9b8d2-262">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-262">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-263">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-263">The console window is unchanged.</span></span>

1. <span data-ttu-id="9b8d2-264">選擇 **"調試** > **步驟"或**按**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-264">Select **Debug** > **Step Into** or press **F11**.</span></span> <span data-ttu-id="9b8d2-265">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-265">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b8d2-266">主控台視窗顯示格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-266">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="9b8d2-267">選擇**調試** > **步進或**按**Shift**+**F11**。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-267">Select **Debug** > **Step Out** or press **Shift**+**F11**.</span></span> <span data-ttu-id="9b8d2-268">這會停止逐步執行。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-268">This stops step-by-step execution.</span></span> <span data-ttu-id="9b8d2-269">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-269">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="9b8d2-270">按任意鍵關閉主控台視窗並停止調試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-270">Press any key to close the console window and stop debugging.</span></span>

---

## <a name="build-a-release-version"></a><span data-ttu-id="9b8d2-271">構建發佈版本</span><span class="sxs-lookup"><span data-stu-id="9b8d2-271">Build a Release version</span></span>

<span data-ttu-id="9b8d2-272">測試應用程式的調試版本後，還應編譯和測試發佈版本。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-272">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="9b8d2-273">發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-273">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="9b8d2-274">例如，旨在提高性能的編譯器優化可以在多執行緒應用程式中創建競爭條件。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-274">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="9b8d2-275">若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯]\*\*\*\* 變更為 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-275">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="9b8d2-277">當您按**F5**或從 **"生成"** 功能表中選擇 **"生成解決方案**"時，Visual Studio 會編譯應用程式的發佈版本。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-277">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="9b8d2-278">您可以像測試版本一樣對其進行測試。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-278">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b8d2-279">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9b8d2-279">Next steps</span></span>

<span data-ttu-id="9b8d2-280">調試應用程式後，下一步是發佈應用程式的可部署版本。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-280">Once you've debugged your application, the next step is to publish a deployable version of the app.</span></span> <span data-ttu-id="9b8d2-281">有關如何執行此操作的資訊，請參閱使用 Visual [Studio 發佈您的 .NET 核心 Hello World 應用程式](publishing-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-281">For information on how to do this, see [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>
