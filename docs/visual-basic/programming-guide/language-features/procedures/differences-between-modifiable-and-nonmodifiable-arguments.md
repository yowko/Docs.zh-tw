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
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="61ae0-102">可修改引數和不可修改引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61ae0-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="61ae0-103">When you call a procedure, you typically pass one or more arguments to it.</span><span class="sxs-lookup"><span data-stu-id="61ae0-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="61ae0-104">Each argument corresponds to an underlying programming element.</span><span class="sxs-lookup"><span data-stu-id="61ae0-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="61ae0-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span><span class="sxs-lookup"><span data-stu-id="61ae0-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="61ae0-106">Modifiable and Nonmodifiable Elements</span><span class="sxs-lookup"><span data-stu-id="61ae0-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="61ae0-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span><span class="sxs-lookup"><span data-stu-id="61ae0-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="61ae0-108">The following table lists modifiable and nonmodifiable programming elements.</span><span class="sxs-lookup"><span data-stu-id="61ae0-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="61ae0-109">Modifiable elements</span><span class="sxs-lookup"><span data-stu-id="61ae0-109">Modifiable elements</span></span>|<span data-ttu-id="61ae0-110">Nonmodifiable elements</span><span class="sxs-lookup"><span data-stu-id="61ae0-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="61ae0-111">Local variables (declared inside procedures), including object variables, except for read-only</span><span class="sxs-lookup"><span data-stu-id="61ae0-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="61ae0-112">Read-only variables, fields, and properties</span><span class="sxs-lookup"><span data-stu-id="61ae0-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="61ae0-113">Fields (member variables of modules, classes, and structures), except for read-only</span><span class="sxs-lookup"><span data-stu-id="61ae0-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="61ae0-114">Constants and literals</span><span class="sxs-lookup"><span data-stu-id="61ae0-114">Constants and literals</span></span>|  
|<span data-ttu-id="61ae0-115">Properties, except for read-only</span><span class="sxs-lookup"><span data-stu-id="61ae0-115">Properties, except for read-only</span></span>|<span data-ttu-id="61ae0-116">Enumeration members</span><span class="sxs-lookup"><span data-stu-id="61ae0-116">Enumeration members</span></span>|  
|<span data-ttu-id="61ae0-117">Array elements</span><span class="sxs-lookup"><span data-stu-id="61ae0-117">Array elements</span></span>|<span data-ttu-id="61ae0-118">Expressions (even if their elements are modifiable)</span><span class="sxs-lookup"><span data-stu-id="61ae0-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="61ae0-119">Modifiable and Nonmodifiable Arguments</span><span class="sxs-lookup"><span data-stu-id="61ae0-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="61ae0-120">A *modifiable argument* is one with a modifiable underlying element.</span><span class="sxs-lookup"><span data-stu-id="61ae0-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="61ae0-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="61ae0-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="61ae0-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="61ae0-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="61ae0-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span><span class="sxs-lookup"><span data-stu-id="61ae0-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="61ae0-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span><span class="sxs-lookup"><span data-stu-id="61ae0-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="61ae0-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span><span class="sxs-lookup"><span data-stu-id="61ae0-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ae0-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="61ae0-126">See also</span></span>

- [<span data-ttu-id="61ae0-127">程序</span><span class="sxs-lookup"><span data-stu-id="61ae0-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="61ae0-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="61ae0-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="61ae0-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="61ae0-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="61ae0-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="61ae0-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="61ae0-131">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="61ae0-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="61ae0-132">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="61ae0-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="61ae0-133">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="61ae0-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="61ae0-134">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="61ae0-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="61ae0-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="61ae0-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="61ae0-136">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="61ae0-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
