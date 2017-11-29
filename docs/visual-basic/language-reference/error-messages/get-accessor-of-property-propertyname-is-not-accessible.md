---
title: "&#39;Get &#39;存取子屬性 &#39;&lt;propertyname&gt;&#39; 不能存取"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords: BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="13ed8-102">&#39;Get &#39;存取子屬性 &#39;&lt;propertyname&gt;&#39; 不能存取</span><span class="sxs-lookup"><span data-stu-id="13ed8-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="13ed8-103">陳述式嘗試擷取屬性的值，它並沒有存取權的屬性時`Get`程序。</span><span class="sxs-lookup"><span data-stu-id="13ed8-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="13ed8-104">如果[Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)標示為更具限制性的存取層級比其[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)，嘗試讀取屬性值可能會失敗，在下列情況：</span><span class="sxs-lookup"><span data-stu-id="13ed8-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="13ed8-105">`Get`陳述式會標示[私人](../../../visual-basic/language-reference/modifiers/private.md)，而且呼叫程式碼是類別或結構定義的屬性之外。</span><span class="sxs-lookup"><span data-stu-id="13ed8-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="13ed8-106">`Get`陳述式會標示[保護](../../../visual-basic/language-reference/modifiers/protected.md)和呼叫的程式碼是不在類別或結構中定義的屬性，也不是在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="13ed8-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="13ed8-107">`Get`陳述式會標示[Friend](../../../visual-basic/language-reference/modifiers/friend.md)和呼叫的程式碼不是相同的組件中定義屬性。</span><span class="sxs-lookup"><span data-stu-id="13ed8-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="13ed8-108">**錯誤 ID:** BC31103</span><span class="sxs-lookup"><span data-stu-id="13ed8-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13ed8-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="13ed8-109">To correct this error</span></span>  
  
-   <span data-ttu-id="13ed8-110">如果您有定義該屬性的原始程式碼控制，請考慮宣告`Get`屬性本身相同的存取層級的程序。</span><span class="sxs-lookup"><span data-stu-id="13ed8-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="13ed8-111">如果您沒有定義屬性的原始程式碼控制，或您必須限制`Get`程序在多個屬性本身，嘗試移動陳述式，讀取屬性值的程式碼區域具有更佳存取方式來存取層級屬性。</span><span class="sxs-lookup"><span data-stu-id="13ed8-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ed8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13ed8-112">See Also</span></span>  
 [<span data-ttu-id="13ed8-113">屬性程序</span><span class="sxs-lookup"><span data-stu-id="13ed8-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="13ed8-114">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="13ed8-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
