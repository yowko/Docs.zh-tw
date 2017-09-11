---
title: "/netcf |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
dev_langs:
- VB
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
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
ms.openlocfilehash: 375ec79fe2bf63bc03988ecaad877eb27f43d55b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="netcf"></a><span data-ttu-id="0089d-102">/netcf</span><span class="sxs-lookup"><span data-stu-id="0089d-102">/netcf</span></span>
<span data-ttu-id="0089d-103">設定要以 [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] 為目標的編譯器。</span><span class="sxs-lookup"><span data-stu-id="0089d-103">Sets the compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0089d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0089d-104">Syntax</span></span>  
  
```  
/netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="0089d-105">備註</span><span class="sxs-lookup"><span data-stu-id="0089d-105">Remarks</span></span>  
 <span data-ttu-id="0089d-106">`/netcf`選項會使[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]目標的編譯器[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]而不是完整[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0089d-106">The `/netcf` option causes the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to target the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] rather than the full [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="0089d-107">目前只有在完整的語言功能[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]已停用。</span><span class="sxs-lookup"><span data-stu-id="0089d-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="0089d-108">`/netcf`選項設計來搭配[/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)。</span><span class="sxs-lookup"><span data-stu-id="0089d-108">The `/netcf` option is designed to be used with [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="0089d-109">停用的語言功能`/netcf`都是相同的語言功能不存在於目標檔案`/sdkpath`。</span><span class="sxs-lookup"><span data-stu-id="0089d-109">The language features disabled by `/netcf` are the same language features not present in the files targeted with `/sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0089d-110">`/netcf`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="0089d-110">The `/netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="0089d-111">`/netcf`時設定選項[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]載入裝置專案。</span><span class="sxs-lookup"><span data-stu-id="0089d-111">The `/netcf` option is set when a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="0089d-112">`/netcf`選項會變更下列語言功能︰</span><span class="sxs-lookup"><span data-stu-id="0089d-112">The `/netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="0089d-113">[結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字，終止程式執行時，會停用。</span><span class="sxs-lookup"><span data-stu-id="0089d-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="0089d-114">下列程式會編譯並執行，而無`/netcf`會在編譯階段失敗，但`/netcf`。</span><span class="sxs-lookup"><span data-stu-id="0089d-114">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     <span data-ttu-id="0089d-115">[!code-vb[VbVbalrCompiler #&34;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0089d-115">[!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]</span></span>  
  
-   <span data-ttu-id="0089d-116">晚期繫結在所有表單中，會停用。</span><span class="sxs-lookup"><span data-stu-id="0089d-116">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="0089d-117">可辨識晚期繫結的狀況發生時，會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="0089d-117">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="0089d-118">下列程式會編譯並執行，而無`/netcf`會在編譯階段失敗，但`/netcf`。</span><span class="sxs-lookup"><span data-stu-id="0089d-118">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     <span data-ttu-id="0089d-119">[!code-vb[VbVbalrCompiler #&35;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0089d-119">[!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]</span></span>  
  
-   <span data-ttu-id="0089d-120">[自動](../../../visual-basic/language-reference/modifiers/auto.md)， [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)，和[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞會停用。</span><span class="sxs-lookup"><span data-stu-id="0089d-120">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="0089d-121">語法[宣告陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)陳述式也會修改成`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。</span><span class="sxs-lookup"><span data-stu-id="0089d-121">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="0089d-122">下列程式碼顯示的效果`/netcf`編譯。</span><span class="sxs-lookup"><span data-stu-id="0089d-122">The following code shows the effect of `/netcf` on a compilation.</span></span>  
  
     <span data-ttu-id="0089d-123">[!code-vb[VbVbalrCompiler #&36;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0089d-123">[!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]</span></span>  
  
-   <span data-ttu-id="0089d-124">使用 Visual Basic 6.0 關鍵字中移除[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會產生不同的錯誤時`/netcf`用。</span><span class="sxs-lookup"><span data-stu-id="0089d-124">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a different error when `/netcf` is used.</span></span> <span data-ttu-id="0089d-125">這會影響下列關鍵字的錯誤訊息︰</span><span class="sxs-lookup"><span data-stu-id="0089d-125">This affects the error messages for the following keywords:</span></span>  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a><span data-ttu-id="0089d-126">範例</span><span class="sxs-lookup"><span data-stu-id="0089d-126">Example</span></span>  
 <span data-ttu-id="0089d-127">下列程式碼編譯`Myfile.vb`與[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中的預設安裝目錄中找到[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]C 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="0089d-127">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] on the C drive.</span></span> <span data-ttu-id="0089d-128">一般而言，您可使用的最新版本[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0089d-128">Typically, you would use the most recent version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0089d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0089d-129">See Also</span></span>  
 <span data-ttu-id="0089d-130">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0089d-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0089d-131"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="0089d-131"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="0089d-132"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="0089d-132"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
