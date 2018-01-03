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
ms.openlocfilehash: 692681b21c243432ec8e7160bcc1eaa4e718d64d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="33b7a-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="33b7a-102">/optionstrict</span></span>
<span data-ttu-id="33b7a-103">強制執行嚴格的類型語意來限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="33b7a-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="33b7a-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="33b7a-105">引數</span><span class="sxs-lookup"><span data-stu-id="33b7a-105">Arguments</span></span>  
 <span data-ttu-id="33b7a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="33b7a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="33b7a-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="33b7a-107">Optional.</span></span> <span data-ttu-id="33b7a-108">`/optionstrict+`選項會限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="33b7a-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="33b7a-109">這個選項的預設值是`/optionstrict-`。</span><span class="sxs-lookup"><span data-stu-id="33b7a-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="33b7a-110">`/optionstrict+`選項等同於`/optionstrict`。</span><span class="sxs-lookup"><span data-stu-id="33b7a-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="33b7a-111">您可以使用的允許動作的類型語意。</span><span class="sxs-lookup"><span data-stu-id="33b7a-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="33b7a-112">必要。</span><span class="sxs-lookup"><span data-stu-id="33b7a-112">Required.</span></span> <span data-ttu-id="33b7a-113">未遵守嚴格的語意時發出警告。</span><span class="sxs-lookup"><span data-stu-id="33b7a-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33b7a-114">備註</span><span class="sxs-lookup"><span data-stu-id="33b7a-114">Remarks</span></span>  
 <span data-ttu-id="33b7a-115">當`/optionstrict+`作用中，是可以隱含地進行唯一擴展的類型轉換。</span><span class="sxs-lookup"><span data-stu-id="33b7a-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="33b7a-116">隱含縮小類型轉換，例如指派`Decimal`輸入整數型別物件的物件，會回報為錯誤。</span><span class="sxs-lookup"><span data-stu-id="33b7a-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="33b7a-117">若要產生隱含縮小類型轉換的警告，請使用`/optionstrict:custom`。</span><span class="sxs-lookup"><span data-stu-id="33b7a-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="33b7a-118">使用`/nowarn:numberlist`略過特定的警告和`/warnaserror:numberlist`將特定警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="33b7a-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="33b7a-119">在 Visual Studio IDE 中設定 /optionstrict</span><span class="sxs-lookup"><span data-stu-id="33b7a-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="33b7a-120">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="33b7a-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="33b7a-121">在**專案**功能表上，按一下 **屬性。**</span><span class="sxs-lookup"><span data-stu-id="33b7a-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="33b7a-122">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33b7a-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="33b7a-123">修改中的值**Option Strict**方塊。</span><span class="sxs-lookup"><span data-stu-id="33b7a-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="33b7a-124">以程式設計方式設定 /optionstrict</span><span class="sxs-lookup"><span data-stu-id="33b7a-124">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="33b7a-125">請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="33b7a-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33b7a-126">範例</span><span class="sxs-lookup"><span data-stu-id="33b7a-126">Example</span></span>  
 <span data-ttu-id="33b7a-127">下列程式碼編譯`Test.vb`使用嚴格的類型語意。</span><span class="sxs-lookup"><span data-stu-id="33b7a-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="33b7a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="33b7a-128">See Also</span></span>  
 [<span data-ttu-id="33b7a-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="33b7a-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="33b7a-130">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="33b7a-130">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="33b7a-131">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="33b7a-131">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="33b7a-132">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="33b7a-132">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="33b7a-133">/nowarn</span><span class="sxs-lookup"><span data-stu-id="33b7a-133">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="33b7a-134">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33b7a-134">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="33b7a-135">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="33b7a-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="33b7a-136">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="33b7a-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="33b7a-137">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="33b7a-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
