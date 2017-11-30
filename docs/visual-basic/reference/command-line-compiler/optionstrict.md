---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="6db4e-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="6db4e-102">/optionstrict</span></span>
<span data-ttu-id="6db4e-103">強制執行嚴格的類型語意來限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="6db4e-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6db4e-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6db4e-105">引數</span><span class="sxs-lookup"><span data-stu-id="6db4e-105">Arguments</span></span>  
 <span data-ttu-id="6db4e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="6db4e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="6db4e-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="6db4e-107">Optional.</span></span> <span data-ttu-id="6db4e-108">`/optionstrict+`選項會限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="6db4e-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="6db4e-109">這個選項的預設值是`/optionstrict-`。</span><span class="sxs-lookup"><span data-stu-id="6db4e-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="6db4e-110">`/optionstrict+`選項等同於`/optionstrict`。</span><span class="sxs-lookup"><span data-stu-id="6db4e-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="6db4e-111">您可以使用的允許動作的類型語意。</span><span class="sxs-lookup"><span data-stu-id="6db4e-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="6db4e-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="6db4e-112">Required.</span></span> <span data-ttu-id="6db4e-113">未遵守嚴格的語意時發出警告。</span><span class="sxs-lookup"><span data-stu-id="6db4e-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6db4e-114">備註</span><span class="sxs-lookup"><span data-stu-id="6db4e-114">Remarks</span></span>  
 <span data-ttu-id="6db4e-115">當`/optionstrict+`作用中，是可以隱含地進行唯一擴展的類型轉換。</span><span class="sxs-lookup"><span data-stu-id="6db4e-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="6db4e-116">隱含縮小類型轉換，例如指派`Decimal`輸入整數型別物件的物件，會回報為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6db4e-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="6db4e-117">若要產生隱含縮小類型轉換的警告，請使用`/optionstrict:custom`。</span><span class="sxs-lookup"><span data-stu-id="6db4e-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="6db4e-118">使用`/nowarn:numberlist`略過特定的警告和`/warnaserror:numberlist`將特定警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="6db4e-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="6db4e-119">在 Visual Studio IDE 中設定 /optionstrict</span><span class="sxs-lookup"><span data-stu-id="6db4e-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="6db4e-120">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="6db4e-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6db4e-121">在**專案**功能表上，按一下 **屬性。**</span><span class="sxs-lookup"><span data-stu-id="6db4e-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="6db4e-122">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="6db4e-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="6db4e-123">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6db4e-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="6db4e-124">修改中的值**Option Strict**方塊。</span><span class="sxs-lookup"><span data-stu-id="6db4e-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="6db4e-125">以程式設計方式設定 /optionstrict</span><span class="sxs-lookup"><span data-stu-id="6db4e-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="6db4e-126">請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6db4e-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db4e-127">範例</span><span class="sxs-lookup"><span data-stu-id="6db4e-127">Example</span></span>  
 <span data-ttu-id="6db4e-128">下列程式碼編譯`Test.vb`使用嚴格的類型語意。</span><span class="sxs-lookup"><span data-stu-id="6db4e-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6db4e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6db4e-129">See Also</span></span>  
 [<span data-ttu-id="6db4e-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6db4e-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6db4e-131">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="6db4e-131">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="6db4e-132">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="6db4e-132">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="6db4e-133">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="6db4e-133">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="6db4e-134">/nowarn</span><span class="sxs-lookup"><span data-stu-id="6db4e-134">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="6db4e-135">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6db4e-135">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="6db4e-136">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="6db4e-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="6db4e-137">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="6db4e-137">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="6db4e-138">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="6db4e-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
