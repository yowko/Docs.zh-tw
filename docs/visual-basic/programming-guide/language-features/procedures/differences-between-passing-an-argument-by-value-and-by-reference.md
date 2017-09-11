---
title: "傳遞引數以傳值或傳址 (Visual Basic) 之間的差異 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 706c64cd316791a748e2b68fe406e34084b04d5a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="fbbd6-102">以傳值或傳址方式傳遞引數的差別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbbd6-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>
<span data-ttu-id="fbbd6-103">當您將一或多個引數傳遞至程序時，每個引數對應至呼叫程式碼基礎的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="fbbd6-104">您可以傳遞基礎項目的值，或者是它的參考。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="fbbd6-105">這稱為*傳遞機制*。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="fbbd6-106">以傳值方式傳遞</span><span class="sxs-lookup"><span data-stu-id="fbbd6-106">Passing by Value</span></span>  
 <span data-ttu-id="fbbd6-107">傳遞引數*值*藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的對應參數的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-107">You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="fbbd6-108">當您使用這個傳遞機制，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]基礎的程式設計項目的值複製程序中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-108">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="fbbd6-109">程序程式碼中呼叫的程式碼沒有任何存取權的基礎項目。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="fbbd6-110">傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="fbbd6-110">Passing by Reference</span></span>  
 <span data-ttu-id="fbbd6-111">傳遞引數*傳*藉由指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)程序定義中的對應參數的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-111">You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="fbbd6-112">當您使用這個傳遞機制，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供程序呼叫的程式碼中直接參考的基礎的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-112">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="fbbd6-113">傳遞機制和項目類型</span><span class="sxs-lookup"><span data-stu-id="fbbd6-113">Passing Mechanism and Element Type</span></span>  
 <span data-ttu-id="fbbd6-114">選擇的傳遞機制不相同的基礎項目類型分類。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="fbbd6-115">傳值或傳址方式傳遞是指什麼[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供給程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-115">Passing by value or by reference refers to what [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies to the procedure code.</span></span> <span data-ttu-id="fbbd6-116">實值型別或參考型別是指程式設計項目儲存在記憶體中的方式。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="fbbd6-117">不過，傳遞機制與項目型別是相互關聯。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="fbbd6-118">參考類型的值是記憶體中的其他資料的指標。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="fbbd6-119">這表示您傳值方式傳遞參考類型，當程序程式碼會有一個指標指向對應的項目資料，即使它無法存取對應的項目本身。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="fbbd6-120">例如，如果項目是陣列變數，程序程式碼無法存取變數本身，但它可以存取陣列成員。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="fbbd6-121">若要修改的能力</span><span class="sxs-lookup"><span data-stu-id="fbbd6-121">Ability to Modify</span></span>  
 <span data-ttu-id="fbbd6-122">傳遞時不可修改的項目做為引數，此程序可以永遠不會修改呼叫程式碼，是否傳遞`ByVal`或`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="fbbd6-123">對於可修改的項目下, 表摘要說明項目型別和傳遞機制之間的互動。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="fbbd6-124">項目類型</span><span class="sxs-lookup"><span data-stu-id="fbbd6-124">Element type</span></span>|<span data-ttu-id="fbbd6-125">傳遞`ByVal`</span><span class="sxs-lookup"><span data-stu-id="fbbd6-125">Passed `ByVal`</span></span>|<span data-ttu-id="fbbd6-126">傳遞`ByRef`</span><span class="sxs-lookup"><span data-stu-id="fbbd6-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="fbbd6-127">實值型別 （只包含一個值）</span><span class="sxs-lookup"><span data-stu-id="fbbd6-127">Value type (contains only a value)</span></span>|<span data-ttu-id="fbbd6-128">此程序無法變更或其任何成員的變數。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="fbbd6-129">此程序可以變更變數和其成員。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="fbbd6-130">參考型別 （包含類別或結構的執行個體的指標）</span><span class="sxs-lookup"><span data-stu-id="fbbd6-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="fbbd6-131">無法變更變數的程序，但可以變更它所指向的執行個體的成員。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="fbbd6-132">此程序可以變更變數和它所指向的執行個體的成員。</span><span class="sxs-lookup"><span data-stu-id="fbbd6-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbbd6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbbd6-133">See Also</span></span>  
 <span data-ttu-id="fbbd6-134">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="fbbd6-135"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="fbbd6-136"> [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-136"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="fbbd6-137"> [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-137"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="fbbd6-138"> [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-138"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="fbbd6-139"> [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="fbbd6-140"> [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="fbbd6-141"> [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-141"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="fbbd6-142"> [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="fbbd6-142"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="fbbd6-143"> [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="fbbd6-143"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
