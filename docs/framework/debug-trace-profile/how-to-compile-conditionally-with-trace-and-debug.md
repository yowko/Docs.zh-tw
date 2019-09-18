---
title: HOW TO：使用追蹤和偵錯進行條件式編譯
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d06d1ef8e1508aefa8c9ed9327b89f58ff6976fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052754"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="c6715-102">HOW TO：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="c6715-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="c6715-103">當您於開發期間偵錯應用程式時，追蹤及偵錯輸出都會移至 Visual Studio 中的 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="c6715-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="c6715-104">然而，若要在已部署的應用程式中包含追蹤功能，您必須在啟用 **TRACE** 編譯器指示詞的情況下編譯已經過檢測的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6715-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="c6715-105">這可將追蹤程式碼編譯成應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="c6715-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="c6715-106">如果您沒有啟用 **TRACE** 指示詞，則在編譯期間會忽略所有的追蹤程式碼，並且不會在您將部署的可執行程式碼中包含追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6715-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="c6715-107">追蹤和偵錯方法均具有相關聯的Conditional 屬性。</span><span class="sxs-lookup"><span data-stu-id="c6715-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="c6715-108">例如，如果追蹤的 Conditional 屬性為 **true**，則會在組件 (已編譯的 .exe 檔案或 .dll) 中包含所有的追蹤陳述式，如果 **Trace** Conditional 屬性為 **false**，則不會包含追蹤陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6715-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="c6715-109">您可以為組建開啟 **Trace** 或 **Debug** Conditional 屬性，或兩者都開啟或都關閉。</span><span class="sxs-lookup"><span data-stu-id="c6715-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="c6715-110">因此，有四種類型的組建：**Debug**、 **Trace**、both 或兩者皆非。</span><span class="sxs-lookup"><span data-stu-id="c6715-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="c6715-111">部分產品部署的發行組建可能不含兩者；大部分的偵錯組建則包含兩者。</span><span class="sxs-lookup"><span data-stu-id="c6715-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="c6715-112">您可用數種方式來指定應用程式的編譯器設定：</span><span class="sxs-lookup"><span data-stu-id="c6715-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="c6715-113">屬性頁</span><span class="sxs-lookup"><span data-stu-id="c6715-113">The property pages</span></span>  
  
- <span data-ttu-id="c6715-114">命令列</span><span class="sxs-lookup"><span data-stu-id="c6715-114">The command line</span></span>  
  
