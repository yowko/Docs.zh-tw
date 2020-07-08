---
title: 如何：使用追蹤和偵錯進行條件式編譯
description: 瞭解如何在編譯 .NET 應用程式時，使用 TRACE 和 DEBUG 條件屬性來有條件地進行編譯。
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
ms.openlocfilehash: 8758b793866ec0317f91d636476d33bd001ddd78
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051216"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="ccfa8-103">如何：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-103">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="ccfa8-104">當您於開發期間偵錯應用程式時，追蹤及偵錯輸出都會移至 Visual Studio 中的 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-104">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="ccfa8-105">然而，若要在已部署的應用程式中包含追蹤功能，您必須在啟用 **TRACE** 編譯器指示詞的情況下編譯已經過檢測的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-105">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="ccfa8-106">這可將追蹤程式碼編譯成應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-106">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="ccfa8-107">如果您沒有啟用 **TRACE** 指示詞，則在編譯期間會忽略所有的追蹤程式碼，並且不會在您將部署的可執行程式碼中包含追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-107">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="ccfa8-108">追蹤和偵錯方法均具有相關聯的Conditional 屬性。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-108">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="ccfa8-109">例如，如果追蹤的 Conditional 屬性為 **true**，則會在組件 (已編譯的 .exe 檔案或 .dll) 中包含所有的追蹤陳述式，如果 **Trace** Conditional 屬性為 **false**，則不會包含追蹤陳述式。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-109">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="ccfa8-110">您可以為組建開啟 **Trace** 或 **Debug** Conditional 屬性，或兩者都開啟或都關閉。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-110">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="ccfa8-111">因此，組建可分為四種類型：**Debug**、**Trace**、兩者都開啟或兩者都關閉。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-111">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="ccfa8-112">部分產品部署的發行組建可能不含兩者；大部分的偵錯組建則包含兩者。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-112">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="ccfa8-113">您可用數種方式來指定應用程式的編譯器設定：</span><span class="sxs-lookup"><span data-stu-id="ccfa8-113">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="ccfa8-114">屬性頁</span><span class="sxs-lookup"><span data-stu-id="ccfa8-114">The property pages</span></span>  
  
- <span data-ttu-id="ccfa8-115">命令列</span><span class="sxs-lookup"><span data-stu-id="ccfa8-115">The command line</span></span>  
  
