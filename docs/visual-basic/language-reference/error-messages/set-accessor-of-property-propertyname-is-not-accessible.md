---
title: 無法存取屬性 '<propertyname>' 的 'Set' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400340"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="2076e-102">無法存取屬性 '\<propertyname>' 的 'Set' 存取子</span><span class="sxs-lookup"><span data-stu-id="2076e-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="2076e-103">當語句無法存取屬性的程式時，會嘗試儲存屬性的值 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="2076e-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="2076e-104">如果[Set 語句](../statements/set-statement.md)標示的存取層級比其[屬性語句](../statements/property-statement.md)更嚴格，則在下列情況中，嘗試設定屬性值可能會失敗：</span><span class="sxs-lookup"><span data-stu-id="2076e-104">If the [Set Statement](../statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="2076e-105">`Set`語句標示為[私](../modifiers/private.md)用，而呼叫程式碼位於定義屬性的類別或結構外。</span><span class="sxs-lookup"><span data-stu-id="2076e-105">The `Set` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="2076e-106">`Set`語句已標示為[受保護](../modifiers/protected.md)，而呼叫程式碼不在定義屬性的類別或結構中，也不在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="2076e-106">The `Set` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="2076e-107">`Set`語句已標記為[Friend](../modifiers/friend.md) ，而呼叫程式碼不在定義該屬性的相同元件中。</span><span class="sxs-lookup"><span data-stu-id="2076e-107">The `Set` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="2076e-108">**錯誤識別碼：** BC31102</span><span class="sxs-lookup"><span data-stu-id="2076e-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2076e-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2076e-109">To correct this error</span></span>  
  
- <span data-ttu-id="2076e-110">如果您可以控制定義屬性的原始程式碼，請考慮 `Set` 使用與屬性本身相同的存取層級來宣告程式。</span><span class="sxs-lookup"><span data-stu-id="2076e-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="2076e-111">如果您無法控制定義屬性的原始程式碼，或您必須限制程式 `Set` 存取層級，而不是屬性本身，請嘗試將設定屬性值的語句，移至具有更佳存取屬性的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="2076e-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2076e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2076e-112">See also</span></span>

- [<span data-ttu-id="2076e-113">屬性程序</span><span class="sxs-lookup"><span data-stu-id="2076e-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="2076e-114">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="2076e-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
