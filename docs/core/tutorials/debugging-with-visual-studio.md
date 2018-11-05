---
title: 使用 Visual Studio 2017 來為您的 C# 或 Visual Basic Hello World .NET Core 應用程式進行偵錯
description: 了解如何使用 Visual Studio 2017 對以 C# 或 Visual Basic 撰寫的 Hello World 應用程式進行偵錯。
author: BillWagner
ms.author: wiwagn
ms.date: 12/15/2017
ms.custom: vs-dotnet
ms.openlocfilehash: 53e4549f4790bc0756cd0ad0b903b3dc25d2f66a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200120"
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="59f7a-103">使用 Visual Studio 2017 針對您的 Hello World 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="59f7a-103">Debug your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="59f7a-104">截至目前為止，您已遵循[在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式](.\with-visual-studio.md)或[在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic Hello World 應用程式](vb-with-visual-studio.md)中的步驟，建立並執行簡單的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-104">So far, you've followed the steps in [Build a C# Hello World Application with .NET Core in Visual Studio 2017](.\with-visual-studio.md) or [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="59f7a-105">在您撰寫並編譯應用程式之後，便可以開始測試它。</span><span class="sxs-lookup"><span data-stu-id="59f7a-105">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="59f7a-106">Visual Studio 包含一組完整的偵錯工具，可供您在針對應用程式進行測試和疑難排解時使用。</span><span class="sxs-lookup"><span data-stu-id="59f7a-106">Visual Studio includes a comprehensive set of debugging tools that you can use when testing and troubleshooting your application.</span></span>

## <a name="debugging-in-debug-mode"></a><span data-ttu-id="59f7a-107">在偵錯模式下進行偵錯</span><span class="sxs-lookup"><span data-stu-id="59f7a-107">Debugging in Debug mode</span></span>

<span data-ttu-id="59f7a-108">[偵錯] 和 [發行] 是 Visual Studio 其中兩個預設的組建組態。</span><span class="sxs-lookup"><span data-stu-id="59f7a-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="59f7a-109">目前的組建組態會顯示在工具列上。</span><span class="sxs-lookup"><span data-stu-id="59f7a-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="59f7a-110">下列工具列影像顯示 Visual Studio 已設定為在 [偵錯] 模式下編譯您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-110">The following toolbar image shows that Visual Studio is configured to compile your application in **Debug** mode.</span></span>

   ![Visual Studio 工具列](./media/debugging-with-visual-studio/toolbar1.png)

<span data-ttu-id="59f7a-112">您應該一律從在 [偵錯] 模式下進行程式測試開始。</span><span class="sxs-lookup"><span data-stu-id="59f7a-112">You should always begin by testing your program in Debug mode.</span></span> <span data-ttu-id="59f7a-113">[偵錯] 模式會關閉大多數的編譯器最佳化，並可在組置程序期間提供更豐富的資訊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-113">Debug mode turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="setting-a-breakpoint"></a><span data-ttu-id="59f7a-114">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="59f7a-114">Setting a breakpoint</span></span>

<span data-ttu-id="59f7a-115">請在 [偵錯] 模式下執行程式並嘗試幾個偵錯功能：</span><span class="sxs-lookup"><span data-stu-id="59f7a-115">Run your program in Debug mode and try a few debugging features:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="59f7a-116">C#</span><span class="sxs-lookup"><span data-stu-id="59f7a-116">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="59f7a-117">「中斷點」會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-117">A *breakpoint* temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span> 

   <span data-ttu-id="59f7a-118">在程式碼視窗左邊界中按一下顯示 `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` 的這一行，以將中斷點設定在該行，或在已選取該行的情況下選擇 [偵錯]  >  [切換中斷點] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="59f7a-118">Set a breakpoint on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="59f7a-119">如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-119">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/setbreakpoint.png)

