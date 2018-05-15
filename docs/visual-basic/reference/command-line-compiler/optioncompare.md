---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1906710ef10634187782f9355146dfa7ccb7748
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-optioncompare"></a><span data-ttu-id="8919f-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="8919f-102">-optioncompare</span></span>
<span data-ttu-id="8919f-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="8919f-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8919f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8919f-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="8919f-105">備註</span><span class="sxs-lookup"><span data-stu-id="8919f-105">Remarks</span></span>  
 <span data-ttu-id="8919f-106">您可以指定`-optioncompare`中有兩種形式：`-optioncompare:binary`使用二進位字串比較和`-optioncompare:text`使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="8919f-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="8919f-107">根據預設，編譯器會使用`-optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="8919f-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="8919f-108">在 Microsoft Windows 中，目前的字碼頁會決定二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="8919f-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="8919f-109">一般的二進位排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="8919f-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="8919f-110">以文字為基礎的字串比較會根據您的系統地區設定所決定的不區分大小寫文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="8919f-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="8919f-111">一般文字排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="8919f-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="8919f-112">在 Visual Studio IDE 中設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="8919f-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="8919f-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="8919f-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8919f-114">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="8919f-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="8919f-115">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8919f-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="8919f-116">修改中的值**Option Compare**方塊。</span><span class="sxs-lookup"><span data-stu-id="8919f-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="8919f-117">以程式設計方式設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="8919f-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="8919f-118">請參閱[Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8919f-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8919f-119">範例</span><span class="sxs-lookup"><span data-stu-id="8919f-119">Example</span></span>  
 <span data-ttu-id="8919f-120">下列程式碼編譯`ProjFile.vb`，並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="8919f-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8919f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8919f-121">See Also</span></span>  
 [<span data-ttu-id="8919f-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="8919f-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8919f-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="8919f-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="8919f-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="8919f-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="8919f-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="8919f-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="8919f-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="8919f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="8919f-127">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="8919f-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="8919f-128">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="8919f-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
