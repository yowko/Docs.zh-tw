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
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400535"
---
# <a name="-optionstrict"></a><span data-ttu-id="41621-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="41621-102">-optionstrict</span></span>

<span data-ttu-id="41621-103">強制執行嚴格的類型語義來限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="41621-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="41621-104">語法</span><span class="sxs-lookup"><span data-stu-id="41621-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="41621-105">引數</span><span class="sxs-lookup"><span data-stu-id="41621-105">Arguments</span></span>

<span data-ttu-id="41621-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="41621-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="41621-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="41621-107">Optional.</span></span> <span data-ttu-id="41621-108">`-optionstrict+`選項會限制隱含類型轉換。</span><span class="sxs-lookup"><span data-stu-id="41621-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="41621-109">此選項的預設值為 `-optionstrict-` 。</span><span class="sxs-lookup"><span data-stu-id="41621-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="41621-110">`-optionstrict+`選項與相同 `-optionstrict` 。</span><span class="sxs-lookup"><span data-stu-id="41621-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="41621-111">您可以針對寬鬆類型的語義使用這兩者。</span><span class="sxs-lookup"><span data-stu-id="41621-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="41621-112">必要。</span><span class="sxs-lookup"><span data-stu-id="41621-112">Required.</span></span> <span data-ttu-id="41621-113">不遵守嚴格語言語義時發出警告。</span><span class="sxs-lookup"><span data-stu-id="41621-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="41621-114">備註</span><span class="sxs-lookup"><span data-stu-id="41621-114">Remarks</span></span>

<span data-ttu-id="41621-115">當 `-optionstrict+` 生效時，只有擴展型別轉換可以隱含地進行。</span><span class="sxs-lookup"><span data-stu-id="41621-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="41621-116">隱含的縮小類型轉換（例如將 `Decimal` 類型物件指派給整數類型物件）會回報為錯誤。</span><span class="sxs-lookup"><span data-stu-id="41621-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="41621-117">若要產生隱含縮小類型轉換的警告，請使用 `-optionstrict:custom` 。</span><span class="sxs-lookup"><span data-stu-id="41621-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="41621-118">用 `-nowarn:numberlist` 來忽略特定的警告，並 `-warnaserror:numberlist` 將特定警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="41621-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="41621-119">若要在 Visual Studio IDE 中設定-optionstrict</span><span class="sxs-lookup"><span data-stu-id="41621-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="41621-120">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="41621-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="41621-121">在 [**專案**] 功能表上，按一下 [**屬性]。**</span><span class="sxs-lookup"><span data-stu-id="41621-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="41621-122">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="41621-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="41621-123">修改 [**選項 Strict** ] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="41621-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="41621-124">以程式設計方式設定-optionstrict</span><span class="sxs-lookup"><span data-stu-id="41621-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="41621-125">請參閱[Option Strict 語句](../../language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="41621-125">See [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="41621-126">範例</span><span class="sxs-lookup"><span data-stu-id="41621-126">Example</span></span>

<span data-ttu-id="41621-127">下列程式碼會 `Test.vb` 使用 strict 類型的語義進行編譯。</span><span class="sxs-lookup"><span data-stu-id="41621-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="41621-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41621-128">See also</span></span>

- [<span data-ttu-id="41621-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="41621-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="41621-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="41621-130">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="41621-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="41621-131">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="41621-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="41621-132">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="41621-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="41621-133">-nowarn</span></span>](nowarn.md)
- [<span data-ttu-id="41621-134">-warnaserror （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="41621-134">-warnaserror (Visual Basic)</span></span>](warnaserror.md)
- [<span data-ttu-id="41621-135">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="41621-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="41621-136">Long</span><span class="sxs-lookup"><span data-stu-id="41621-136">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="41621-137">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="41621-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
