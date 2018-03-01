---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 62a9a4bf3428f3ee731e7ecc63be51dbf3076ee4
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="ffe29-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="ffe29-102">/optioncompare</span></span>
<span data-ttu-id="ffe29-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="ffe29-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe29-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffe29-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="ffe29-105">備註</span><span class="sxs-lookup"><span data-stu-id="ffe29-105">Remarks</span></span>  
 <span data-ttu-id="ffe29-106">您可以指定`/optioncompare`中有兩種形式：`/optioncompare:binary`使用二進位字串比較和`/optioncompare:text`使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="ffe29-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="ffe29-107">根據預設，編譯器會使用`/optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="ffe29-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="ffe29-108">在 Microsoft Windows 中，所使用的字碼頁會決定二進位排序順序。</span><span class="sxs-lookup"><span data-stu-id="ffe29-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="ffe29-109">一般的二進位排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="ffe29-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="ffe29-110">以文字為基礎的字串比較會根據您的系統地區設定所決定的不區分大小寫文字排序順序。</span><span class="sxs-lookup"><span data-stu-id="ffe29-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="ffe29-111">一般文字排序順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="ffe29-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="ffe29-112">在 Visual Studio IDE 中設定 /optioncompare</span><span class="sxs-lookup"><span data-stu-id="ffe29-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="ffe29-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="ffe29-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ffe29-114">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="ffe29-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="ffe29-115">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ffe29-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="ffe29-116">修改中的值**Option Compare**方塊。</span><span class="sxs-lookup"><span data-stu-id="ffe29-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="ffe29-117">以程式設計方式設定 /optioncompare</span><span class="sxs-lookup"><span data-stu-id="ffe29-117">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="ffe29-118">請參閱[Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ffe29-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe29-119">範例</span><span class="sxs-lookup"><span data-stu-id="ffe29-119">Example</span></span>  
 <span data-ttu-id="ffe29-120">下列程式碼編譯`ProjFile.vb`，並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="ffe29-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffe29-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="ffe29-121">See Also</span></span>  
 [<span data-ttu-id="ffe29-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ffe29-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ffe29-123">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="ffe29-123">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="ffe29-124">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="ffe29-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="ffe29-125">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="ffe29-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="ffe29-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="ffe29-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="ffe29-127">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="ffe29-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="ffe29-128">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="ffe29-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
