---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d384986e42ee69a0f425c1590599aa2c82bc856
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="78276-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78276-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="78276-103">指定類別可用只能當作基底類別，而且您無法直接從它建立物件。</span><span class="sxs-lookup"><span data-stu-id="78276-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78276-104">備註</span><span class="sxs-lookup"><span data-stu-id="78276-104">Remarks</span></span>  
 <span data-ttu-id="78276-105">目的*基底類別*(也稱為*抽象類別*) 是定義所衍生自它的所有類別通用的功能。</span><span class="sxs-lookup"><span data-stu-id="78276-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="78276-106">這可以節省衍生的類別不必重新定義通用的項目。</span><span class="sxs-lookup"><span data-stu-id="78276-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="78276-107">在某些情況下，此常用功能不完整到足以讓可使用的物件，而且每個衍生的類別定義遺漏的功能。</span><span class="sxs-lookup"><span data-stu-id="78276-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="78276-108">在這種情況下，您會想使用的程式碼，只能從衍生類別中建立物件。</span><span class="sxs-lookup"><span data-stu-id="78276-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="78276-109">您使用`MustInherit`強制這個基底類別。</span><span class="sxs-lookup"><span data-stu-id="78276-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="78276-110">另一個用途`MustInherit`類別是要限制一組相關的類別變數。</span><span class="sxs-lookup"><span data-stu-id="78276-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="78276-111">您可以定義基底類別，並從它衍生所有相關的類別。</span><span class="sxs-lookup"><span data-stu-id="78276-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="78276-112">基底類別不需要提供通用於所有的衍生類別中，任何功能，但它可以做為將值指派給變數的篩選。</span><span class="sxs-lookup"><span data-stu-id="78276-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="78276-113">如果您使用的程式碼會宣告一個變數為基底類別，Visual Basic 可讓您從一個衍生類別的物件只指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="78276-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="78276-114">.NET Framework 會定義數個`MustInherit`類別，其間<xref:System.Array>， <xref:System.Enum>，和<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="78276-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="78276-115"><xref:System.ValueType>是基底類別，以限制變數的範例。</span><span class="sxs-lookup"><span data-stu-id="78276-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="78276-116">所有實值型別衍生自<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="78276-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="78276-117">如果您將變數宣告為<xref:System.ValueType>，您可以指派只有實值類型給該變數。</span><span class="sxs-lookup"><span data-stu-id="78276-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="78276-118">規則</span><span class="sxs-lookup"><span data-stu-id="78276-118">Rules</span></span>  
  
-   <span data-ttu-id="78276-119">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="78276-119">**Declaration Context.**</span></span> <span data-ttu-id="78276-120">您可以使用`MustInherit`只有`Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="78276-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="78276-121">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="78276-121">**Combined Modifiers.**</span></span> <span data-ttu-id="78276-122">您無法指定`MustInherit`搭配`NotInheritable`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="78276-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78276-123">範例</span><span class="sxs-lookup"><span data-stu-id="78276-123">Example</span></span>  
 <span data-ttu-id="78276-124">下列範例說明強制的繼承和強制覆寫。</span><span class="sxs-lookup"><span data-stu-id="78276-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="78276-125">基底類別`shape`定義的變數， `acrossLine`。</span><span class="sxs-lookup"><span data-stu-id="78276-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="78276-126">類別`circle`和`square`衍生自`shape`。</span><span class="sxs-lookup"><span data-stu-id="78276-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="78276-127">它們繼承的定義`acrossLine`，但它們必須定義函式`area`因為該計算不同的每一種圖形。</span><span class="sxs-lookup"><span data-stu-id="78276-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="78276-128">您可以宣告`shape1`和`shape2`類型`shape`。</span><span class="sxs-lookup"><span data-stu-id="78276-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="78276-129">不過，您無法建立從物件`shape`因為其欠缺函式的功能`area`且標示`MustInherit`。</span><span class="sxs-lookup"><span data-stu-id="78276-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="78276-130">因為它們會宣告為`shape`，變數`shape1`和`shape2`限於從衍生類別物件`circle`和`square`。</span><span class="sxs-lookup"><span data-stu-id="78276-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="78276-131">Visual Basic 不允許您將任何其他物件指派給這些變數時，它將提供高層級的型別安全。</span><span class="sxs-lookup"><span data-stu-id="78276-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="78276-132">使用方式</span><span class="sxs-lookup"><span data-stu-id="78276-132">Usage</span></span>  
 <span data-ttu-id="78276-133">`MustInherit`修飾詞可用於此內容：</span><span class="sxs-lookup"><span data-stu-id="78276-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="78276-134">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="78276-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="78276-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78276-135">See Also</span></span>  
 [<span data-ttu-id="78276-136">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="78276-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="78276-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="78276-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="78276-138">關鍵字</span><span class="sxs-lookup"><span data-stu-id="78276-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="78276-139">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="78276-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
