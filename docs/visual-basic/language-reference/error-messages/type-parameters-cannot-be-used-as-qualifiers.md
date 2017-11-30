---
title: "型別參數不能當做限定詞使用"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords: BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="1f2bd-102">型別參數不能當做限定詞使用</span><span class="sxs-lookup"><span data-stu-id="1f2bd-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="1f2bd-103">程式設計項目是使用限定性條件字串，其中包含的型別參數人選。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="1f2bd-104">型別參數代表的需求，要建構的泛型型別時提供的類型。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="1f2bd-105">它不代表已定義的特定類型。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="1f2bd-106">限定性條件字串必須包含在編譯時期所定義的項目。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="1f2bd-107">下列陳述式可能會產生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="1f2bd-108">**錯誤 ID:** BC32098</span><span class="sxs-lookup"><span data-stu-id="1f2bd-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f2bd-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1f2bd-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="1f2bd-110">從限定性條件字串中，移除型別參數，或取代已定義的類型。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="1f2bd-111">如果您需要找出在合格的程式設計項目時，用於建構的類型，您必須使用其他程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="1f2bd-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2bd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f2bd-112">See Also</span></span>  
 [<span data-ttu-id="1f2bd-113">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="1f2bd-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="1f2bd-114">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="1f2bd-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="1f2bd-115">類型清單</span><span class="sxs-lookup"><span data-stu-id="1f2bd-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
