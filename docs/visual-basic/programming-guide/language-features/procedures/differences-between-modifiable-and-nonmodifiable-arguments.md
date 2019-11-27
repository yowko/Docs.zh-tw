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
ms.openlocfilehash: 989795ee2cdd3a78b71bad4d95cf9b384c2719bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341382"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="e2d6c-102">可修改引數和不可修改引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2d6c-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="e2d6c-103">當您呼叫程式時，通常會傳遞一或多個引數給它。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="e2d6c-104">每個引數都會對應至基礎程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="e2d6c-105">基礎元素和引數本身都可以是可修改或不可修改的。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="e2d6c-106">可修改和不可修改的元素</span><span class="sxs-lookup"><span data-stu-id="e2d6c-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="e2d6c-107">程式設計專案可以是可*修改的元素*，其值可能會變更，或無法修改的*元素*，其在建立後已有固定值。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="e2d6c-108">下表列出可修改和不可修改的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="e2d6c-109">可修改的元素</span><span class="sxs-lookup"><span data-stu-id="e2d6c-109">Modifiable elements</span></span>|<span data-ttu-id="e2d6c-110">不可修改元素</span><span class="sxs-lookup"><span data-stu-id="e2d6c-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="e2d6c-111">本機變數（在程式內宣告），包括物件變數（唯讀除外）</span><span class="sxs-lookup"><span data-stu-id="e2d6c-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="e2d6c-112">唯讀變數、欄位和屬性</span><span class="sxs-lookup"><span data-stu-id="e2d6c-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="e2d6c-113">欄位（模組、類別和結構的成員變數），除了唯讀以外</span><span class="sxs-lookup"><span data-stu-id="e2d6c-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="e2d6c-114">常數和常值</span><span class="sxs-lookup"><span data-stu-id="e2d6c-114">Constants and literals</span></span>|  
|<span data-ttu-id="e2d6c-115">屬性，除了唯讀以外</span><span class="sxs-lookup"><span data-stu-id="e2d6c-115">Properties, except for read-only</span></span>|<span data-ttu-id="e2d6c-116">列舉成員</span><span class="sxs-lookup"><span data-stu-id="e2d6c-116">Enumeration members</span></span>|  
|<span data-ttu-id="e2d6c-117">陣列元素</span><span class="sxs-lookup"><span data-stu-id="e2d6c-117">Array elements</span></span>|<span data-ttu-id="e2d6c-118">運算式（即使它們的元素是可修改的）</span><span class="sxs-lookup"><span data-stu-id="e2d6c-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="e2d6c-119">可修改和不可修改的引數</span><span class="sxs-lookup"><span data-stu-id="e2d6c-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="e2d6c-120">可*修改的引數*是一個具有可修改的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="e2d6c-121">呼叫程式碼可以隨時儲存新的值，而且如果您傳遞引數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，程式中的程式碼也可以修改呼叫程式碼中的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="e2d6c-122">不可修改的*引數*具有無法修改的基礎元素，或已傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="e2d6c-123">程式無法修改呼叫程式碼中的基礎元素，即使它是可修改的元素。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="e2d6c-124">如果它是無法修改的元素，則呼叫程式碼本身無法加以修改。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="e2d6c-125">被呼叫的程式可能會修改其不可變引數的本機複本，但該修改不會影響呼叫程式碼中的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="e2d6c-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d6c-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2d6c-126">See also</span></span>

- [<span data-ttu-id="e2d6c-127">程序</span><span class="sxs-lookup"><span data-stu-id="e2d6c-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e2d6c-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="e2d6c-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e2d6c-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="e2d6c-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="e2d6c-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e2d6c-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="e2d6c-131">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="e2d6c-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="e2d6c-132">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="e2d6c-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="e2d6c-133">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="e2d6c-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="e2d6c-134">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e2d6c-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="e2d6c-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e2d6c-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="e2d6c-136">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="e2d6c-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
