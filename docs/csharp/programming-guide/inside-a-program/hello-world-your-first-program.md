---
title: "Hello World -- 您的第一個程式 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1b6511394e69edd344c4f4a1bbc9da549a1a2a17
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="e1596-102">Hello World -- 您的第一個程式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e1596-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="e1596-103">下列程序會建立 C# 版本的傳統 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e1596-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="e1596-104">程式。</span><span class="sxs-lookup"><span data-stu-id="e1596-104">program.</span></span> <span data-ttu-id="e1596-105">此程式會顯示字串 `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="e1596-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="e1596-106">如需更多的介紹性概念範例，請參閱 [Visual C# 和 Visual Basic 使用者入門](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e1596-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="e1596-107">建立並執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="e1596-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="e1596-108">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e1596-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e1596-109">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="e1596-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="e1596-110">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e1596-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e1596-111">依序展開 [已安裝]、[範本] 和 [Visual C#]，然後選擇 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="e1596-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="e1596-112">在 [名稱] 文字方塊中指定專案名稱，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e1596-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="e1596-113">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="e1596-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="e1596-114">如果 [程式碼編輯器] 中未開啟 Program.cs，請在方案總管中開啟 **Program.cs** 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="e1596-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="e1596-115">以下列程式碼取代 Program.cs 的內容。</span><span class="sxs-lookup"><span data-stu-id="e1596-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  <span data-ttu-id="e1596-116">選擇 F5 鍵執行執行專案。</span><span class="sxs-lookup"><span data-stu-id="e1596-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="e1596-117">包含 `Hello World!` 一行的命令提示字元視窗隨即出現</span><span class="sxs-lookup"><span data-stu-id="e1596-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="e1596-118">接下來，會檢查此程式的重要部分。</span><span class="sxs-lookup"><span data-stu-id="e1596-118">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="e1596-119">註解</span><span class="sxs-lookup"><span data-stu-id="e1596-119">Comments</span></span>  
 <span data-ttu-id="e1596-120">第一行包含註解。</span><span class="sxs-lookup"><span data-stu-id="e1596-120">The first line contains a comment.</span></span> <span data-ttu-id="e1596-121">字元 `//` 會將該行的其餘部分轉換成註解。</span><span class="sxs-lookup"><span data-stu-id="e1596-121">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 <span data-ttu-id="e1596-122">您也可以用 `/*` 和 `*/` 字元括住它，註解文字區塊。</span><span class="sxs-lookup"><span data-stu-id="e1596-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="e1596-123">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="e1596-123">This is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a><span data-ttu-id="e1596-124">Main 方法</span><span class="sxs-lookup"><span data-stu-id="e1596-124">Main Method</span></span>  
 <span data-ttu-id="e1596-125">C# 主控台應用程式必須包含 `Main` 方法，控制項在此開始和結束。</span><span class="sxs-lookup"><span data-stu-id="e1596-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="e1596-126">`Main` 方法是您建立物件和執行其他方法的所在。</span><span class="sxs-lookup"><span data-stu-id="e1596-126">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="e1596-127">`Main` 方法是位於類別或結構內的[靜態](../../../csharp/language-reference/keywords/static.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e1596-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="e1596-128">在上一個 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e1596-128">In the previous "Hello World!"</span></span> <span data-ttu-id="e1596-129">範例中，它位於名為 `Hello` 的類別中。</span><span class="sxs-lookup"><span data-stu-id="e1596-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="e1596-130">您可以下列方式之一宣告 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="e1596-130">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="e1596-131">它會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="e1596-131">It can return `void`.</span></span>  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   <span data-ttu-id="e1596-132">它也可以傳回整數。</span><span class="sxs-lookup"><span data-stu-id="e1596-132">It can also return an integer.</span></span>  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   <span data-ttu-id="e1596-133">使用任一傳回型別，它可以接受引數。</span><span class="sxs-lookup"><span data-stu-id="e1596-133">With either of the return types, it can take arguments.</span></span>  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     <span data-ttu-id="e1596-134">-或-</span><span class="sxs-lookup"><span data-stu-id="e1596-134">-or-</span></span>  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 <span data-ttu-id="e1596-135">`Main` 方法的參數 `args`，是包含用來叫用程式的命令列引數的 `string` 陣列。</span><span class="sxs-lookup"><span data-stu-id="e1596-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="e1596-136">不像在 C++ 中，陣列不包含可執行檔 (exe) 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e1596-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="e1596-137">如需如何使用命令列引數的詳細資訊，請參閱 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)以及[如何：使用命令列建立和使用組件](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)。</span><span class="sxs-lookup"><span data-stu-id="e1596-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="e1596-138">在 `Main` 方法的結尾呼叫 <xref:System.Console.ReadKey%2A>，可讓您在按下 F5 以於偵錯模式中執行程式時，防止主控台視窗在您有機會讀取輸出之前關閉。</span><span class="sxs-lookup"><span data-stu-id="e1596-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="e1596-139">輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="e1596-139">Input and Output</span></span>  
 <span data-ttu-id="e1596-140">C# 程式通常會使用 .NET Framework 執行階段程式庫所提供的輸入/輸出服務。</span><span class="sxs-lookup"><span data-stu-id="e1596-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="e1596-141">陳述式 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e1596-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="e1596-142">這是執行階段程式庫中 <xref:System.Console> 類別的其中一個輸出方法。</span><span class="sxs-lookup"><span data-stu-id="e1596-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="e1596-143">它會在標準輸出資料流中顯示其字串參數，後面接著新行。</span><span class="sxs-lookup"><span data-stu-id="e1596-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="e1596-144">其他 <xref:System.Console> 方法可供不同的輸入和輸出作業使用。</span><span class="sxs-lookup"><span data-stu-id="e1596-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="e1596-145">如果您在程式開始處包含 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而不必完整限定它們。</span><span class="sxs-lookup"><span data-stu-id="e1596-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="e1596-146">例如，您可以呼叫 `Console.WriteLine` 而不用呼叫 `System.Console.WriteLine`：</span><span class="sxs-lookup"><span data-stu-id="e1596-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 <span data-ttu-id="e1596-147">如需輸入/輸出方法的詳細資訊，請參閱 <xref:System.IO>。</span><span class="sxs-lookup"><span data-stu-id="e1596-147">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="e1596-148">命令列編譯和執行</span><span class="sxs-lookup"><span data-stu-id="e1596-148">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="e1596-149">您可以編譯 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e1596-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="e1596-150">程式，使用命令列而不是使用 Visual Studio 整合式開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="e1596-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="e1596-151">從命令提示字元編譯與執行</span><span class="sxs-lookup"><span data-stu-id="e1596-151">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="e1596-152">將前面程序的程式碼貼入任何文字編輯器，再將檔案儲存為文字檔案。</span><span class="sxs-lookup"><span data-stu-id="e1596-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="e1596-153">將檔案命名為 `Hello.cs`。</span><span class="sxs-lookup"><span data-stu-id="e1596-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="e1596-154">C# 原始程式碼檔使用延伸模組 `.cs`。</span><span class="sxs-lookup"><span data-stu-id="e1596-154">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="e1596-155">執行下列步驟之一來開啟命令提示字元視窗︰</span><span class="sxs-lookup"><span data-stu-id="e1596-155">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="e1596-156">在 Windows 10 的 [開始] 功能表中搜尋 `Developer Command Prompt`，然後點選或選擇 [VS 2017 開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="e1596-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="e1596-157">[開發人員命令提示字元] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e1596-157">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="e1596-158">開啟 Windows 7 的 [開始] 功能表，展開最新版 Visual Studio 的資料夾，開啟 **Visual Studio Tools** 的捷徑功能表，然後選擇 [VS 2017 開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="e1596-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="e1596-159">[開發人員命令提示字元] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e1596-159">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="e1596-160">從標準的命令提示字元視窗啟用命令列組建。</span><span class="sxs-lookup"><span data-stu-id="e1596-160">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="e1596-161">請參閱[如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="e1596-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="e1596-162">在命令提示字元視窗中，巡覽至包含 `Hello.cs` 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e1596-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="e1596-163">輸入下列命令以編譯 `Hello.cs`。</span><span class="sxs-lookup"><span data-stu-id="e1596-163">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="e1596-164">如果您的程式沒有任何編譯錯誤，則會建立名為 `Hello.exe` 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e1596-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="e1596-165">在命令提示字元視窗中輸入下列命令，執行程式：</span><span class="sxs-lookup"><span data-stu-id="e1596-165">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="e1596-166">如需 C# 編譯器及其選項的詳細資訊，請參閱[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e1596-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1596-167">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1596-167">See Also</span></span>  
 [<span data-ttu-id="e1596-168">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e1596-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e1596-169">C# 程式內部</span><span class="sxs-lookup"><span data-stu-id="e1596-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="e1596-170">字串</span><span class="sxs-lookup"><span data-stu-id="e1596-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="e1596-171">\<paveover>C# 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="e1596-171">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [<span data-ttu-id="e1596-172">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e1596-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e1596-173">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="e1596-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="e1596-174">Visual C# 和 Visual Basic 使用者入門</span><span class="sxs-lookup"><span data-stu-id="e1596-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
