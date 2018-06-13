---
title: 使用 csc.exe 建置命令列
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 3cd49a17991f3d7606b0364a83be2b2e30ba0cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218055"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="189f9-102">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="189f9-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="189f9-103">您可以在命令提示字元中輸入 C# 編譯器的可執行檔名稱 (*csc.exe*)，藉此叫用該編譯器。</span><span class="sxs-lookup"><span data-stu-id="189f9-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="189f9-104">如果您使用 [Visual Studio 的開發人員命令提示字元] 視窗，所有必要的環境變數都會自動完成設定。</span><span class="sxs-lookup"><span data-stu-id="189f9-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="189f9-105">如需如何存取此工具的資訊，請參閱 [Visual Studio 的開發人員命令提示字元](../../../framework/tools/developer-command-prompt-for-vs.md)主題。</span><span class="sxs-lookup"><span data-stu-id="189f9-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="189f9-106">如果您使用標準 [命令提示字元] 視窗，則必須先調整路徑，才能在電腦上的任何子目錄中叫用 *csc.exe*。</span><span class="sxs-lookup"><span data-stu-id="189f9-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="189f9-107">您也必須執行 *vsvars32.bat* 來設定適當的環境變數，以便支援命令列組建。</span><span class="sxs-lookup"><span data-stu-id="189f9-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="189f9-108">如需 *vsvars32.bat* 的詳細資訊，包括如何尋找和執行的指示，請參閱[如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="189f9-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="189f9-109">如果您是在只有 [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)] 的電腦上工作，則可以在 [SDK 命令提示字元]\ (可從 [Microsoft .NET Framework SDK] 功能表選項開啟) 中使用 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="189f9-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="189f9-110">您也可以使用 MSBuild 以程式設計的方式建置 C# 程式。</span><span class="sxs-lookup"><span data-stu-id="189f9-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="189f9-111">如需詳細資訊，請參閱 [MSBuild](/visualstudio/msbuild/msbuild)。</span><span class="sxs-lookup"><span data-stu-id="189f9-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="189f9-112">*csc.exe* 可執行檔通常位於 *Windows* 目錄下的 Microsoft.NET\Framework\\\<版本> 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="189f9-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="189f9-113">它的位置可能依據特定電腦的實際組態而有所不同。</span><span class="sxs-lookup"><span data-stu-id="189f9-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="189f9-114">如果您的電腦上安裝了多個版本的 .NET Framework，您將看到這個檔案的多個版本。</span><span class="sxs-lookup"><span data-stu-id="189f9-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="189f9-115">如需這類安裝的詳細資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="189f9-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="189f9-116">當您使用 Visual Studio IDE 建置專案時，可以在 [輸出] 視窗中顯示 **csc** 命令和其關聯的編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="189f9-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="189f9-117">若要顯示這項資訊，請遵循[如何：檢視、儲存和設定組建記錄檔](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log)中的指示，將記錄資料的詳細等級變更為 [一般] 或 [詳細]。</span><span class="sxs-lookup"><span data-stu-id="189f9-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="189f9-118">在您重新建置專案之後，請在 [輸出] 視窗中搜尋 **csc**，尋找 C# 編譯器的引動過程。</span><span class="sxs-lookup"><span data-stu-id="189f9-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="189f9-119">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="189f9-119">**In this topic**</span></span>

