---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="13a98-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="13a98-102">/optioncompare</span></span>
<span data-ttu-id="13a98-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="13a98-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a98-104">語法</span><span class="sxs-lookup"><span data-stu-id="13a98-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="13a98-105">備註</span><span class="sxs-lookup"><span data-stu-id="13a98-105">Remarks</span></span>  
 <span data-ttu-id="13a98-106">您可以指定`/optioncompare`中有兩種形式：`/optioncompare:binary`使用二進位字串比較和`/optioncompare:text`使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="13a98-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="13a98-107">根據預設，編譯器會使用`/optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="13a98-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="13a98-108">在 Microsoft Windows 中，所使用的字碼頁會決定二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="13a98-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="13a98-109">一般的二進位排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="13a98-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="13a98-110">以文字為基礎的字串比較會根據您的系統地區設定所決定的不區分大小寫文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="13a98-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="13a98-111">一般文字排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="13a98-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="13a98-112">在 Visual Studio IDE 中設定 /optioncompare</span><span class="sxs-lookup"><span data-stu-id="13a98-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="13a98-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="13a98-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="13a98-114">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="13a98-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="13a98-115">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="13a98-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="13a98-116">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="13a98-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="13a98-117">修改中的值**Option Compare**方塊。</span><span class="sxs-lookup"><span data-stu-id="13a98-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="13a98-118">以程式設計方式設定 /optioncompare</span><span class="sxs-lookup"><span data-stu-id="13a98-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="13a98-119">請參閱[Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="13a98-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a98-120">範例</span><span class="sxs-lookup"><span data-stu-id="13a98-120">Example</span></span>  
 <span data-ttu-id="13a98-121">下列程式碼編譯`ProjFile.vb`，並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="13a98-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="13a98-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13a98-122">See Also</span></span>  
 [<span data-ttu-id="13a98-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="13a98-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="13a98-124">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="13a98-124">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="13a98-125">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="13a98-125">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="13a98-126">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="13a98-126">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="13a98-127">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="13a98-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="13a98-128">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="13a98-128">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="13a98-129">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="13a98-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