- <span data-ttu-id="c6715-115">**#CONST** (若為 Visual Basic) 和 **#define** (若為 C#)</span><span class="sxs-lookup"><span data-stu-id="c6715-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="c6715-116">從屬性頁對話方塊變更編譯設定</span><span class="sxs-lookup"><span data-stu-id="c6715-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="c6715-117">以滑鼠右鍵按一下方案總管 中的專案節點。</span><span class="sxs-lookup"><span data-stu-id="c6715-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="c6715-118">從捷徑功能表中選擇 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="c6715-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="c6715-119">在 Visual Basic 中，按一下屬性頁左窗格內的 [編譯] 索引標籤，然後按一下 [進階編譯選項] 按鈕，即可顯示 [進階編譯器設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c6715-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="c6715-120">請選取您想要啟用之編譯器設定的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c6715-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="c6715-121">清除您想要停用之設定值的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c6715-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="c6715-122">在 C# 中，按一下屬性頁左窗格內的 [建置] 索引標籤，然後選取您想要啟用之編譯器設定的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c6715-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="c6715-123">清除您想要停用之設定值的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c6715-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="c6715-124">使用命令列來編譯已經過檢測的程式碼</span><span class="sxs-lookup"><span data-stu-id="c6715-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="c6715-125">在命令列上設定條件式編譯器參數。</span><span class="sxs-lookup"><span data-stu-id="c6715-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="c6715-126">編譯器會在可執行檔中包含追蹤或偵錯程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6715-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="c6715-127">例如，在命令列上輸入下列編譯器指令會在已編譯可執行檔中包含追蹤程式碼：</span><span class="sxs-lookup"><span data-stu-id="c6715-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="c6715-128">針對 Visual Basic： **vbc-r:System.dll-d:TRACE = TRUE-d:DEBUG = FALSE MyApplication .vb**</span><span class="sxs-lookup"><span data-stu-id="c6715-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="c6715-129">適用C#于： **csc-r:System.dll-d:TRACE-d:DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="c6715-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="c6715-130">若要編譯一個以上的應用程式檔案，請在檔案名稱之間保留一個空格，例如，**MyApplication1.vb MyApplication2.vb MyApplication3.vb** 或 **MyApplication1.cs MyApplication2.cs MyApplication3.cs**。</span><span class="sxs-lookup"><span data-stu-id="c6715-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="c6715-131">上述範例中使用的條件式編譯指示詞的意義如下：</span><span class="sxs-lookup"><span data-stu-id="c6715-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="c6715-132">指示詞</span><span class="sxs-lookup"><span data-stu-id="c6715-132">Directive</span></span>|<span data-ttu-id="c6715-133">意義</span><span class="sxs-lookup"><span data-stu-id="c6715-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="c6715-134">Visual Basic 編譯器</span><span class="sxs-lookup"><span data-stu-id="c6715-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="c6715-135">C# 編譯器</span><span class="sxs-lookup"><span data-stu-id="c6715-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="c6715-136">參考外部組件 (EXE 或 DLL)</span><span class="sxs-lookup"><span data-stu-id="c6715-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="c6715-137">定義條件式編譯的符號</span><span class="sxs-lookup"><span data-stu-id="c6715-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="c6715-138">您必須使用大寫字母來拼寫 TRACE 或 DEBUG。</span><span class="sxs-lookup"><span data-stu-id="c6715-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="c6715-139">如需條件式編譯命令的詳細資訊，請在命令提示字元中輸入 `vbc /?` (若為 Visual Basic) 或 `csc /?` (若為 C#)。</span><span class="sxs-lookup"><span data-stu-id="c6715-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="c6715-140">如需詳細資訊，請參閱[從命令列建置](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) 或[叫用命令列編譯器](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic)。</span><span class="sxs-lookup"><span data-stu-id="c6715-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="c6715-141">使用 #CONST 或 #define 來執行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="c6715-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="c6715-142">請在原始程式碼檔案上方輸入適用於您的程式語言之陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6715-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="c6715-143">語言</span><span class="sxs-lookup"><span data-stu-id="c6715-143">Language</span></span>|<span data-ttu-id="c6715-144">陳述式</span><span class="sxs-lookup"><span data-stu-id="c6715-144">Statement</span></span>|<span data-ttu-id="c6715-145">結果</span><span class="sxs-lookup"><span data-stu-id="c6715-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="c6715-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="c6715-146">**Visual Basic**</span></span>|<span data-ttu-id="c6715-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="c6715-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="c6715-148">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="c6715-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="c6715-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="c6715-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="c6715-150">停用追蹤</span><span class="sxs-lookup"><span data-stu-id="c6715-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="c6715-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="c6715-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="c6715-152">啟用偵錯</span><span class="sxs-lookup"><span data-stu-id="c6715-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="c6715-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="c6715-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="c6715-154">停用偵錯</span><span class="sxs-lookup"><span data-stu-id="c6715-154">Disables debugging</span></span>|  
    |<span data-ttu-id="c6715-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="c6715-155">**C#**</span></span>|<span data-ttu-id="c6715-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="c6715-156">**#define TRACE**</span></span>|<span data-ttu-id="c6715-157">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="c6715-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="c6715-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="c6715-158">**#undef TRACE**</span></span>|<span data-ttu-id="c6715-159">停用追蹤</span><span class="sxs-lookup"><span data-stu-id="c6715-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="c6715-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="c6715-160">**#define DEBUG**</span></span>|<span data-ttu-id="c6715-161">啟用偵錯</span><span class="sxs-lookup"><span data-stu-id="c6715-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="c6715-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="c6715-162">**#undef DEBUG**</span></span>|<span data-ttu-id="c6715-163">停用偵錯</span><span class="sxs-lookup"><span data-stu-id="c6715-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="c6715-164">若要停用追蹤或偵錯</span><span class="sxs-lookup"><span data-stu-id="c6715-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="c6715-165">請刪除原始程式碼中的編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="c6715-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="c6715-166">\-或-</span><span class="sxs-lookup"><span data-stu-id="c6715-166">\- or -</span></span>  
  
<span data-ttu-id="c6715-167">將編譯器指示詞標為註解。</span><span class="sxs-lookup"><span data-stu-id="c6715-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6715-168">當您準備編譯時，可從 [建置] 功能表中選取 [建置]，或使用命令列方法 (但不輸入 **d:** ) 來定義條件式編譯的符號。</span><span class="sxs-lookup"><span data-stu-id="c6715-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6715-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6715-169">See also</span></span>

- [<span data-ttu-id="c6715-170">追蹤和檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="c6715-170">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="c6715-171">如何：建立、初始化和設定追蹤參數</span><span class="sxs-lookup"><span data-stu-id="c6715-171">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="c6715-172">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="c6715-172">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="c6715-173">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="c6715-173">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="c6715-174">如何：將追蹤語句新增至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="c6715-174">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="c6715-175">如何：為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="c6715-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="c6715-176">如何：叫用命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="c6715-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
