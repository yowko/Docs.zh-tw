---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 3edb1f74ab63497aeda0d72847bce92ad315a1a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098913"
---
# <a name="-optioninfer"></a><span data-ttu-id="dc3c9-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="dc3c9-102">-optioninfer</span></span>

<span data-ttu-id="dc3c9-103">可讓您在變數宣告中使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc3c9-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc3c9-105">引數</span><span class="sxs-lookup"><span data-stu-id="dc3c9-105">Arguments</span></span>  
  
|<span data-ttu-id="dc3c9-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="dc3c9-106">Term</span></span>|<span data-ttu-id="dc3c9-107">定義</span><span class="sxs-lookup"><span data-stu-id="dc3c9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="dc3c9-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="dc3c9-108">`+` &#124; `-`</span></span>|<span data-ttu-id="dc3c9-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-109">Optional.</span></span> <span data-ttu-id="dc3c9-110">指定 `-optioninfer+` 以啟用區域類型推斷，或是指定 `-optioninfer-` 以封鎖它。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="dc3c9-111">未指定值的 `-optioninfer` 選項與 `-optioninfer+` 相同。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="dc3c9-112">不存在 `-optioninfer` 參數時的預設值也是 `-optioninfer+`。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="dc3c9-113">預設值是在 Vbc.rsp 回應檔中設定。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="dc3c9-114">您可以使用 `-noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="dc3c9-115">這個選項的編譯器預設值是 `-optioninfer-`。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc3c9-116">備註</span><span class="sxs-lookup"><span data-stu-id="dc3c9-116">Remarks</span></span>  

 <span data-ttu-id="dc3c9-117">如果原始程式碼檔包含 [Option 推斷語句](../../language-reference/statements/option-infer-statement.md)，則語句會覆寫 `-optioninfer` 命令列編譯器設定。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-117">If the source code file contains an [Option Infer Statement](../../language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="dc3c9-118">若要在 Visual Studio IDE 中設定-optioninfer</span><span class="sxs-lookup"><span data-stu-id="dc3c9-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="dc3c9-119">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="dc3c9-120">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="dc3c9-121">在 [ **編譯** ] 索引標籤上，修改 [ **選項推斷** ] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc3c9-122">範例</span><span class="sxs-lookup"><span data-stu-id="dc3c9-122">Example</span></span>  

 <span data-ttu-id="dc3c9-123">下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。</span><span class="sxs-lookup"><span data-stu-id="dc3c9-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc3c9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3c9-124">See also</span></span>

- [<span data-ttu-id="dc3c9-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="dc3c9-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="dc3c9-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="dc3c9-126">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="dc3c9-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="dc3c9-127">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="dc3c9-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="dc3c9-128">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="dc3c9-129">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="dc3c9-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="dc3c9-130">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="dc3c9-130">Option Infer Statement</span></span>](../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="dc3c9-131">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="dc3c9-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="dc3c9-132">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="dc3c9-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="dc3c9-133">專案設計工具、編譯頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc3c9-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="dc3c9-134">-noconfig</span><span class="sxs-lookup"><span data-stu-id="dc3c9-134">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="dc3c9-135">從命令列建置</span><span class="sxs-lookup"><span data-stu-id="dc3c9-135">Building from the Command Line</span></span>](building-from-the-command-line.md)
