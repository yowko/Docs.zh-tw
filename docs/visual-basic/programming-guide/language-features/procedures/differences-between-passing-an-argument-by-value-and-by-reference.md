---
title: 以傳值或傳址方式傳遞引數的差別
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 84ec3bac2532b2cef72ddda347251bc987801c3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341226"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="e7d8d-102">以傳值或傳址方式傳遞引數的差別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7d8d-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>
<span data-ttu-id="e7d8d-103">當您將一或多個引數傳遞至程式時，每個引數都會對應至呼叫程式碼中的基礎程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="e7d8d-104">您可以傳遞這個基礎元素的值，或它的參考。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="e7d8d-105">這就是所謂的*傳遞機制*。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="e7d8d-106">以傳值方式傳遞</span><span class="sxs-lookup"><span data-stu-id="e7d8d-106">Passing by Value</span></span>  
 <span data-ttu-id="e7d8d-107">您可以藉由在程序定義中指定對應參數的[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)關鍵字，以傳*值*方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-107">You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="e7d8d-108">當您使用這個傳遞機制時，Visual Basic 會將基礎程式設計項目的值複製到程式中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-108">When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="e7d8d-109">程式碼沒有呼叫程式碼中基礎元素的任何存取權。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="e7d8d-110">以傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="e7d8d-110">Passing by Reference</span></span>  
 <span data-ttu-id="e7d8d-111">您可以在程序定義中指定對應參數的[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字，以傳*址方式*傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-111">You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="e7d8d-112">當您使用這個傳遞機制時，Visual Basic 可讓程式直接參考呼叫程式碼中的基礎程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-112">When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="e7d8d-113">傳遞機制和元素類型</span><span class="sxs-lookup"><span data-stu-id="e7d8d-113">Passing Mechanism and Element Type</span></span>  
 <span data-ttu-id="e7d8d-114">傳遞機制的選擇與基礎元素類型的分類不同。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="e7d8d-115">以傳值或傳址方式傳遞是指 Visual Basic 提供給程式碼的內容。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-115">Passing by value or by reference refers to what Visual Basic supplies to the procedure code.</span></span> <span data-ttu-id="e7d8d-116">實值型別或參考型別是指程式設計專案在記憶體中的儲存方式。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="e7d8d-117">不過，傳遞機制和元素類型是相互關聯的。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="e7d8d-118">參考型別的值是記憶體中其他位置的資料指標。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="e7d8d-119">這表示當您以傳值方式傳遞參考型別時，程式碼會有基礎專案資料的指標，即使它無法存取基礎元素本身也一樣。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="e7d8d-120">例如，如果元素是陣列變數，程式碼就不會有變數本身的存取權，但它可以存取陣列成員。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="e7d8d-121">能夠修改</span><span class="sxs-lookup"><span data-stu-id="e7d8d-121">Ability to Modify</span></span>  
 <span data-ttu-id="e7d8d-122">當您傳遞無法修改的元素做為引數時，不論是傳遞 `ByVal` 或 `ByRef`，程式都不能在呼叫程式碼中加以修改。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="e7d8d-123">對於可修改的元素，下表摘要說明專案類型與傳遞機制之間的互動。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="e7d8d-124">項目類型</span><span class="sxs-lookup"><span data-stu-id="e7d8d-124">Element type</span></span>|<span data-ttu-id="e7d8d-125">已通過 `ByVal`</span><span class="sxs-lookup"><span data-stu-id="e7d8d-125">Passed `ByVal`</span></span>|<span data-ttu-id="e7d8d-126">已通過 `ByRef`</span><span class="sxs-lookup"><span data-stu-id="e7d8d-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="e7d8d-127">實值型別（只包含值）</span><span class="sxs-lookup"><span data-stu-id="e7d8d-127">Value type (contains only a value)</span></span>|<span data-ttu-id="e7d8d-128">程式無法變更變數或其任何成員。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="e7d8d-129">程式可以變更變數及其成員。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="e7d8d-130">參考型別（包含類別或結構實例的指標）</span><span class="sxs-lookup"><span data-stu-id="e7d8d-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="e7d8d-131">程式無法變更變數，但是可以變更它所指向之實例的成員。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="e7d8d-132">此程式可以變更其指向之實例的變數和成員。</span><span class="sxs-lookup"><span data-stu-id="e7d8d-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7d8d-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7d8d-133">See also</span></span>

- [<span data-ttu-id="e7d8d-134">程序</span><span class="sxs-lookup"><span data-stu-id="e7d8d-134">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e7d8d-135">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="e7d8d-135">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e7d8d-136">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="e7d8d-136">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="e7d8d-137">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e7d8d-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="e7d8d-138">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="e7d8d-138">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="e7d8d-139">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="e7d8d-139">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="e7d8d-140">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="e7d8d-140">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="e7d8d-141">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e7d8d-141">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="e7d8d-142">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="e7d8d-142">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="e7d8d-143">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="e7d8d-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