1. <span data-ttu-id="59f7a-121">在 [偵錯] 模式下執行程式，方法是選取工具列上帶有綠色箭號的 **HelloWorld** 按鈕、按 F5，或選擇 [偵錯]  >  [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="59f7a-121">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing F5, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="59f7a-122">當程式提示輸入名稱時，在主控台視窗中輸入字串，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="59f7a-122">Enter a string in the console window when the program prompts for a name and press Enter.</span></span>

1. <span data-ttu-id="59f7a-123">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-123">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="59f7a-124">[自動變數] 視窗會顯示目前行附近所使用變數的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-124">The **Autos** window displays the values of variables that are used around the current line.</span></span> <span data-ttu-id="59f7a-125">[區域變數] 視窗 (按一下 [區域變數] 索引標籤即可檢視) 會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-125">The **Locals** window (which you can view by clicking the **Locals** tab) displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio Application Insights](./media/debugging-with-visual-studio/break.png)

1. <span data-ttu-id="59f7a-127">您可以變更變數的值，以了解它會如何影響我們的程式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-127">You can change the value of the variables to see how it affects your program.</span></span> <span data-ttu-id="59f7a-128">如果看不到 [即時運算視窗]，請選擇 [偵錯]  >  [視窗]  >  [即時運算] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="59f7a-128">If the **Immediate Window** is not visible, display it by choosing the **Debug** > **Windows** > **Immediate** menu item.</span></span> <span data-ttu-id="59f7a-129">[即時運算視窗] 可讓您與正在進行偵錯的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="59f7a-129">The **Immediate Window** lets you interact with the application you're debugging.</span></span>

1. <span data-ttu-id="59f7a-130">您可以藉由互動方式變更變數的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-130">You can interactively change the values of variables.</span></span> <span data-ttu-id="59f7a-131">在 [即時運算視窗] 中輸入`name = "Gracie"`，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-131">Enter `name = "Gracie"` in the **Immediate Window** and press the Enter key.</span></span>

1. <span data-ttu-id="59f7a-132">在 [即時運算視窗] 中輸入 `date = new DateTime(2016,11,01,11,59,00)`，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-132">Enter `date = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

   <span data-ttu-id="59f7a-133">此 [即時運算視窗] 會顯示字串變數的值和 <xref:System.DateTime> 值的屬性。</span><span class="sxs-lookup"><span data-stu-id="59f7a-133">The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="59f7a-134">此外，[自動變數] 和 [區域變數] 視窗中變數的值也會更新。</span><span class="sxs-lookup"><span data-stu-id="59f7a-134">In addition, the value of the variables is updated in the **Autos** and **Locals** windows.</span></span>

   ![[自動變數] 視窗和 [即時運算] 視窗](./media/debugging-with-visual-studio/autosimmediate.png)

1. <span data-ttu-id="59f7a-136">選取工具列中的 [繼續] 按鈕，或選取 [偵錯]  >  [繼續] 功能表項目，以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-136">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="59f7a-137">主控台視窗中顯示的值會與您在 [即時運算視窗] 中所做的變更對應。</span><span class="sxs-lookup"><span data-stu-id="59f7a-137">The values displayed in the console window correspond to the changes you made in the **Immediate Window**.</span></span>

   ![主控台視窗顯示在 [What is your name?] 提示字元上的輸入值 Jack，後面接著 Hello Gracie ，時間：11/1/2016 上午 11:59](./media/debugging-with-visual-studio/changed.png)

1. <span data-ttu-id="59f7a-139">按任意鍵以結束應用程式並結束 [偵錯] 模式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-139">Press any key to exit the application and end Debug mode.</span></span>
# <a name="visual-basictabvb"></a>[<span data-ttu-id="59f7a-140">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59f7a-140">Visual Basic</span></span>](#tab/vb)
1. <span data-ttu-id="59f7a-141">「中斷點」會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-141">A *breakpoint* temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span> 

   <span data-ttu-id="59f7a-142">在程式碼視窗左邊界中按一下顯示 `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` 的這一行，以將中斷點設定在該行，或在已選取該行的情況下選擇 [偵錯]  >  [切換中斷點] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="59f7a-142">Set a breakpoint on the line that reads `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="59f7a-143">如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-143">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/vb-setbreakpoint.png)

1. <span data-ttu-id="59f7a-145">在 [偵錯] 模式下執行程式，方法是選取工具列上帶有綠色箭號的 **HelloWorld** 按鈕、按 F5，或選擇 [偵錯]  >  [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="59f7a-145">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing F5, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="59f7a-146">當程式提示輸入名稱時，在主控台視窗中輸入字串，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="59f7a-146">Enter a string in the console window when the program prompts for a name and press Enter.</span></span>

1. <span data-ttu-id="59f7a-147">程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-147">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="59f7a-148">[自動變數] 視窗會顯示目前行附近所使用變數的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-148">The **Autos** window displays the values of variables that are used around the current line.</span></span> <span data-ttu-id="59f7a-149">[區域變數] 視窗 (按一下 [區域變數] 索引標籤即可檢視) 會顯示目前正在執行的方法中所定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-149">The **Locals** window (which you can view by clicking the **Locals** tab) displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio Application Insights](./media/debugging-with-visual-studio/vb-break.png)

1. <span data-ttu-id="59f7a-151">您可以變更變數的值，以了解它會如何影響我們的程式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-151">You can change the value of the variables to see how it affects your program.</span></span> <span data-ttu-id="59f7a-152">如果看不到 [即時運算視窗]，請選擇 [偵錯]  >  [視窗]  >  [即時運算] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="59f7a-152">If the **Immediate Window** is not visible, display it by choosing the **Debug** > **Windows** > **Immediate** menu item.</span></span> <span data-ttu-id="59f7a-153">[即時運算視窗] 可讓您與正在進行偵錯的應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="59f7a-153">The **Immediate Window** lets you interact with the application you're debugging.</span></span>

1. <span data-ttu-id="59f7a-154">您可以藉由互動方式變更變數的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-154">You can interactively change the values of variables.</span></span> <span data-ttu-id="59f7a-155">在 [即時運算視窗] 中輸入`name = "Gracie"`，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-155">Enter `name = "Gracie"` in the **Immediate Window** and press the Enter key.</span></span>

1. <span data-ttu-id="59f7a-156">在 [即時運算視窗] 中輸入`currentDate = new DateTime(2016,11,01,11,59,00)`，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-156">Enter `currentDate = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

1. <span data-ttu-id="59f7a-157">選取工具列中的 [繼續] 按鈕，或選取 [偵錯]  >  [繼續] 功能表項目，以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-157">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="59f7a-158">主控台視窗中顯示的值會與您在 [即時運算視窗] 中所做的變更對應。</span><span class="sxs-lookup"><span data-stu-id="59f7a-158">The values displayed in the console window correspond to the changes you made in the **Immediate Window**.</span></span>

   ![顯示在即時運算視窗中所輸入變更值的主控台視窗](./media/debugging-with-visual-studio/changed.png)

1. <span data-ttu-id="59f7a-160">按任意鍵以結束應用程式並結束 [偵錯] 模式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-160">Press any key to exit the application and end Debug mode.</span></span>
---

## <a name="setting-a-conditional-breakpoint"></a><span data-ttu-id="59f7a-161">設定條件中斷點</span><span class="sxs-lookup"><span data-stu-id="59f7a-161">Setting a conditional breakpoint</span></span>

<span data-ttu-id="59f7a-162">您的程式會顯示使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-162">Your program displays the string that the user enters.</span></span> <span data-ttu-id="59f7a-163">如果使用者未進行任何輸入時，會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="59f7a-163">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="59f7a-164">您可以利用有用的「條件中斷點」偵錯功能來測試此情況，以在一或多個條件成立時中斷程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-164">You can test this with a useful debugging feature, the *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="59f7a-165">若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="59f7a-165">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="59f7a-166">C#</span><span class="sxs-lookup"><span data-stu-id="59f7a-166">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="59f7a-167">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-167">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="59f7a-168">在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-168">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="59f7a-169">核取 [條件] 的方塊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-169">Check the box for **Conditions**.</span></span>

   ![中斷點設定面板](./media/debugging-with-visual-studio/breakpointsettings.png)

1. <span data-ttu-id="59f7a-171">對於 [條件運算式]，請以下列內容取代 "e.g. x == 5"：</span><span class="sxs-lookup"><span data-stu-id="59f7a-171">For the **Conditional Expression** replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="59f7a-172">您要測試程式碼的條件，`String.IsNullOrEmpty(name)` 方法呼叫是 `true`，因為「名稱」尚未指派值或其值為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="59f7a-172">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because *name* has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="59f7a-173">您可以指定一個「叫用次數」，以在陳述式執行次數達到指定的次數之前中斷程式執行；或是指定一個「篩選條件」，以根據執行緒識別碼、處理序名稱或執行緒名稱等屬性中斷應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-173">You can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="59f7a-174">選取 [關閉] 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-174">Select the **Close** button to close the dialog.</span></span>

1. <span data-ttu-id="59f7a-175">在 [偵錯] 模式下執行程式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-175">Run the program in Debug mode.</span></span>

1. <span data-ttu-id="59f7a-176">在主控台視窗中，於提示您輸入名稱時，按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-176">In the console window, press the Enter key when prompted to enter your name.</span></span>

1. <span data-ttu-id="59f7a-177">由於已經滿足我們指定的條件 (`name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>)，因此程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-177">Because the condition we specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="59f7a-178">選取 [區域變數] 視窗，此視窗會顯示目前正在執行之方法 (在您的程式中為 `Main` 方法) 的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-178">Select the **Locals** window, which shows the values of variables that are local to the currently executing method, which is the `Main` method in your program.</span></span> <span data-ttu-id="59f7a-179">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="59f7a-179">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="59f7a-180">請在 [即時運算視窗] 中輸入下列陳述式來確認此值是空字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-180">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="59f7a-181">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="59f7a-181">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true](./media/debugging-with-visual-studio/emptystring.png)

1. <span data-ttu-id="59f7a-183">選取工具列上的 [繼續] 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-183">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="59f7a-184">按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-184">Press any key to close the console window and exit Debug mode.</span></span>

1. <span data-ttu-id="59f7a-185">按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點] 功能表項目，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="59f7a-185">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>
# <a name="visual-basictabvb"></a>[<span data-ttu-id="59f7a-186">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59f7a-186">Visual Basic</span></span>](#tab/vb)
1. <span data-ttu-id="59f7a-187">在代表中斷點的紅點上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-187">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="59f7a-188">在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-188">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="59f7a-189">核取 [條件] 的方塊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-189">Check the box for **Conditions**.</span></span>

   ![中斷點設定面板](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="59f7a-191">對於 [條件運算式]，請以下列內容取代 "e.g. x == 5"：</span><span class="sxs-lookup"><span data-stu-id="59f7a-191">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="59f7a-192">您要測試程式碼的條件，`String.IsNullOrEmpty(name)` 方法呼叫是 `True`，因為「名稱」尚未指派值或其值為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="59f7a-192">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `True` either because *name* has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="59f7a-193">您可以指定一個「叫用次數」，以在陳述式執行次數達到指定的次數之前中斷程式執行；或是指定一個「篩選條件」，以根據執行緒識別碼、處理序名稱或執行緒名稱等屬性中斷應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-193">You can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="59f7a-194">選取 [關閉] 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="59f7a-194">Select the **Close** button to close the dialog.</span></span>

1. <span data-ttu-id="59f7a-195">在 [偵錯] 模式下執行程式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-195">Run the program in Debug mode.</span></span>

1. <span data-ttu-id="59f7a-196">在主控台視窗中，於提示您輸入名稱時，按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-196">In the console window, press the Enter key when prompted to enter your name.</span></span>

1. <span data-ttu-id="59f7a-197">由於已經滿足我們指定的條件 (`name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>)，因此程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-197">Because the condition we specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="59f7a-198">選取 [區域變數] 視窗，此視窗會顯示目前正在執行之方法 (在您的程式中為 `Main` 方法) 的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-198">Select the **Locals** window, which shows the values of variables that are local to the currently executing method, which is the `Main` method in your program.</span></span> <span data-ttu-id="59f7a-199">注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="59f7a-199">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="59f7a-200">請在 [即時運算視窗] 中輸入下列陳述式來確認此值是空字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-200">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="59f7a-201">結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="59f7a-201">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![[即時運算視窗] 在執行陳述式之後傳回值 true](./media/debugging-with-visual-studio/vb-emptystring.png)

1. <span data-ttu-id="59f7a-203">選取工具列上的 [繼續] 按鈕以繼續程式執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-203">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="59f7a-204">按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-204">Press any key to close the console window and exit Debug mode.</span></span>

1. <span data-ttu-id="59f7a-205">按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點] 功能表項目，以清除中斷點。</span><span class="sxs-lookup"><span data-stu-id="59f7a-205">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>
---
## <a name="stepping-through-a-program"></a><span data-ttu-id="59f7a-206">逐步執行程式</span><span class="sxs-lookup"><span data-stu-id="59f7a-206">Stepping through a program</span></span>