- <span data-ttu-id="ccfa8-116">**#CONST** (若為 Visual Basic) 和 **#define** (若為 C#)</span><span class="sxs-lookup"><span data-stu-id="ccfa8-116">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="ccfa8-117">從屬性頁對話方塊變更編譯設定</span><span class="sxs-lookup"><span data-stu-id="ccfa8-117">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="ccfa8-118">以滑鼠右鍵按一下方案總管\*\*\*\* 中的專案節點。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-118">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="ccfa8-119">從捷徑功能表中選擇 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-119">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="ccfa8-120">在 Visual Basic 中，按一下屬性頁左窗格內的 [編譯]\*\*\*\* 索引標籤，然後按一下 [進階編譯選項]\*\*\*\* 按鈕，即可顯示 [進階編譯器設定]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-120">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="ccfa8-121">請選取您想要啟用之編譯器設定的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-121">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="ccfa8-122">清除您想要停用之設定值的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-122">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="ccfa8-123">在 C# 中，按一下屬性頁左窗格內的 [建置]\*\*\*\* 索引標籤，然後選取您想要啟用之編譯器設定的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-123">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="ccfa8-124">清除您想要停用之設定值的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-124">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="ccfa8-125">使用命令列來編譯已經過檢測的程式碼</span><span class="sxs-lookup"><span data-stu-id="ccfa8-125">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="ccfa8-126">在命令列上設定條件式編譯器參數。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-126">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="ccfa8-127">編譯器會在可執行檔中包含追蹤或偵錯程式碼。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-127">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="ccfa8-128">例如，在命令列上輸入下列編譯器指令會在已編譯可執行檔中包含追蹤程式碼：</span><span class="sxs-lookup"><span data-stu-id="ccfa8-128">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="ccfa8-129">針對 Visual Basic： **vbc -r:System.dll-d:TRACE = TRUE-d:DEBUG = FALSE MyApplication .vb**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-129">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="ccfa8-130">若為 c #： **csc -r:System.dll-d:TRACE-d:DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-130">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="ccfa8-131">若要編譯一個以上的應用程式檔案，請在檔案名稱之間保留一個空格，例如，**MyApplication1.vb MyApplication2.vb MyApplication3.vb** 或 **MyApplication1.cs MyApplication2.cs MyApplication3.cs**。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-131">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="ccfa8-132">上述範例中使用的條件式編譯指示詞的意義如下：</span><span class="sxs-lookup"><span data-stu-id="ccfa8-132">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="ccfa8-133">指示詞</span><span class="sxs-lookup"><span data-stu-id="ccfa8-133">Directive</span></span>|<span data-ttu-id="ccfa8-134">意義</span><span class="sxs-lookup"><span data-stu-id="ccfa8-134">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="ccfa8-135">Visual Basic 編譯器</span><span class="sxs-lookup"><span data-stu-id="ccfa8-135">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="ccfa8-136">C# 編譯器</span><span class="sxs-lookup"><span data-stu-id="ccfa8-136">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="ccfa8-137">參考外部組件 (EXE 或 DLL)</span><span class="sxs-lookup"><span data-stu-id="ccfa8-137">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="ccfa8-138">定義條件式編譯的符號</span><span class="sxs-lookup"><span data-stu-id="ccfa8-138">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="ccfa8-139">您必須使用大寫字母來拼寫 TRACE 或 DEBUG。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-139">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="ccfa8-140">如需條件式編譯命令的詳細資訊，請在命令提示字元中輸入 `vbc /?` (若為 Visual Basic) 或 `csc /?` (若為 C#)。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-140">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="ccfa8-141">如需詳細資訊，請參閱[從命令列建置](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) 或[叫用命令列編譯器](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic)。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-141">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="ccfa8-142">使用 #CONST 或 #define 來執行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-142">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="ccfa8-143">請在原始程式碼檔案上方輸入適用於您的程式語言之陳述式。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-143">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="ccfa8-144">語言</span><span class="sxs-lookup"><span data-stu-id="ccfa8-144">Language</span></span>|<span data-ttu-id="ccfa8-145">引數</span><span class="sxs-lookup"><span data-stu-id="ccfa8-145">Statement</span></span>|<span data-ttu-id="ccfa8-146">結果</span><span class="sxs-lookup"><span data-stu-id="ccfa8-146">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="ccfa8-147">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-147">**Visual Basic**</span></span>|<span data-ttu-id="ccfa8-148">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-148">**#CONST TRACE = true**</span></span>|<span data-ttu-id="ccfa8-149">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="ccfa8-149">Enables tracing</span></span>|  
    ||<span data-ttu-id="ccfa8-150">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-150">**#CONST TRACE = false**</span></span>|<span data-ttu-id="ccfa8-151">停用追蹤</span><span class="sxs-lookup"><span data-stu-id="ccfa8-151">Disables tracing</span></span>|  
    ||<span data-ttu-id="ccfa8-152">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-152">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="ccfa8-153">啟用偵錯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-153">Enables debugging</span></span>|  
    ||<span data-ttu-id="ccfa8-154">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-154">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="ccfa8-155">停用偵錯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-155">Disables debugging</span></span>|  
    |<span data-ttu-id="ccfa8-156">**C#**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-156">**C#**</span></span>|<span data-ttu-id="ccfa8-157">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-157">**#define TRACE**</span></span>|<span data-ttu-id="ccfa8-158">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="ccfa8-158">Enables tracing</span></span>|  
    ||<span data-ttu-id="ccfa8-159">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-159">**#undef TRACE**</span></span>|<span data-ttu-id="ccfa8-160">停用追蹤</span><span class="sxs-lookup"><span data-stu-id="ccfa8-160">Disables tracing</span></span>|  
    ||<span data-ttu-id="ccfa8-161">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-161">**#define DEBUG**</span></span>|<span data-ttu-id="ccfa8-162">啟用偵錯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-162">Enables debugging</span></span>|  
    ||<span data-ttu-id="ccfa8-163">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="ccfa8-163">**#undef DEBUG**</span></span>|<span data-ttu-id="ccfa8-164">停用偵錯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-164">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="ccfa8-165">若要停用追蹤或偵錯</span><span class="sxs-lookup"><span data-stu-id="ccfa8-165">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="ccfa8-166">請刪除原始程式碼中的編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-166">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="ccfa8-167">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="ccfa8-167">\- or -</span></span>  
  
<span data-ttu-id="ccfa8-168">將編譯器指示詞標為註解。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-168">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccfa8-169">當您準備編譯時，可從 [建置]\*\*\*\* 功能表中選取 [建置]\*\*\*\*，或使用命令列方法 (但不輸入 **d:**) 來定義條件式編譯的符號。</span><span class="sxs-lookup"><span data-stu-id="ccfa8-169">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfa8-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccfa8-170">See also</span></span>

- [<span data-ttu-id="ccfa8-171">追蹤和稽核應用程式</span><span class="sxs-lookup"><span data-stu-id="ccfa8-171">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="ccfa8-172">如何：建立、初始化和設定追蹤參數</span><span class="sxs-lookup"><span data-stu-id="ccfa8-172">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="ccfa8-173">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="ccfa8-173">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="ccfa8-174">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="ccfa8-174">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="ccfa8-175">如何：將追蹤陳述式加入至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="ccfa8-175">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="ccfa8-176">如何為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="ccfa8-176">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="ccfa8-177">作法：叫用命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ccfa8-177">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
