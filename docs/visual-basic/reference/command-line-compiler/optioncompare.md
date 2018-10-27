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
ms.openlocfilehash: 1d50a3bb739bbde09fa10d2adf03ec7c1ff5d344
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180796"
---
# <a name="-optioncompare"></a><span data-ttu-id="dd333-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="dd333-102">-optioncompare</span></span>
<span data-ttu-id="dd333-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="dd333-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd333-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd333-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="dd333-105">備註</span><span class="sxs-lookup"><span data-stu-id="dd333-105">Remarks</span></span>  
 <span data-ttu-id="dd333-106">您可以指定`-optioncompare`中有兩種形式：`-optioncompare:binary`若要使用二進位字串比較和`-optioncompare:text`使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="dd333-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="dd333-107">根據預設，編譯器會使用`-optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="dd333-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="dd333-108">在 Microsoft Windows 目前的字碼頁會決定的二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="dd333-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="dd333-109">一般的二進位排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd333-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="dd333-110">以文字為基礎的字串比較根據您的系統地區設定所決定的不區分大小寫文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="dd333-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="dd333-111">典型的文字排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd333-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="dd333-112">若要在 Visual Studio IDE 中設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="dd333-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="dd333-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="dd333-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dd333-114">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="dd333-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="dd333-115">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dd333-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="dd333-116">修改中的值**Option Compare**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="dd333-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="dd333-117">以程式設計方式設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="dd333-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="dd333-118">請參閱[Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="dd333-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd333-119">範例</span><span class="sxs-lookup"><span data-stu-id="dd333-119">Example</span></span>  
 <span data-ttu-id="dd333-120">下列程式碼編譯`ProjFile.vb`，並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="dd333-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd333-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd333-121">See Also</span></span>  
 [<span data-ttu-id="dd333-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="dd333-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="dd333-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="dd333-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="dd333-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="dd333-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="dd333-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="dd333-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="dd333-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="dd333-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="dd333-127">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="dd333-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="dd333-128">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="dd333-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
