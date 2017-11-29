---
title: "可修改引數和不可修改引數之間的差異 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="5298f-102">可修改引數和不可修改引數之間的差異 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5298f-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="5298f-103">當您呼叫程序時，通常會傳遞一或多個引數給它。</span><span class="sxs-lookup"><span data-stu-id="5298f-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="5298f-104">每個引數會對應至基礎的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="5298f-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="5298f-105">基礎項和引數本身可以是可修改或不可修改。</span><span class="sxs-lookup"><span data-stu-id="5298f-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="5298f-106">可修改和不可修改的項目</span><span class="sxs-lookup"><span data-stu-id="5298f-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="5298f-107">程式設計項目可以是*可修改的項目*，且可以包含其值已變更，或*不可修改的項目*，一旦建立之後具有固定的值。</span><span class="sxs-lookup"><span data-stu-id="5298f-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="5298f-108">下表列出可修改和不可修改的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="5298f-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="5298f-109">可修改的項目</span><span class="sxs-lookup"><span data-stu-id="5298f-109">Modifiable elements</span></span>|<span data-ttu-id="5298f-110">不可修改的項目</span><span class="sxs-lookup"><span data-stu-id="5298f-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="5298f-111">區域變數 （程序內宣告），包括物件變數，但唯讀</span><span class="sxs-lookup"><span data-stu-id="5298f-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="5298f-112">唯讀變數、 欄位和屬性</span><span class="sxs-lookup"><span data-stu-id="5298f-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="5298f-113">除了唯讀欄位 （模組、 類別和結構的成員變數，）</span><span class="sxs-lookup"><span data-stu-id="5298f-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="5298f-114">常數和常值</span><span class="sxs-lookup"><span data-stu-id="5298f-114">Constants and literals</span></span>|  
|<span data-ttu-id="5298f-115">除了唯讀屬性，</span><span class="sxs-lookup"><span data-stu-id="5298f-115">Properties, except for read-only</span></span>|<span data-ttu-id="5298f-116">列舉型別成員</span><span class="sxs-lookup"><span data-stu-id="5298f-116">Enumeration members</span></span>|  
|<span data-ttu-id="5298f-117">陣列項目</span><span class="sxs-lookup"><span data-stu-id="5298f-117">Array elements</span></span>|<span data-ttu-id="5298f-118">運算式 （即使其項目是可修改）</span><span class="sxs-lookup"><span data-stu-id="5298f-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="5298f-119">可修改和不可修改引數</span><span class="sxs-lookup"><span data-stu-id="5298f-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="5298f-120">A*可修改引數*是具有可修改的對應項目。</span><span class="sxs-lookup"><span data-stu-id="5298f-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="5298f-121">呼叫程式碼可以在任何時候，儲存新的值，如果您要傳入的引數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，程序中的程式碼也可以修改呼叫程式碼中對應的項目。</span><span class="sxs-lookup"><span data-stu-id="5298f-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="5298f-122">A*不可修改引數*具有不可修改的對應項目或是傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="5298f-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="5298f-123">此程序無法修改呼叫程式碼中，對應的項目，即使它是可修改的項目。</span><span class="sxs-lookup"><span data-stu-id="5298f-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="5298f-124">如果是不可修改的項目，呼叫程式碼本身不能修改它。</span><span class="sxs-lookup"><span data-stu-id="5298f-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="5298f-125">呼叫的程序可能會修改為不可修改引數，其本機副本，但修改不會影響呼叫的程式碼中對應的項目。</span><span class="sxs-lookup"><span data-stu-id="5298f-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5298f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5298f-126">See Also</span></span>  
 [<span data-ttu-id="5298f-127">程序</span><span class="sxs-lookup"><span data-stu-id="5298f-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5298f-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="5298f-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5298f-129">如何：將引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="5298f-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="5298f-130">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="5298f-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="5298f-131">以傳值或傳址方式傳遞引數的差別</span><span class="sxs-lookup"><span data-stu-id="5298f-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="5298f-132">如何：變更程序引數的值</span><span class="sxs-lookup"><span data-stu-id="5298f-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="5298f-133">如何：防止程序引數的值變更</span><span class="sxs-lookup"><span data-stu-id="5298f-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="5298f-134">如何：強制以傳值方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="5298f-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="5298f-135">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="5298f-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="5298f-136">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="5298f-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
