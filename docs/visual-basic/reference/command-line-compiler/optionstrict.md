---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 6d281fe07754f0471f8d6c0e31cf3ea890060504
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005344"
---
# <a name="-optionstrict"></a><span data-ttu-id="1389a-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="1389a-102">-optionstrict</span></span>
<span data-ttu-id="1389a-103">強制執行嚴格的類型語義來限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="1389a-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1389a-104">語法</span><span class="sxs-lookup"><span data-stu-id="1389a-104">Syntax</span></span>  
  
```console  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1389a-105">引數</span><span class="sxs-lookup"><span data-stu-id="1389a-105">Arguments</span></span>  
 <span data-ttu-id="1389a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1389a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1389a-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1389a-107">Optional.</span></span> <span data-ttu-id="1389a-108">@No__t-0 選項會限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="1389a-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="1389a-109">此選項的預設值為 `-optionstrict-`。</span><span class="sxs-lookup"><span data-stu-id="1389a-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="1389a-110">@No__t-0 選項與 `-optionstrict` 相同。</span><span class="sxs-lookup"><span data-stu-id="1389a-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="1389a-111">您可以針對寬鬆類型的語義使用這兩者。</span><span class="sxs-lookup"><span data-stu-id="1389a-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="1389a-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="1389a-112">Required.</span></span> <span data-ttu-id="1389a-113">不遵守嚴格語言語義時發出警告。</span><span class="sxs-lookup"><span data-stu-id="1389a-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1389a-114">備註</span><span class="sxs-lookup"><span data-stu-id="1389a-114">Remarks</span></span>  
 <span data-ttu-id="1389a-115">當 `-optionstrict+` 生效時，只有擴展型別轉換可以隱含地進行。</span><span class="sxs-lookup"><span data-stu-id="1389a-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="1389a-116">隱含的縮小類型轉換（例如將 @no__t 0 的類型物件指派給整數類型物件）會回報為錯誤。</span><span class="sxs-lookup"><span data-stu-id="1389a-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="1389a-117">若要產生隱含縮小類型轉換的警告，請使用 `-optionstrict:custom`。</span><span class="sxs-lookup"><span data-stu-id="1389a-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="1389a-118">使用 `-nowarn:numberlist` 來忽略特定的警告，並 `-warnaserror:numberlist` 將特定警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="1389a-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="1389a-119">若要在 Visual Studio IDE 中設定-optionstrict</span><span class="sxs-lookup"><span data-stu-id="1389a-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="1389a-120">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="1389a-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1389a-121">在 [**專案**] 功能表上，按一下 [**屬性]。**</span><span class="sxs-lookup"><span data-stu-id="1389a-121">On the **Project** menu, click **Properties.**</span></span>   
  
2. <span data-ttu-id="1389a-122">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1389a-122">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="1389a-123">修改 [**選項 Strict** ] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="1389a-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="1389a-124">以程式設計方式設定-optionstrict</span><span class="sxs-lookup"><span data-stu-id="1389a-124">To set -optionstrict programmatically</span></span>  
  
- <span data-ttu-id="1389a-125">請參閱[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1389a-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1389a-126">範例</span><span class="sxs-lookup"><span data-stu-id="1389a-126">Example</span></span>  
 <span data-ttu-id="1389a-127">下列程式碼會使用 strict 類型的語義來編譯 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="1389a-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1389a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1389a-128">See also</span></span>

- [<span data-ttu-id="1389a-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="1389a-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1389a-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="1389a-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="1389a-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="1389a-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="1389a-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="1389a-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="1389a-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="1389a-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="1389a-134">-warnaserror （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1389a-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="1389a-135">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="1389a-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="1389a-136">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="1389a-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="1389a-137">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="1389a-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
