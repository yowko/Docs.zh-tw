---
title: 類型參數不能當做限定詞使用
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592141"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="a4260-102">類型參數不能當做限定詞使用</span><span class="sxs-lookup"><span data-stu-id="a4260-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="a4260-103">程式設計專案是以包含型別參數的限定性字串來限定。</span><span class="sxs-lookup"><span data-stu-id="a4260-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="a4260-104">型別參數代表在結構化泛型型別時要提供的型別需求。</span><span class="sxs-lookup"><span data-stu-id="a4260-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="a4260-105">它不代表特定的已定義型別。</span><span class="sxs-lookup"><span data-stu-id="a4260-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="a4260-106">限定性字串必須僅包含在編譯時期定義的元素。</span><span class="sxs-lookup"><span data-stu-id="a4260-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="a4260-107">下列陳述式可能會產生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4260-107">The following statements can generate this error.</span></span>  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="a4260-108">**錯誤識別碼：** BC32098</span><span class="sxs-lookup"><span data-stu-id="a4260-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4260-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a4260-109">To correct this error</span></span>  
  
1. <span data-ttu-id="a4260-110">請從限定性字串中移除類型參數，或將它取代為已定義的類型。</span><span class="sxs-lookup"><span data-stu-id="a4260-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="a4260-111">如果您需要使用已結構化的類型來尋找限定的程式設計項目，則必須使用其他程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="a4260-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4260-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4260-112">See also</span></span>

- [<span data-ttu-id="a4260-113">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="a4260-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="a4260-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4260-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a4260-115">類型清單</span><span class="sxs-lookup"><span data-stu-id="a4260-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
