---
title: 無法存取屬性 '<propertyname>' 的 'Get' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 08986cde7151cac5e70083705f38a83837bedb93
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874043"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="8c587-102">無法存取屬性 '\<propertyname>' 的 'Get' 存取子</span><span class="sxs-lookup"><span data-stu-id="8c587-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="8c587-103">當語句無法存取屬性的程式時，它會嘗試取得屬性的值 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="8c587-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="8c587-104">如果 [Get 語句](../statements/get-statement.md) 標示了更嚴格的存取層級，而不是其 [Property 語句](../statements/property-statement.md)，則在下列情況下，嘗試讀取屬性值可能會失敗：</span><span class="sxs-lookup"><span data-stu-id="8c587-104">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="8c587-105">`Get`語句標示為[私](../modifiers/private.md)用，而且呼叫程式碼位於定義屬性的類別或結構之外。</span><span class="sxs-lookup"><span data-stu-id="8c587-105">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="8c587-106">`Get`語句標示為[受保護](../modifiers/protected.md)，而且呼叫程式碼不在定義屬性的類別或結構中，也不在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="8c587-106">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="8c587-107">`Get`語句標示為[Friend](../modifiers/friend.md) ，而且呼叫程式碼不在定義該屬性的相同元件中。</span><span class="sxs-lookup"><span data-stu-id="8c587-107">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="8c587-108">**錯誤識別碼：** BC31103</span><span class="sxs-lookup"><span data-stu-id="8c587-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c587-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8c587-109">To correct this error</span></span>  
  
- <span data-ttu-id="8c587-110">如果您有定義該屬性之原始程式碼的控制權，請考慮使用與 `Get` 屬性本身相同的存取層級來宣告程式。</span><span class="sxs-lookup"><span data-stu-id="8c587-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="8c587-111">如果您沒有定義此屬性之原始程式碼的控制權，或您必須將 `Get` 程式存取層級限制在屬性本身之外，請嘗試將讀取屬性值的語句移至對屬性有較佳存取權的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="8c587-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c587-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c587-112">See also</span></span>

- [<span data-ttu-id="8c587-113">屬性程序</span><span class="sxs-lookup"><span data-stu-id="8c587-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="8c587-114">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="8c587-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
