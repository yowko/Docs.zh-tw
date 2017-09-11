---
title: "/optioncompare |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
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
ms.openlocfilehash: c9512427cda0b6a3bcb0c1fe338b47ff9f779d19
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="optioncompare"></a><span data-ttu-id="743f9-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="743f9-102">/optioncompare</span></span>
<span data-ttu-id="743f9-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="743f9-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="743f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="743f9-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="743f9-105">備註</span><span class="sxs-lookup"><span data-stu-id="743f9-105">Remarks</span></span>  
 <span data-ttu-id="743f9-106">您可以指定`/optioncompare`中有兩種形式︰`/optioncompare:binary`使用二進位字串比較和`/optioncompare:text`使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="743f9-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="743f9-107">根據預設，編譯器會使用`/optioncompare:binary`。</span><span class="sxs-lookup"><span data-stu-id="743f9-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="743f9-108">Microsoft Windows 中所使用的字碼頁會決定二進位排序次序。</span><span class="sxs-lookup"><span data-stu-id="743f9-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="743f9-109">一般的二進位排序順序如下所示︰</span><span class="sxs-lookup"><span data-stu-id="743f9-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="743f9-110">文字為基礎的字串比較是以不區分大小寫文字排序順序取決於您的系統地區設定為依據。</span><span class="sxs-lookup"><span data-stu-id="743f9-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="743f9-111">一般文字排序順序如下所示︰</span><span class="sxs-lookup"><span data-stu-id="743f9-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="743f9-112">在 Visual Studio IDE 中設定 /optioncompare</span><span class="sxs-lookup"><span data-stu-id="743f9-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="743f9-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="743f9-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="743f9-114">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="743f9-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="743f9-115">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="743f9-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="743f9-116">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="743f9-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="743f9-117">修改中的值**選項比較**方塊。</span><span class="sxs-lookup"><span data-stu-id="743f9-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="743f9-118">以程式設計方式設定 /optioncompare</span><span class="sxs-lookup"><span data-stu-id="743f9-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="743f9-119">請參閱[Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="743f9-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="743f9-120">範例</span><span class="sxs-lookup"><span data-stu-id="743f9-120">Example</span></span>  
 <span data-ttu-id="743f9-121">下列程式碼會編譯 P`rojFile.vb` ，並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="743f9-121">The following code compiles P`rojFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="743f9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="743f9-122">See Also</span></span>  
 <span data-ttu-id="743f9-123">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="743f9-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="743f9-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="743f9-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="743f9-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="743f9-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="743f9-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="743f9-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="743f9-127"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="743f9-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="743f9-128"> [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="743f9-128"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="743f9-129"> [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="743f9-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
