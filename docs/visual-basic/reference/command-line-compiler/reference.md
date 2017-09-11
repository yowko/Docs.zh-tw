---
title: "/reference (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
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
ms.openlocfilehash: 6870c0b6008124bad18f8eba9207d06e085f2307
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="reference-visual-basic"></a><span data-ttu-id="823b7-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="823b7-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="823b7-103">會導致編譯器提供給您正在編譯的專案中指定的組件的型別資訊。</span><span class="sxs-lookup"><span data-stu-id="823b7-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="823b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="823b7-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="823b7-105">引數</span><span class="sxs-lookup"><span data-stu-id="823b7-105">Arguments</span></span>  
  
|<span data-ttu-id="823b7-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="823b7-106">Term</span></span>|<span data-ttu-id="823b7-107">定義</span><span class="sxs-lookup"><span data-stu-id="823b7-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="823b7-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="823b7-108">Required.</span></span> <span data-ttu-id="823b7-109">組件檔案名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="823b7-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="823b7-110">如果檔案名稱包含空格，請用引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="823b7-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="823b7-111">備註</span><span class="sxs-lookup"><span data-stu-id="823b7-111">Remarks</span></span>  
 <span data-ttu-id="823b7-112">您匯入的檔案必須包含組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="823b7-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="823b7-113">只有公用型別是在組件外部可見的。</span><span class="sxs-lookup"><span data-stu-id="823b7-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="823b7-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)選項從模組匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="823b7-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="823b7-115">如果您參考的組件 （組件 A） 本身也參考另一個組件 (組件 B)，如果您需要參考 B 組件︰</span><span class="sxs-lookup"><span data-stu-id="823b7-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="823b7-116">來自組件 A 的型別繼承自型別或實作介面從 b 組件</span><span class="sxs-lookup"><span data-stu-id="823b7-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="823b7-117">欄位、 屬性、 事件或方法，從組件 B 的傳回型別或參數型別會叫用。</span><span class="sxs-lookup"><span data-stu-id="823b7-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="823b7-118">使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="823b7-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="823b7-119">編譯器無法辨識的組件 （而非模組） 中的型別，它必須強制解析的型別。</span><span class="sxs-lookup"><span data-stu-id="823b7-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="823b7-120">一種執行這是定義型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="823b7-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="823b7-121">其他方式可解決在組件的編譯器型別名稱。</span><span class="sxs-lookup"><span data-stu-id="823b7-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="823b7-122">例如，如果您是從組件中的型別繼承，型別名稱就會知道編譯器。</span><span class="sxs-lookup"><span data-stu-id="823b7-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="823b7-123">參考常用 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件中，依預設會使用。</span><span class="sxs-lookup"><span data-stu-id="823b7-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="823b7-124">使用`/noconfig`若不想讓編譯器使用 Vbc.rsp。</span><span class="sxs-lookup"><span data-stu-id="823b7-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="823b7-125">簡短形式`/reference`是`/r`。</span><span class="sxs-lookup"><span data-stu-id="823b7-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="823b7-126">範例</span><span class="sxs-lookup"><span data-stu-id="823b7-126">Example</span></span>  
 <span data-ttu-id="823b7-127">下列程式碼編譯來源檔案我`nput.vb`M 從參考組件`etad1.dll`和 M`etad2.dll`產生 O`ut.exe`。</span><span class="sxs-lookup"><span data-stu-id="823b7-127">The following code compiles source file I`nput.vb` and reference assemblies from M`etad1.dll` and M`etad2.dll` to produce O`ut.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="823b7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="823b7-128">See Also</span></span>  
 <span data-ttu-id="823b7-129">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="823b7-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="823b7-130"> [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="823b7-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="823b7-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="823b7-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="823b7-132"> [公用](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="823b7-132"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="823b7-133"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="823b7-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