<span data-ttu-id="59f7a-207">Visual Studio 也可讓您逐行執行程式並監視其執行情況。</span><span class="sxs-lookup"><span data-stu-id="59f7a-207">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="59f7a-208">通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。</span><span class="sxs-lookup"><span data-stu-id="59f7a-208">Ordinarily, you'd set a breakpoint and use this feature to follow program flow through a small part of your program code.</span></span> <span data-ttu-id="59f7a-209">由於您的程式相當小，因此您可以透過執行下列操作將整個程式執行一遍：</span><span class="sxs-lookup"><span data-stu-id="59f7a-209">Since your program is small, you can step through the entire program by doing the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="59f7a-210">C#</span><span class="sxs-lookup"><span data-stu-id="59f7a-210">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="59f7a-211">在功能表列上，選擇 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-211">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-212">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="59f7a-212">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio 視窗](./media/debugging-with-visual-studio/stepinto1.png)

   <span data-ttu-id="59f7a-214">此時，[自動變數] 視窗會顯示您的程式只有定義一個變數 `args`。</span><span class="sxs-lookup"><span data-stu-id="59f7a-214">At this point, the **Autos** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="59f7a-215">由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="59f7a-215">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="59f7a-216">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="59f7a-216">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="59f7a-217">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-217">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-218">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-218">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="59f7a-219">如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。</span><span class="sxs-lookup"><span data-stu-id="59f7a-219">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="59f7a-220">`args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。</span><span class="sxs-lookup"><span data-stu-id="59f7a-220">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio 視窗](./media/debugging-with-visual-studio/stepinto2.png)

