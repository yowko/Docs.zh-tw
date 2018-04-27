---
title: 以傳值或傳址方式傳遞引數的差別 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f733b4fd50612292c0c4ac7195304d99ae2dbea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="b5f06-102">以傳值或傳址方式傳遞引數的差別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5f06-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>
<span data-ttu-id="b5f06-103">當您將一或多個引數傳遞至程序時，每個引數會對應至基礎的程式設計項目，呼叫程式碼中。</span><span class="sxs-lookup"><span data-stu-id="b5f06-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="b5f06-104">您可以將這個基礎元素的值，或者是它的參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="b5f06-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="b5f06-105">這稱為*傳遞機制*。</span><span class="sxs-lookup"><span data-stu-id="b5f06-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="b5f06-106">以傳值方式傳遞</span><span class="sxs-lookup"><span data-stu-id="b5f06-106">Passing by Value</span></span>  
 <span data-ttu-id="b5f06-107">傳遞引數*值*藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的對應參數的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b5f06-107">You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="b5f06-108">當您使用這個傳遞機制時，Visual Basic 會將基礎的程式設計項目的值複製至程序中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="b5f06-108">When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="b5f06-109">程序程式碼呼叫的程式碼中沒有任何存取的基礎項目。</span><span class="sxs-lookup"><span data-stu-id="b5f06-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="b5f06-110">傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="b5f06-110">Passing by Reference</span></span>  
 <span data-ttu-id="b5f06-111">傳遞引數*傳*藉由指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)程序定義中的對應參數的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b5f06-111">You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="b5f06-112">當您使用這個傳遞機制時，Visual Basic 提供的程序的直接參考的基礎的程式設計項目呼叫的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="b5f06-112">When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="b5f06-113">傳遞機制以及項目類型</span><span class="sxs-lookup"><span data-stu-id="b5f06-113">Passing Mechanism and Element Type</span></span>  
 <span data-ttu-id="b5f06-114">選擇的傳遞機制並不相同的基礎項目類型分類。</span><span class="sxs-lookup"><span data-stu-id="b5f06-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="b5f06-115">傳值方式或傳址方式傳遞指的是 Visual Basic 提供的程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="b5f06-115">Passing by value or by reference refers to what Visual Basic supplies to the procedure code.</span></span> <span data-ttu-id="b5f06-116">實值類型或參考型別是指程式設計項目儲存在記憶體中的方式。</span><span class="sxs-lookup"><span data-stu-id="b5f06-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="b5f06-117">不過，傳遞機制以及項目類型是相互關聯。</span><span class="sxs-lookup"><span data-stu-id="b5f06-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="b5f06-118">參考類型的值是記憶體中的其他資料的指標。</span><span class="sxs-lookup"><span data-stu-id="b5f06-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="b5f06-119">這表示當傳值方式傳遞參考類型，程序程式碼會有一個指標指向基礎項目的資料，即使它無法存取對應的項目本身。</span><span class="sxs-lookup"><span data-stu-id="b5f06-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="b5f06-120">例如，如果項目是陣列變數，程序程式碼並沒有變數本身的存取權，但它可以存取陣列成員。</span><span class="sxs-lookup"><span data-stu-id="b5f06-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="b5f06-121">若要修改的能力</span><span class="sxs-lookup"><span data-stu-id="b5f06-121">Ability to Modify</span></span>  
 <span data-ttu-id="b5f06-122">當您將不可修改的項目傳遞做為引數時，程序可以永遠不會修改它呼叫的程式碼，是否在傳遞`ByVal`或`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="b5f06-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="b5f06-123">對於可修改的項目下, 表摘要說明的項目類型與傳遞機制之間的互動。</span><span class="sxs-lookup"><span data-stu-id="b5f06-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="b5f06-124">項目類型</span><span class="sxs-lookup"><span data-stu-id="b5f06-124">Element type</span></span>|<span data-ttu-id="b5f06-125">傳遞 `ByVal`</span><span class="sxs-lookup"><span data-stu-id="b5f06-125">Passed `ByVal`</span></span>|<span data-ttu-id="b5f06-126">傳遞 `ByRef`</span><span class="sxs-lookup"><span data-stu-id="b5f06-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="b5f06-127">實值型別 （只包含一個值）</span><span class="sxs-lookup"><span data-stu-id="b5f06-127">Value type (contains only a value)</span></span>|<span data-ttu-id="b5f06-128">程序無法變更變數或它的任何成員。</span><span class="sxs-lookup"><span data-stu-id="b5f06-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="b5f06-129">變數和其成員，可以變更程序。</span><span class="sxs-lookup"><span data-stu-id="b5f06-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="b5f06-130">參考類型 （包含的類別或結構的執行個體的指標）</span><span class="sxs-lookup"><span data-stu-id="b5f06-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="b5f06-131">無法變更變數的程序，但可以變更它所指向的執行個體的成員。</span><span class="sxs-lookup"><span data-stu-id="b5f06-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="b5f06-132">此程序可以變更的變數和它所指向的執行個體的成員。</span><span class="sxs-lookup"><span data-stu-id="b5f06-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5f06-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5f06-133">See Also</span></span>  
 [<span data-ttu-id="b5f06-134">程序</span><span class="sxs-lookup"><span data-stu-id="b5f06-134">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b5f06-135">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="b5f06-135">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b5f06-136">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="b5f06-136">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="b5f06-137">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="b5f06-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="b5f06-138">可修改引數和不可修改引數之間的差異</span><span class="sxs-lookup"><span data-stu-id="b5f06-138">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="b5f06-139">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="b5f06-139">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="b5f06-140">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="b5f06-140">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="b5f06-141">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="b5f06-141">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="b5f06-142">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="b5f06-142">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="b5f06-143">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="b5f06-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
