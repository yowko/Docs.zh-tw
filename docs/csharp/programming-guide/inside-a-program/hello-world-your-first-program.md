---
title: "Hello World -- 您的第一個程式 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
dev_langs:
- CSharp
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: b7cb84362c96dac50ae5136334138b55ed1ce00b
ms.openlocfilehash: 03891f83885cf41ab157ebd78ef7e72767b4b163
ms.contentlocale: zh-tw
ms.lasthandoff: 07/31/2017

---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="d5196-102">Hello World -- 您的第一個程式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d5196-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="d5196-103">下列程序會建立 C# 版本的傳統 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="d5196-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="d5196-104">程式。</span><span class="sxs-lookup"><span data-stu-id="d5196-104">program.</span></span> <span data-ttu-id="d5196-105">此程式會顯示字串 `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="d5196-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="d5196-106">如需更多的介紹性概念範例，請參閱 [Visual C# 和 Visual Basic 使用者入門](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="d5196-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="d5196-107">建立並執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d5196-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="d5196-108">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d5196-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="d5196-109">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="d5196-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="d5196-110">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d5196-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d5196-111">依序展開 [已安裝]、[範本] 和 [Visual C#]，然後選擇 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="d5196-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="d5196-112">在 [名稱] 文字方塊中指定專案名稱，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d5196-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="d5196-113">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="d5196-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="d5196-114">如果 [程式碼編輯器] 中未開啟 Program.cs，請在方案總管中開啟 **Program.cs** 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="d5196-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="d5196-115">以下列程式碼取代 Program.cs 的內容。</span><span class="sxs-lookup"><span data-stu-id="d5196-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     <span data-ttu-id="d5196-116">[!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-116">[!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]</span></span>  
  
