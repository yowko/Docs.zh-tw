---
title: "/optioninfer |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioninfer
dev_langs:
- VB
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
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
ms.openlocfilehash: 4bcc35da2a255ca75805c8a918027d2ccb61b154
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="optioninfer"></a><span data-ttu-id="35e00-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="35e00-102">/optioninfer</span></span>
<span data-ttu-id="35e00-103">可讓您在變數宣告中使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="35e00-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35e00-104">語法</span><span class="sxs-lookup"><span data-stu-id="35e00-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="35e00-105">引數</span><span class="sxs-lookup"><span data-stu-id="35e00-105">Arguments</span></span>  
  
|<span data-ttu-id="35e00-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="35e00-106">Term</span></span>|<span data-ttu-id="35e00-107">定義</span><span class="sxs-lookup"><span data-stu-id="35e00-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="35e00-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="35e00-108">`+` &#124; `-`</span></span>|<span data-ttu-id="35e00-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="35e00-109">Optional.</span></span> <span data-ttu-id="35e00-110">指定 `/optioninfer+` 以啟用區域類型推斷，或是指定 `/optioninfer-` 以封鎖它。</span><span class="sxs-lookup"><span data-stu-id="35e00-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="35e00-111">未指定值的 `/optioninfer` 選項與 `/optioninfer+` 相同。</span><span class="sxs-lookup"><span data-stu-id="35e00-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="35e00-112">不存在 `/optioninfer` 參數時的預設值也是 `/optioninfer+`。</span><span class="sxs-lookup"><span data-stu-id="35e00-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="35e00-113">預設值是在 Vbc.rsp 回應檔中設定。</span><span class="sxs-lookup"><span data-stu-id="35e00-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="35e00-114">您可以使用 `/noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="35e00-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="35e00-115">這個選項的編譯器預設值是 `/optioninfer-`。</span><span class="sxs-lookup"><span data-stu-id="35e00-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35e00-116">備註</span><span class="sxs-lookup"><span data-stu-id="35e00-116">Remarks</span></span>  
 <span data-ttu-id="35e00-117">如果原始程式碼檔案包含[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)，陳述式會覆寫`/optioninfer`命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="35e00-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="35e00-118">在 Visual Studio IDE 中設定 /optioninfer</span><span class="sxs-lookup"><span data-stu-id="35e00-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="35e00-119">選取的專案中**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="35e00-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="35e00-120">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="35e00-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="35e00-121">如需詳細資訊，請參閱[NIB︰ 使用專案設計工具管理專案屬性](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)。</span><span class="sxs-lookup"><span data-stu-id="35e00-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="35e00-122">在**編譯**索引標籤上，修改中的值**Option infer**方塊。</span><span class="sxs-lookup"><span data-stu-id="35e00-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35e00-123">範例</span><span class="sxs-lookup"><span data-stu-id="35e00-123">Example</span></span>  
 <span data-ttu-id="35e00-124">下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。</span><span class="sxs-lookup"><span data-stu-id="35e00-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="35e00-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35e00-125">See Also</span></span>  
 <span data-ttu-id="35e00-126">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="35e00-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="35e00-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="35e00-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="35e00-130"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="35e00-131"> [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-131"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="35e00-132"> [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="35e00-133"> [Visual Basic 預設值，專案選項對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="35e00-133"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="35e00-134"> [專案設計工具、編譯頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="35e00-134"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="35e00-135"> [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="35e00-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="35e00-136"> [從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span><span class="sxs-lookup"><span data-stu-id="35e00-136"> [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span></span>
