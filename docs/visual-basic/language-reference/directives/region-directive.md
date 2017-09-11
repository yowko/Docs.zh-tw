---
title: "#Region 指示詞 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
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
ms.openlocfilehash: 86b8e9ce99a8c12e290f5efdc5a5c4da57f350d9
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="region-directive"></a>#<span data-ttu-id="5fa60-102">Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="5fa60-102">Region Directive</span></span>
<span data-ttu-id="5fa60-103">摺疊並隱藏 Visual Basic 檔案中的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="5fa60-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa60-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fa60-104">Syntax</span></span>  
  
```  
  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="5fa60-105">組件</span><span class="sxs-lookup"><span data-stu-id="5fa60-105">Parts</span></span>  
  
|<span data-ttu-id="5fa60-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="5fa60-106">Term</span></span>|<span data-ttu-id="5fa60-107">定義</span><span class="sxs-lookup"><span data-stu-id="5fa60-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="5fa60-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="5fa60-108">Required.</span></span> <span data-ttu-id="5fa60-109">做為摺疊區域標題的字串。</span><span class="sxs-lookup"><span data-stu-id="5fa60-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="5fa60-110">區域預設會摺疊。</span><span class="sxs-lookup"><span data-stu-id="5fa60-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="5fa60-111">終止 `#Region` 區塊。</span><span class="sxs-lookup"><span data-stu-id="5fa60-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fa60-112">備註</span><span class="sxs-lookup"><span data-stu-id="5fa60-112">Remarks</span></span>  
 <span data-ttu-id="5fa60-113">使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。</span><span class="sxs-lookup"><span data-stu-id="5fa60-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="5fa60-114">您可以放置，或*巢狀*，其他區域來分組類似的區域內。</span><span class="sxs-lookup"><span data-stu-id="5fa60-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa60-115">範例</span><span class="sxs-lookup"><span data-stu-id="5fa60-115">Example</span></span>  
 <span data-ttu-id="5fa60-116">此範例使用 `#Region` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="5fa60-116">This example uses the `#Region` directive.</span></span>  
  
 <span data-ttu-id="5fa60-117">[!code-vb[VbVbalrConditionalComp #&4;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5fa60-117">[!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa60-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fa60-118">See Also</span></span>  
 <span data-ttu-id="5fa60-119">[#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="5fa60-119">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="5fa60-120"> [大綱](https://docs.microsoft.com/visualstudio/ide/outlining) </span><span class="sxs-lookup"><span data-stu-id="5fa60-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining) </span></span>  
<span data-ttu-id="5fa60-121"> [如何：摺疊和隱藏程式碼區段](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span><span class="sxs-lookup"><span data-stu-id="5fa60-121"> [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span></span>