1. <span data-ttu-id="59f7a-222">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-222">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-223">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-223">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="59f7a-224">[自動變數] 視窗會顯示 `name` 是 `null`，而主控台視窗則會顯示 "What is your name?" 字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-224">The **Autos** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="59f7a-225">在主控台視窗中輸入一個字串並按 Enter，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="59f7a-225">Respond to the prompt by entering a string in the console window and pressing Enter.</span></span> <span data-ttu-id="59f7a-226">主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會擷取您的輸入。</span><span class="sxs-lookup"><span data-stu-id="59f7a-226">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="59f7a-227">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-227">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-228">Visual Studio 會醒目提示包含 `date` (在 C# 中) 或 `currentDate` (在 Visual Basic 中) 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-228">Visual Studio highlights the statement that includes the `date` (in C#) or `currentDate` (in Visual Basic) variable assignment.</span></span> <span data-ttu-id="59f7a-229">[自動變數] 視窗會顯示 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性值，以及對 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法進行呼叫所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-229">The **Autos** window shows the <xref:System.DateTime.Now?displayProperty=nameWithType> property value and the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59f7a-230">主控台視窗也會顯示在主控台提示輸入時輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-230">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="59f7a-231">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-231">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-232">[自動變數] 視窗現在會顯示從 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性指派之後的 `date` 變數值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-232">The **Autos** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="59f7a-233">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="59f7a-233">The console window is unchanged.</span></span>

1. <span data-ttu-id="59f7a-234">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-234">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-235">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="59f7a-235">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59f7a-236">`date` (或 `currentDate`) 和 `name` 變數的值會顯示在 [自動變數] 視窗中，而主控台視窗則會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-236">The values of the `date` (or `currentDate`) and `name` variables appear in the **Autos** window, and the console window displays the formatted string.</span></span>

1. <span data-ttu-id="59f7a-237">選取 [偵錯]  >  [跳離函式]，或按 Shift 和 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-237">Select **Debug** > **Step Out** or press Shift and the F11 key.</span></span> <span data-ttu-id="59f7a-238">這會停止逐步執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-238">This stops step-by-step execution.</span></span> <span data-ttu-id="59f7a-239">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-239">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="59f7a-240">按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-240">Press any key to close the console window and exit Debug mode.</span></span>
# <a name="visual-basictabvb"></a>[<span data-ttu-id="59f7a-241">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59f7a-241">Visual Basic</span></span>](#tab/vb)
1. <span data-ttu-id="59f7a-242">在功能表列上，選擇 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-242">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-243">Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。</span><span class="sxs-lookup"><span data-stu-id="59f7a-243">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio 視窗](./media/debugging-with-visual-studio/vb-stepinto1.png)

   <span data-ttu-id="59f7a-245">此時，因為您尚未將任何命令列引數傳遞至程式，[自動變數] 視窗顯示的 `args` 變數值是空白的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="59f7a-245">At this point, because you haven't passed any command-line arguments to the program, the **Autos** window shows that the value of the `args` variable is an empty string array.</span></span> <span data-ttu-id="59f7a-246">此外，Visual Studio 已開啟一個空白主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="59f7a-246">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="59f7a-247">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-247">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-248">Visual Studio 現在會醒目提示要執行的下一行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-248">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="59f7a-249">如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。</span><span class="sxs-lookup"><span data-stu-id="59f7a-249">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="59f7a-250">`args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。</span><span class="sxs-lookup"><span data-stu-id="59f7a-250">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio 視窗](./media/debugging-with-visual-studio/vb-stepinto2.png)

