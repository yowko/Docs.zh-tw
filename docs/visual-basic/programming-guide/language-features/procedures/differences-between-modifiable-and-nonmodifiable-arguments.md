---
title: 可修改引數和不可修改引數之間的差異 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665945"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="6ad5e-102">可修改引數和不可修改引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ad5e-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="6ad5e-103">當您呼叫程序時，您通常會傳遞一或多個引數給它。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="6ad5e-104">每個引數會對應至基礎的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="6ad5e-105">基礎元素及引數本身可以是可修改或不可修改。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="6ad5e-106">可修改和不可修改的項目</span><span class="sxs-lookup"><span data-stu-id="6ad5e-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="6ad5e-107">程式設計項目可以是*可修改的項目*，且可以包含它的值變更，或有*不可修改的項目*，一旦建立之後，其中會包含固定的值。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="6ad5e-108">下表列出可修改和不可修改的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="6ad5e-109">可修改的項目</span><span class="sxs-lookup"><span data-stu-id="6ad5e-109">Modifiable elements</span></span>|<span data-ttu-id="6ad5e-110">不可修改的項目</span><span class="sxs-lookup"><span data-stu-id="6ad5e-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="6ad5e-111">本機變數 （在程序宣告），包括物件的變數，但唯讀除外</span><span class="sxs-lookup"><span data-stu-id="6ad5e-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="6ad5e-112">唯讀變數、 欄位和屬性</span><span class="sxs-lookup"><span data-stu-id="6ad5e-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="6ad5e-113">除了唯讀的欄位 （模組、 類別和結構的成員變數，）</span><span class="sxs-lookup"><span data-stu-id="6ad5e-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="6ad5e-114">常數和常值</span><span class="sxs-lookup"><span data-stu-id="6ad5e-114">Constants and literals</span></span>|  
|<span data-ttu-id="6ad5e-115">屬性，除了唯讀</span><span class="sxs-lookup"><span data-stu-id="6ad5e-115">Properties, except for read-only</span></span>|<span data-ttu-id="6ad5e-116">列舉型別成員</span><span class="sxs-lookup"><span data-stu-id="6ad5e-116">Enumeration members</span></span>|  
|<span data-ttu-id="6ad5e-117">陣列項目</span><span class="sxs-lookup"><span data-stu-id="6ad5e-117">Array elements</span></span>|<span data-ttu-id="6ad5e-118">運算式 （即使其元素都是可修改）</span><span class="sxs-lookup"><span data-stu-id="6ad5e-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="6ad5e-119">可修改和不可修改引數</span><span class="sxs-lookup"><span data-stu-id="6ad5e-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="6ad5e-120">A*可修改引數*是具有可修改的基礎項目。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="6ad5e-121">呼叫端程式碼可以在任何時間，儲存新的值，如果您傳遞的引數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，程序中的程式碼也可以修改呼叫程式碼對應的項目。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="6ad5e-122">A*不可修改引數*已經不可修改的基礎項目，或傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="6ad5e-123">此程序無法修改呼叫程式碼中，對應的項目，即使它是可修改的項目。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="6ad5e-124">如果它是不可修改的項目時，呼叫程式碼本身無法加以修改。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="6ad5e-125">呼叫的程序可能會修改為不可修改引數，其本機複本，但該修改並不會影響呼叫端程式碼對應的項目。</span><span class="sxs-lookup"><span data-stu-id="6ad5e-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad5e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad5e-126">See also</span></span>

- [<span data-ttu-id="6ad5e-127">程序</span><span class="sxs-lookup"><span data-stu-id="6ad5e-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6ad5e-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="6ad5e-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6ad5e-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="6ad5e-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="6ad5e-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="6ad5e-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="6ad5e-131">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="6ad5e-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="6ad5e-132">如何：程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="6ad5e-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="6ad5e-133">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="6ad5e-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="6ad5e-134">如何：強制以傳值方式傳遞的引數</span><span class="sxs-lookup"><span data-stu-id="6ad5e-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="6ad5e-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="6ad5e-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="6ad5e-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="6ad5e-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
