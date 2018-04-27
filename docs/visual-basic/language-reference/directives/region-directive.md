---
title: '#Region 指示詞'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83ceac7d73eff23e16c5f6efb1c4eb8a2210ee2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="region-directive"></a><span data-ttu-id="ee0ee-102">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="ee0ee-102">#Region Directive</span></span>
<span data-ttu-id="ee0ee-103">摺疊並隱藏 Visual Basic 檔案中的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee0ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee0ee-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="ee0ee-105">組件</span><span class="sxs-lookup"><span data-stu-id="ee0ee-105">Parts</span></span>  
  
|<span data-ttu-id="ee0ee-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ee0ee-106">Term</span></span>|<span data-ttu-id="ee0ee-107">定義</span><span class="sxs-lookup"><span data-stu-id="ee0ee-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="ee0ee-108">必要。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-108">Required.</span></span> <span data-ttu-id="ee0ee-109">做為摺疊區域標題的字串。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="ee0ee-110">區域預設會摺疊。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="ee0ee-111">終止 `#Region` 區塊。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee0ee-112">備註</span><span class="sxs-lookup"><span data-stu-id="ee0ee-112">Remarks</span></span>  
 <span data-ttu-id="ee0ee-113">使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="ee0ee-114">您可以放置，或*巢狀*，以類似的區域群組在一起的其他區域內。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee0ee-115">範例</span><span class="sxs-lookup"><span data-stu-id="ee0ee-115">Example</span></span>  
 <span data-ttu-id="ee0ee-116">此範例使用 `#Region` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="ee0ee-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ee0ee-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee0ee-117">See Also</span></span>  
 [<span data-ttu-id="ee0ee-118">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="ee0ee-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="ee0ee-119">大綱</span><span class="sxs-lookup"><span data-stu-id="ee0ee-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="ee0ee-120">操作說明：摺疊和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="ee0ee-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
