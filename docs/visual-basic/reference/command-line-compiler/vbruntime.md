---
title: "/vbruntime |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cb07ed8c2f6070079cc51c290ff5a61305c5a5d3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="vbruntime"></a><span data-ttu-id="fcb2a-102">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="fcb2a-102">/vbruntime</span></span>
<span data-ttu-id="fcb2a-103">指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcb2a-104">Syntax</span></span>  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="fcb2a-105">引數</span><span class="sxs-lookup"><span data-stu-id="fcb2a-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="fcb2a-106">編譯而不需要 Visual Basic 執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="fcb2a-107">編譯 Visual Basic 執行階段程式庫的預設值的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="fcb2a-108">編譯而不會參考 Visual Basic 執行階段程式庫，並內嵌至組件從 Visual Basic 執行階段程式庫的核心功能。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="fcb2a-109">使用指定的程式庫 (DLL) 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcb2a-110">備註</span><span class="sxs-lookup"><span data-stu-id="fcb2a-110">Remarks</span></span>  
 <span data-ttu-id="fcb2a-111">`/vbruntime`編譯器選項可讓您指定編譯器應該編譯而不需要 Visual Basic 執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-111">The `/vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="fcb2a-112">如果您編譯 Visual Basic 執行階段程式庫參考時，會記錄錯誤或警告產生 Visual Basic 執行階段 helper 呼叫的程式碼或語言建構。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="fcb2a-113">(A *Visual Basic 執行階段 helper*是定義在 Microsoft.VisualBasic.dll 中執行特定語言語意執行階段所呼叫的函式。)</span><span class="sxs-lookup"><span data-stu-id="fcb2a-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="fcb2a-114">`/vbruntime+`選項會產生相同的行為，如果沒有，就會發生`/vbruntime`指定參數。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-114">The `/vbruntime+` option produces the same behavior that occurs if no `/vbruntime` switch is specified.</span></span> <span data-ttu-id="fcb2a-115">您可以使用`/vbruntime+`選項來覆寫先前`/vbruntime`參數。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-115">You can use the `/vbruntime+` option to override previous `/vbruntime` switches.</span></span>  
  
 <span data-ttu-id="fcb2a-116">大部分物件的`My`型別是無法使用，當您使用`/vbruntime-`或`vbruntime:``path`選項。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-116">Most objects of the `My` type are unavailable when you use the `/vbruntime-` or `vbruntime:``path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="fcb2a-117">內嵌 Visual Basic 執行階段的核心功能</span><span class="sxs-lookup"><span data-stu-id="fcb2a-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="fcb2a-118">`/vbruntime*`選項可讓您編譯而不需執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-118">The `/vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="fcb2a-119">相反地，從 Visual Basic 執行階段程式庫的核心功能會內嵌在使用者組件。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="fcb2a-120">如果您的應用程式執行，並包含 Visual Basic 執行階段平台上，您可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="fcb2a-121">下列執行階段成員會內嵌︰</span><span class="sxs-lookup"><span data-stu-id="fcb2a-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="fcb2a-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions>類別</xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="fcb2a-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="fcb2a-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>方法</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="fcb2a-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="fcb2a-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>方法</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="fcb2a-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="fcb2a-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>方法</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="fcb2a-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="fcb2a-126"><xref:Microsoft.VisualBasic.Constants.vbBack>常數</xref:Microsoft.VisualBasic.Constants.vbBack></span><span class="sxs-lookup"><span data-stu-id="fcb2a-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-127"><xref:Microsoft.VisualBasic.Constants.vbCr>常數</xref:Microsoft.VisualBasic.Constants.vbCr></span><span class="sxs-lookup"><span data-stu-id="fcb2a-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>常數</xref:Microsoft.VisualBasic.Constants.vbCrLf></span><span class="sxs-lookup"><span data-stu-id="fcb2a-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>常數</xref:Microsoft.VisualBasic.Constants.vbFormFeed></span><span class="sxs-lookup"><span data-stu-id="fcb2a-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-130"><xref:Microsoft.VisualBasic.Constants.vbLf>常數</xref:Microsoft.VisualBasic.Constants.vbLf></span><span class="sxs-lookup"><span data-stu-id="fcb2a-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>常數</xref:Microsoft.VisualBasic.Constants.vbNewLine></span><span class="sxs-lookup"><span data-stu-id="fcb2a-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>常數</xref:Microsoft.VisualBasic.Constants.vbNullChar></span><span class="sxs-lookup"><span data-stu-id="fcb2a-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>常數</xref:Microsoft.VisualBasic.Constants.vbNullString></span><span class="sxs-lookup"><span data-stu-id="fcb2a-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-134"><xref:Microsoft.VisualBasic.Constants.vbTab>常數</xref:Microsoft.VisualBasic.Constants.vbTab></span><span class="sxs-lookup"><span data-stu-id="fcb2a-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>常數</xref:Microsoft.VisualBasic.Constants.vbVerticalTab></span><span class="sxs-lookup"><span data-stu-id="fcb2a-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="fcb2a-136">某些物件的`My`類型</span><span class="sxs-lookup"><span data-stu-id="fcb2a-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="fcb2a-137">如果您編譯使用`/vbruntime*`選項和您的程式碼參考的成員從 Visual Basic 執行階段程式庫的核心功能與未內嵌，編譯器會傳回錯誤，指出成員不是可用。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-137">If you compile using the `/vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="fcb2a-138">參考指定的程式庫</span><span class="sxs-lookup"><span data-stu-id="fcb2a-138">Referencing a specified library</span></span>  
 <span data-ttu-id="fcb2a-139">您可以使用`path`引數，若要使用的自訂執行階段程式庫，而非預設的 Visual Basic 執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="fcb2a-140">如果值`path`引數為 DLL 的完整的路徑，編譯器會將該檔案做為執行階段程式庫。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="fcb2a-141">如果值`path`引數不是為 DLL 的完整的路徑，Visual Basic 編譯器會先搜尋目前資料夾中識別的 dll。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="fcb2a-142">它會在您已使用所指定的路徑中搜尋[/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-142">It will then search in the path that you have specified by using the [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="fcb2a-143">如果`/sdkpath`未使用編譯器選項，編譯器會搜尋的.NET Framework 資料夾中識別的 DLL (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-143">If the `/sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb2a-144">範例</span><span class="sxs-lookup"><span data-stu-id="fcb2a-144">Example</span></span>  
 <span data-ttu-id="fcb2a-145">下列範例示範如何使用`/vbruntime`選項編譯自訂的程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="fcb2a-145">The following example shows how to use the `/vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcb2a-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb2a-146">See Also</span></span>  
 <span data-ttu-id="fcb2a-147">[Visual Basic 核心 – Visual Studio 2010 SP1 中新的編譯模式](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span><span class="sxs-lookup"><span data-stu-id="fcb2a-147">[Visual Basic Core – New compilation mode in Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span></span>  
<span data-ttu-id="fcb2a-148"> [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="fcb2a-148"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="fcb2a-149"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="fcb2a-149"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="fcb2a-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="fcb2a-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