- [<span data-ttu-id="189f9-120">命令列語法規則</span><span class="sxs-lookup"><span data-stu-id="189f9-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="189f9-121">範例命令列</span><span class="sxs-lookup"><span data-stu-id="189f9-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="189f9-122">C# 編譯器與 C++ 編譯器輸出的差異</span><span class="sxs-lookup"><span data-stu-id="189f9-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="189f9-123">C# 編譯器命令列語法規則</span><span class="sxs-lookup"><span data-stu-id="189f9-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="189f9-124">C# 編譯器會在解譯作業系統命令列所指定的引數時使用下列規則：</span><span class="sxs-lookup"><span data-stu-id="189f9-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="189f9-125">引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。</span><span class="sxs-lookup"><span data-stu-id="189f9-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="189f9-126">插入號字元 (^) 不會被辨識為逸出字元或分隔符號。</span><span class="sxs-lookup"><span data-stu-id="189f9-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="189f9-127">先由作業系統中的命令列剖析器處理字元，再將它傳遞給程式中的 `argv` 陣列。</span><span class="sxs-lookup"><span data-stu-id="189f9-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="189f9-128">不論其內是否包含空白字元，都會將以雙引號括住的字串 ("string") 解譯為單一引數。</span><span class="sxs-lookup"><span data-stu-id="189f9-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="189f9-129">有引號的字串可以內嵌到引數中。</span><span class="sxs-lookup"><span data-stu-id="189f9-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="189f9-130">前面有反斜線 (\\") 的雙引號會解譯為常值雙引號字元 (")。</span><span class="sxs-lookup"><span data-stu-id="189f9-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="189f9-131">反斜線會逐字解譯，除非後面緊接著雙引號。</span><span class="sxs-lookup"><span data-stu-id="189f9-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="189f9-132">如果雙引號後面加上偶數數目的反斜線，則會在每對反斜線的 `argv` 陣列中放入一個反斜線，並將雙引號解譯為字串分隔符號。</span><span class="sxs-lookup"><span data-stu-id="189f9-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="189f9-133">如果雙引號後面加上奇數數目的反斜線，則會在每對反斜線的 `argv` 陣列中放入一個反斜線，並使用其餘的反斜線「逸出」雙引號。</span><span class="sxs-lookup"><span data-stu-id="189f9-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="189f9-134">這會在 `argv` 中新增常值雙引號 (")。</span><span class="sxs-lookup"><span data-stu-id="189f9-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="189f9-135">C# 編譯器命令列範例</span><span class="sxs-lookup"><span data-stu-id="189f9-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="189f9-136">編譯可產生 *File.exe* 的 *File.cs*：</span><span class="sxs-lookup"><span data-stu-id="189f9-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="189f9-137">編譯可產生 *File.dll* 的 *File.cs*：</span><span class="sxs-lookup"><span data-stu-id="189f9-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="189f9-138">編譯 *File.cs* 並建立 *My.exe*：</span><span class="sxs-lookup"><span data-stu-id="189f9-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="189f9-139">在啟用最佳化的情況下編譯目前目錄中的所有 C# 檔案，並定義 DEBUG 符號。</span><span class="sxs-lookup"><span data-stu-id="189f9-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="189f9-140">輸出為 *File2.exe*：</span><span class="sxs-lookup"><span data-stu-id="189f9-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="189f9-141">編譯產生 *File2.dll* 偵錯版本之目前目錄中的所有 C# 檔案。</span><span class="sxs-lookup"><span data-stu-id="189f9-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="189f9-142">不會顯示標誌和警告：</span><span class="sxs-lookup"><span data-stu-id="189f9-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="189f9-143">將目前目錄中的所有 C# 檔案都編譯為 *Something.xyz* (DLL)：</span><span class="sxs-lookup"><span data-stu-id="189f9-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="189f9-144">C# 編譯器與 C++ 編譯器輸出的差異</span><span class="sxs-lookup"><span data-stu-id="189f9-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="189f9-145">叫用 C# 編譯器時並不會建立目的檔 (*.obj*)，而是直接建立輸出檔。</span><span class="sxs-lookup"><span data-stu-id="189f9-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="189f9-146">因此，C# 編譯器不需要連結器。</span><span class="sxs-lookup"><span data-stu-id="189f9-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="189f9-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="189f9-147">See also</span></span>
 [<span data-ttu-id="189f9-148">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="189f9-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="189f9-149">依字母順序列出 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="189f9-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [<span data-ttu-id="189f9-150">依分類列出的 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="189f9-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [<span data-ttu-id="189f9-151">Main() 和命令列引數</span><span class="sxs-lookup"><span data-stu-id="189f9-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="189f9-152">命令列引數</span><span class="sxs-lookup"><span data-stu-id="189f9-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [<span data-ttu-id="189f9-153">如何：顯示命令列引數</span><span class="sxs-lookup"><span data-stu-id="189f9-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="189f9-154">如何：使用 foreach 存取命令列引數</span><span class="sxs-lookup"><span data-stu-id="189f9-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="189f9-155">Main() 傳回值</span><span class="sxs-lookup"><span data-stu-id="189f9-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
