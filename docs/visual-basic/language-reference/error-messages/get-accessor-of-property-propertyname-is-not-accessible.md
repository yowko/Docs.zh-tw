---
title: 無法存取屬性 '<propertyname>' 的 'Get' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 72675f882676d3ded9ccc9ff245a1d757fa4393a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257781"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="1af68-102">'Get' 存取子的屬性 '\<屬性名稱 >' 不能存取</span><span class="sxs-lookup"><span data-stu-id="1af68-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="1af68-103">陳述式來擷取屬性的值，當它並沒有屬性的存取嘗試`Get`程序。</span><span class="sxs-lookup"><span data-stu-id="1af68-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="1af68-104">如果[Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)標示為更嚴格的存取權層級比其[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)，嘗試讀取屬性值無法在下列情況：</span><span class="sxs-lookup"><span data-stu-id="1af68-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="1af68-105">`Get`陳述式會標示[私人](../../../visual-basic/language-reference/modifiers/private.md)，而且呼叫程式碼是類別或結構定義的屬性之外。</span><span class="sxs-lookup"><span data-stu-id="1af68-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="1af68-106">`Get`陳述式會標示[Protected](../../../visual-basic/language-reference/modifiers/protected.md)和呼叫的程式碼是不在類別或結構中定義的屬性，也不是在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="1af68-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="1af68-107">`Get`陳述式會標示[Friend](../../../visual-basic/language-reference/modifiers/friend.md)而且呼叫程式碼不是處於相同的組件中定義屬性。</span><span class="sxs-lookup"><span data-stu-id="1af68-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="1af68-108">**錯誤 ID:** BC31103</span><span class="sxs-lookup"><span data-stu-id="1af68-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1af68-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1af68-109">To correct this error</span></span>  
  
-   <span data-ttu-id="1af68-110">如果您可以定義該屬性的原始程式碼控制，請考慮宣告`Get`屬性本身以相同的存取層級的程序。</span><span class="sxs-lookup"><span data-stu-id="1af68-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="1af68-111">如果您沒有定義屬性的原始程式碼控制，或者您必須限制`Get`程序在多個屬性本身，嘗試移動讀取屬性值的程式碼區域具有更好的存取權的陳述式存取層級屬性。</span><span class="sxs-lookup"><span data-stu-id="1af68-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af68-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1af68-112">See also</span></span>
- [<span data-ttu-id="1af68-113">屬性程序</span><span class="sxs-lookup"><span data-stu-id="1af68-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="1af68-114">如何：宣告混合的存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="1af68-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
