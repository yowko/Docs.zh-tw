---
title: 只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: b798f296b62b51de34a7ec5ce5a8b608273f5748
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819225"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="ec7af-102">只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="ec7af-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="ec7af-103">您無法推斷匿名類型成員名稱，從複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="ec7af-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="ec7af-104">如需匿名型別可以和無法推斷成員名稱和類型的來源的詳細資訊，請參閱[How to:推斷屬性名稱和匿名類型宣告中的型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="ec7af-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="ec7af-105">**錯誤 ID:** BC36556</span><span class="sxs-lookup"><span data-stu-id="ec7af-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec7af-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ec7af-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ec7af-107">為成員的名稱，指派運算式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ec7af-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec7af-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec7af-108">See also</span></span>

- [<span data-ttu-id="ec7af-109">匿名類型</span><span class="sxs-lookup"><span data-stu-id="ec7af-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="ec7af-110">如何：推斷屬性名稱和匿名類型宣告中的類型</span><span class="sxs-lookup"><span data-stu-id="ec7af-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