7.  <span data-ttu-id="d5196-117">選擇 F5 鍵執行執行專案。</span><span class="sxs-lookup"><span data-stu-id="d5196-117">Choose the F5 key to run the project.</span></span> <span data-ttu-id="d5196-118">包含 `Hello World!` 一行的命令提示字元視窗隨即出現</span><span class="sxs-lookup"><span data-stu-id="d5196-118">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="d5196-119">接下來，會檢查此程式的重要部分。</span><span class="sxs-lookup"><span data-stu-id="d5196-119">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="d5196-120">註解</span><span class="sxs-lookup"><span data-stu-id="d5196-120">Comments</span></span>  
 <span data-ttu-id="d5196-121">第一行包含註解。</span><span class="sxs-lookup"><span data-stu-id="d5196-121">The first line contains a comment.</span></span> <span data-ttu-id="d5196-122">字元 `//` 會將該行的其餘部分轉換成註解。</span><span class="sxs-lookup"><span data-stu-id="d5196-122">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 <span data-ttu-id="d5196-123">[!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-123">[!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]</span></span>  
  
 <span data-ttu-id="d5196-124">您也可以用 `/*` 和 `*/` 字元括住它，註解文字區塊。</span><span class="sxs-lookup"><span data-stu-id="d5196-124">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="d5196-125">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="d5196-125">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="d5196-126">[!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-126">[!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]</span></span>  
  
## <a name="main-method"></a><span data-ttu-id="d5196-127">Main 方法</span><span class="sxs-lookup"><span data-stu-id="d5196-127">Main Method</span></span>  
 <span data-ttu-id="d5196-128">C# 主控台應用程式必須包含 `Main` 方法，控制項在此開始和結束。</span><span class="sxs-lookup"><span data-stu-id="d5196-128">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="d5196-129">`Main` 方法是您建立物件和執行其他方法的所在。</span><span class="sxs-lookup"><span data-stu-id="d5196-129">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="d5196-130">`Main` 方法是位於類別或結構內的[靜態](../../../csharp/language-reference/keywords/static.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d5196-130">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="d5196-131">在上一個 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="d5196-131">In the previous "Hello World!"</span></span> <span data-ttu-id="d5196-132">範例中，它位於名為 `Hello` 的類別中。</span><span class="sxs-lookup"><span data-stu-id="d5196-132">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="d5196-133">您可以下列方式之一宣告 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="d5196-133">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="d5196-134">它會傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="d5196-134">It can return `void`.</span></span>  
  
     <span data-ttu-id="d5196-135">[!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-135">[!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]</span></span>  
  
-   <span data-ttu-id="d5196-136">它也可以傳回整數。</span><span class="sxs-lookup"><span data-stu-id="d5196-136">It can also return an integer.</span></span>  
  
     <span data-ttu-id="d5196-137">[!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-137">[!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]</span></span>  
  
-   <span data-ttu-id="d5196-138">使用任一傳回型別，它可以接受引數。</span><span class="sxs-lookup"><span data-stu-id="d5196-138">With either of the return types, it can take arguments.</span></span>  
  
     <span data-ttu-id="d5196-139">[!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-139">[!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]</span></span>  
  
     <span data-ttu-id="d5196-140">-或-</span><span class="sxs-lookup"><span data-stu-id="d5196-140">-or-</span></span>  
  
     <span data-ttu-id="d5196-141">[!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-141">[!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]</span></span>  
  
 <span data-ttu-id="d5196-142">`Main` 方法的參數 `args`，是包含用來叫用程式的命令列引數的 `string` 陣列。</span><span class="sxs-lookup"><span data-stu-id="d5196-142">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="d5196-143">不像在 C++ 中，陣列不包含可執行檔 (exe) 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d5196-143">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="d5196-144">如需如何使用命令列引數的詳細資訊，請參閱 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)以及[如何：使用命令列建立和使用組件](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)。</span><span class="sxs-lookup"><span data-stu-id="d5196-144">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="d5196-145">在 `Main` 方法的結尾呼叫 <xref:System.Console.ReadKey%2A>，可讓您在按下 F5 以於偵錯模式中執行程式時，防止主控台視窗在您有機會讀取輸出之前關閉。</span><span class="sxs-lookup"><span data-stu-id="d5196-145">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="d5196-146">輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="d5196-146">Input and Output</span></span>  
 <span data-ttu-id="d5196-147">C# 程式通常會使用 .NET Framework 執行階段程式庫所提供的輸入/輸出服務。</span><span class="sxs-lookup"><span data-stu-id="d5196-147">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="d5196-148">陳述式 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d5196-148">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="d5196-149">這是執行階段程式庫中 <xref:System.Console> 類別的其中一個輸出方法。</span><span class="sxs-lookup"><span data-stu-id="d5196-149">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="d5196-150">它會在標準輸出資料流中顯示其字串參數，後面接著新行。</span><span class="sxs-lookup"><span data-stu-id="d5196-150">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="d5196-151">其他 <xref:System.Console> 方法可供不同的輸入和輸出作業使用。</span><span class="sxs-lookup"><span data-stu-id="d5196-151">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="d5196-152">如果您在程式開始處包含 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而不必完整限定它們。</span><span class="sxs-lookup"><span data-stu-id="d5196-152">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="d5196-153">例如，您可以呼叫 `Console.WriteLine` 而不用呼叫 `System.Console.WriteLine`：</span><span class="sxs-lookup"><span data-stu-id="d5196-153">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 <span data-ttu-id="d5196-154">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-154">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]</span></span>  
  
 <span data-ttu-id="d5196-155">[!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5196-155">[!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]</span></span>  
  
 <span data-ttu-id="d5196-156">如需輸入/輸出方法的詳細資訊，請參閱 <xref:System.IO>。</span><span class="sxs-lookup"><span data-stu-id="d5196-156">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="d5196-157">命令列編譯和執行</span><span class="sxs-lookup"><span data-stu-id="d5196-157">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="d5196-158">您可以編譯 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="d5196-158">You can compile the "Hello World!"</span></span> <span data-ttu-id="d5196-159">程式，使用命令列而不是使用 Visual Studio 整合式開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="d5196-159">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="d5196-160">從命令提示字元編譯與執行</span><span class="sxs-lookup"><span data-stu-id="d5196-160">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="d5196-161">將前面程序的程式碼貼入任何文字編輯器，再將檔案儲存為文字檔案。</span><span class="sxs-lookup"><span data-stu-id="d5196-161">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="d5196-162">將檔案命名為 `Hello.cs`。</span><span class="sxs-lookup"><span data-stu-id="d5196-162">Name the file `Hello.cs`.</span></span> <span data-ttu-id="d5196-163">C# 原始程式碼檔使用延伸模組 `.cs`。</span><span class="sxs-lookup"><span data-stu-id="d5196-163">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="d5196-164">執行下列步驟之一來開啟命令提示字元視窗︰</span><span class="sxs-lookup"><span data-stu-id="d5196-164">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="d5196-165">在 Windows 10 的 [開始] 功能表中搜尋 `Developer Command Prompt`，然後點選或選擇 [VS 2017 開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="d5196-165">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="d5196-166">[開發人員命令提示字元] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d5196-166">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="d5196-167">開啟 Windows 7 的 [開始] 功能表，展開最新版 Visual Studio 的資料夾，開啟 **Visual Studio Tools** 的捷徑功能表，然後選擇 [VS 2017 開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="d5196-167">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="d5196-168">[開發人員命令提示字元] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d5196-168">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="d5196-169">從標準的命令提示字元視窗啟用命令列組建。</span><span class="sxs-lookup"><span data-stu-id="d5196-169">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="d5196-170">請參閱[如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="d5196-170">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="d5196-171">在命令提示字元視窗中，巡覽至包含 `Hello.cs` 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5196-171">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="d5196-172">輸入下列命令以編譯 `Hello.cs`。</span><span class="sxs-lookup"><span data-stu-id="d5196-172">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="d5196-173">如果您的程式沒有任何編譯錯誤，則會建立名為 `Hello.exe` 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d5196-173">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="d5196-174">在命令提示字元視窗中輸入下列命令，執行程式：</span><span class="sxs-lookup"><span data-stu-id="d5196-174">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="d5196-175">如需 C# 編譯器及其選項的詳細資訊，請參閱[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d5196-175">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d5196-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5196-176">See Also</span></span>  
 <span data-ttu-id="d5196-177">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5196-177">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d5196-178">[C# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5196-178">[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md) </span></span>  
 <span data-ttu-id="d5196-179">[字串](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5196-179">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="d5196-180">[\<paveover>C# 範例應用程式](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15) </span><span class="sxs-lookup"><span data-stu-id="d5196-180">[\<paveover>C# Sample Applications](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15) </span></span>  
 <span data-ttu-id="d5196-181">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5196-181">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d5196-182">[Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5196-182">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 [<span data-ttu-id="d5196-183">Visual C# 和 Visual Basic 使用者入門</span><span class="sxs-lookup"><span data-stu-id="d5196-183">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)

