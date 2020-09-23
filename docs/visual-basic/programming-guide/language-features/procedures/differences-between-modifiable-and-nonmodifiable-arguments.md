---
title: 可修改引數和不可修改引數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 662ad3039bb3fd5c44847d5b2a97a033a18ad063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071955"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="cda8d-102">可修改引數和不可修改引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cda8d-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>

<span data-ttu-id="cda8d-103">當您呼叫程式時，通常會將一個或多個引數傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="cda8d-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="cda8d-104">每個引數都對應至基礎程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="cda8d-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="cda8d-105">基礎元素和引數本身可以是可修改或不可修改的。</span><span class="sxs-lookup"><span data-stu-id="cda8d-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="cda8d-106">可修改和不可修改的元素</span><span class="sxs-lookup"><span data-stu-id="cda8d-106">Modifiable and Nonmodifiable Elements</span></span>  

 <span data-ttu-id="cda8d-107">程式設計專案可以是可 *修改*的專案，其值可能會變更，或在建立之後具有固定值的 *不可修改元素*。</span><span class="sxs-lookup"><span data-stu-id="cda8d-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="cda8d-108">下表列出可修改和不可修改的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="cda8d-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="cda8d-109">可修改的元素</span><span class="sxs-lookup"><span data-stu-id="cda8d-109">Modifiable elements</span></span>|<span data-ttu-id="cda8d-110">不可修改的元素</span><span class="sxs-lookup"><span data-stu-id="cda8d-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="cda8d-111">本機變數 (在程式) 內宣告，包括物件變數（唯讀除外）</span><span class="sxs-lookup"><span data-stu-id="cda8d-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="cda8d-112">唯讀變數、欄位和屬性</span><span class="sxs-lookup"><span data-stu-id="cda8d-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="cda8d-113">欄位 (模組、類別和結構) 的成員變數，但唯讀除外</span><span class="sxs-lookup"><span data-stu-id="cda8d-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="cda8d-114">常數和常值</span><span class="sxs-lookup"><span data-stu-id="cda8d-114">Constants and literals</span></span>|  
|<span data-ttu-id="cda8d-115">除了唯讀以外的屬性</span><span class="sxs-lookup"><span data-stu-id="cda8d-115">Properties, except for read-only</span></span>|<span data-ttu-id="cda8d-116">列舉成員</span><span class="sxs-lookup"><span data-stu-id="cda8d-116">Enumeration members</span></span>|  
|<span data-ttu-id="cda8d-117">陣列元素</span><span class="sxs-lookup"><span data-stu-id="cda8d-117">Array elements</span></span>|<span data-ttu-id="cda8d-118">運算式 (即使其元素可修改) </span><span class="sxs-lookup"><span data-stu-id="cda8d-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="cda8d-119">可修改和不可修改的引數</span><span class="sxs-lookup"><span data-stu-id="cda8d-119">Modifiable and Nonmodifiable Arguments</span></span>  

 <span data-ttu-id="cda8d-120">可 *修改的引數* 是具有可修改基礎元素的引數。</span><span class="sxs-lookup"><span data-stu-id="cda8d-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="cda8d-121">呼叫程式碼可以隨時儲存新值，而且如果您傳遞引數 [ByRef](../../../language-reference/modifiers/byref.md)，程式中的程式碼也可以修改呼叫程式碼中的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="cda8d-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="cda8d-122">*不可變引數*具有不可修改的基礎元素，或已傳遞[ByVal](../../../language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="cda8d-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="cda8d-123">程式無法修改呼叫程式碼中的基礎元素（即使它是可修改的專案）。</span><span class="sxs-lookup"><span data-stu-id="cda8d-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="cda8d-124">如果它是不可修改的元素，則呼叫程式碼本身無法修改它。</span><span class="sxs-lookup"><span data-stu-id="cda8d-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="cda8d-125">呼叫的程式可能會修改其不可變引數的本機複本，但該修改並不會影響呼叫程式碼中的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="cda8d-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda8d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cda8d-126">See also</span></span>

- [<span data-ttu-id="cda8d-127">程序</span><span class="sxs-lookup"><span data-stu-id="cda8d-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cda8d-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="cda8d-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cda8d-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="cda8d-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="cda8d-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="cda8d-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="cda8d-131">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="cda8d-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="cda8d-132">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="cda8d-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="cda8d-133">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="cda8d-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="cda8d-134">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="cda8d-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="cda8d-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="cda8d-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="cda8d-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="cda8d-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