1. <span data-ttu-id="59f7a-252">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-252">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-253">Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-253">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="59f7a-254">[自動變數] 視窗會顯示 `name` 是 `Nothing`，而主控台視窗則會顯示 "What is your name?" 字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-254">The **Autos** window shows that `name` is `Nothing`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="59f7a-255">在主控台視窗中輸入一個字串並按 Enter，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="59f7a-255">Respond to the prompt by entering a string in the console window and pressing Enter.</span></span> <span data-ttu-id="59f7a-256">主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會擷取您的輸入。</span><span class="sxs-lookup"><span data-stu-id="59f7a-256">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="59f7a-257">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-257">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-258">Visual Studio 會醒目提示包含 `date` (在 C# 中) 或 `currentDate` (在 Visual Basic 中) 變數指派的陳述式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-258">Visual Studio highlights the statement that includes the `date` (in C#) or `currentDate` (in Visual Basic) variable assignment.</span></span> <span data-ttu-id="59f7a-259">[自動變數] 視窗會顯示 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性值，以及對 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法進行呼叫所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-259">The **Autos** window shows the <xref:System.DateTime.Now?displayProperty=nameWithType> property value and the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59f7a-260">主控台視窗也會顯示在主控台提示輸入時輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-260">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="59f7a-261">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-261">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-262">[自動變數] 視窗現在會顯示從 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性指派之後的 `date` 變數值。</span><span class="sxs-lookup"><span data-stu-id="59f7a-262">The **Autos** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="59f7a-263">主控台視窗沒有變更。</span><span class="sxs-lookup"><span data-stu-id="59f7a-263">The console window is unchanged.</span></span>

1. <span data-ttu-id="59f7a-264">選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-264">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="59f7a-265">Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="59f7a-265">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59f7a-266">`date` (或 `currentDate`) 和 `name` 變數的值會顯示在 [自動變數] 視窗中，而主控台視窗則會顯示已格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="59f7a-266">The values of the `date` (or `currentDate`) and `name` variables appear in the **Autos** window, and the console window displays the formatted string.</span></span>

1. <span data-ttu-id="59f7a-267">選取 [偵錯]  >  [跳離函式]，或按 Shift 和 F11 鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-267">Select **Debug** > **Step Out** or press Shift and the F11 key.</span></span> <span data-ttu-id="59f7a-268">這會停止逐步執行。</span><span class="sxs-lookup"><span data-stu-id="59f7a-268">This stops step-by-step execution.</span></span> <span data-ttu-id="59f7a-269">主控台視窗會顯示訊息並等候您按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="59f7a-269">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="59f7a-270">按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。</span><span class="sxs-lookup"><span data-stu-id="59f7a-270">Press any key to close the console window and exit Debug mode.</span></span>
---

## <a name="building-a-release-version"></a><span data-ttu-id="59f7a-271">組置發行版本</span><span class="sxs-lookup"><span data-stu-id="59f7a-271">Building a Release version</span></span>

<span data-ttu-id="59f7a-272">在對應用程式偵錯組建進行測試之後，您還應該編譯和測試發行版本。</span><span class="sxs-lookup"><span data-stu-id="59f7a-272">Once you've tested the Debug build of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="59f7a-273">發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="59f7a-273">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="59f7a-274">例如，設計來提升效能的編譯器最佳化可能會在非同步或多執行緒應用程式中，建立競爭條件。</span><span class="sxs-lookup"><span data-stu-id="59f7a-274">For example, compiler optimizations that are designed to improve performance can create race conditions in asynchronous or multithreaded applications.</span></span>

<span data-ttu-id="59f7a-275">若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="59f7a-275">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![Image](./media/debugging-with-visual-studio/toolbar2.png)

<span data-ttu-id="59f7a-277">當您按 F5 或從 [組建] 功能表中選擇 [組置方案] 時，Visual Studio 就會編譯您主控台應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="59f7a-277">When you press F5 or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of your console application.</span></span> <span data-ttu-id="59f7a-278">您可以測試該版本，就像您對應用程式的偵錯版本所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="59f7a-278">You can test it as you did the Debug version of the application.</span></span>

<span data-ttu-id="59f7a-279">完成應用程式偵錯之後，下一個步驟就是發行可部署的應用程式版本。</span><span class="sxs-lookup"><span data-stu-id="59f7a-279">Once you've finished debugging your application, the next step is to publish a deployable version of your application.</span></span> <span data-ttu-id="59f7a-280">如需如何執行此操作的資訊，請參閱[使用 Visual Studio 2017 發佈 Hello World 應用程式](./publishing-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="59f7a-280">For information on how to do this, see [Publish the Hello World application with Visual Studio 2017](./publishing-with-visual-studio.md).</span></span>
