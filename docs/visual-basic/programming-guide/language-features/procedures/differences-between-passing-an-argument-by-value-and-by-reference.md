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
ms.openlocfilehash: f9fdb1e98fb827391b615f5fe0afd1ee43c9f8e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075040"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="6aaa9-102">以傳值或傳址方式傳遞引數的差別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6aaa9-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>

<span data-ttu-id="6aaa9-103">當您將一或多個引數傳遞至程式時，每個引數會對應至呼叫程式碼中的基礎程式設計專案。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="6aaa9-104">您可以傳遞這個基礎專案的值或它的參考。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="6aaa9-105">這就是所謂的 *傳遞機制*。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="6aaa9-106">以傳值方式傳遞</span><span class="sxs-lookup"><span data-stu-id="6aaa9-106">Passing by Value</span></span>  

 <span data-ttu-id="6aaa9-107">您可以在程序定義中為對應的參數指定[ByVal](../../../language-reference/modifiers/byval.md)關鍵字，以傳*值方式*傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-107">You pass an argument *by value* by specifying the [ByVal](../../../language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="6aaa9-108">當您使用此傳遞機制時，Visual Basic 會將基礎程式設計項目的值複製到程式中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-108">When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="6aaa9-109">程式碼無法存取呼叫程式碼中的基礎元素。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="6aaa9-110">以傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="6aaa9-110">Passing by Reference</span></span>  

 <span data-ttu-id="6aaa9-111">您可以在程序定義中為對應的參數指定[ByRef](../../../language-reference/modifiers/byref.md)關鍵字，以傳*址方式*傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-111">You pass an argument *by reference* by specifying the [ByRef](../../../language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="6aaa9-112">當您使用此傳遞機制時，Visual Basic 會為程式提供呼叫程式碼中基礎程式設計項目的直接參考。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-112">When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="6aaa9-113">傳遞機制和元素類型</span><span class="sxs-lookup"><span data-stu-id="6aaa9-113">Passing Mechanism and Element Type</span></span>  

 <span data-ttu-id="6aaa9-114">傳遞機制的選擇與基礎元素類型的分類不同。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="6aaa9-115">以傳值或傳址方式傳遞是指 Visual Basic 提供給程式程式碼的內容。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-115">Passing by value or by reference refers to what Visual Basic supplies to the procedure code.</span></span> <span data-ttu-id="6aaa9-116">實值型別或參考型別是指程式設計專案如何儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="6aaa9-117">不過，傳遞機制和元素類型是相互關聯的。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="6aaa9-118">參考型別的值是記憶體中其他位置的資料指標。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="6aaa9-119">這表示當您以傳值方式傳遞參考型別時，程式碼會有基礎專案資料的指標，即使它無法存取基礎元素本身也是一樣。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="6aaa9-120">例如，如果元素是陣列變數，程式碼就無法存取變數本身，但是可以存取陣列成員。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="6aaa9-121">修改的能力</span><span class="sxs-lookup"><span data-stu-id="6aaa9-121">Ability to Modify</span></span>  

 <span data-ttu-id="6aaa9-122">當您傳遞不可修改的專案做為引數時，程式永遠不會在呼叫程式碼中修改它（不論是否已傳遞 `ByVal` 或） `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="6aaa9-123">針對可修改的元素，下表摘要說明專案類型與傳遞機制之間的互動。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="6aaa9-124">項目類型</span><span class="sxs-lookup"><span data-stu-id="6aaa9-124">Element type</span></span>|<span data-ttu-id="6aaa9-125">通過 `ByVal`</span><span class="sxs-lookup"><span data-stu-id="6aaa9-125">Passed `ByVal`</span></span>|<span data-ttu-id="6aaa9-126">通過 `ByRef`</span><span class="sxs-lookup"><span data-stu-id="6aaa9-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="6aaa9-127">數值型別 (只包含值) </span><span class="sxs-lookup"><span data-stu-id="6aaa9-127">Value type (contains only a value)</span></span>|<span data-ttu-id="6aaa9-128">程式無法變更變數或其任何成員。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="6aaa9-129">程式可以變更變數和其成員。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="6aaa9-130">參考型別 (包含類別或結構實例的指標) </span><span class="sxs-lookup"><span data-stu-id="6aaa9-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="6aaa9-131">程式無法變更變數，但可以變更它所指向之實例的成員。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="6aaa9-132">程式可以變更它所指向之實例的變數和成員。</span><span class="sxs-lookup"><span data-stu-id="6aaa9-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6aaa9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aaa9-133">See also</span></span>

- [<span data-ttu-id="6aaa9-134">程序</span><span class="sxs-lookup"><span data-stu-id="6aaa9-134">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6aaa9-135">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="6aaa9-135">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6aaa9-136">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="6aaa9-136">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="6aaa9-137">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="6aaa9-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="6aaa9-138">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="6aaa9-138">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="6aaa9-139">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="6aaa9-139">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="6aaa9-140">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="6aaa9-140">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="6aaa9-141">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="6aaa9-141">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="6aaa9-142">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="6aaa9-142">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="6aaa9-143">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="6aaa9-143">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
