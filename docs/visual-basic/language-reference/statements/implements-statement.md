---
title: "Implements 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implements-statement"></a><span data-ttu-id="0d89c-102">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="0d89c-102">Implements Statement</span></span>
<span data-ttu-id="0d89c-103">指定一或多個介面，或必須在類別中實作的介面成員或結構定義中的出現。</span><span class="sxs-lookup"><span data-stu-id="0d89c-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d89c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d89c-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="0d89c-105">組件</span><span class="sxs-lookup"><span data-stu-id="0d89c-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="0d89c-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="0d89c-106">Required.</span></span> <span data-ttu-id="0d89c-107">其屬性、 程序和事件會由對應的成員類別或結構中實作介面。</span><span class="sxs-lookup"><span data-stu-id="0d89c-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="0d89c-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0d89c-108">Required.</span></span> <span data-ttu-id="0d89c-109">所實作之介面的成員。</span><span class="sxs-lookup"><span data-stu-id="0d89c-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d89c-110">備註</span><span class="sxs-lookup"><span data-stu-id="0d89c-110">Remarks</span></span>  
 <span data-ttu-id="0d89c-111">介面是集合的原型代表成員 （屬性、 程序和事件） 封裝的介面。</span><span class="sxs-lookup"><span data-stu-id="0d89c-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="0d89c-112">介面包含宣告的成員;類別和結構實作這些成員。</span><span class="sxs-lookup"><span data-stu-id="0d89c-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="0d89c-113">如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d89c-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="0d89c-114">`Implements`陳述式必須緊接`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0d89c-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="0d89c-115">當您實作的介面時，您必須實作介面中宣告的所有成員。</span><span class="sxs-lookup"><span data-stu-id="0d89c-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="0d89c-116">省略任何成員會被視為語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="0d89c-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="0d89c-117">若要實作的個別成員，指定[實作](../../../visual-basic/language-reference/statements/implements-clause.md)關鍵字 (也就是從個別`Implements`陳述式) 當您宣告類別或結構中的成員。</span><span class="sxs-lookup"><span data-stu-id="0d89c-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="0d89c-118">如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d89c-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="0d89c-119">類別可以使用[私人](../../../visual-basic/language-reference/modifiers/private.md)實作的屬性和程序，但這些成員都只能由實作類別的執行個體放入變數宣告為介面的型別轉型存取。</span><span class="sxs-lookup"><span data-stu-id="0d89c-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d89c-120">範例</span><span class="sxs-lookup"><span data-stu-id="0d89c-120">Example</span></span>  
 <span data-ttu-id="0d89c-121">下列範例示範如何使用`Implements`陳述式來實作介面的成員。</span><span class="sxs-lookup"><span data-stu-id="0d89c-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="0d89c-122">它會定義名為介面`ICustomerInfo`事件、 屬性，與程序。</span><span class="sxs-lookup"><span data-stu-id="0d89c-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="0d89c-123">類別`customerInfo`實作介面中定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="0d89c-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="0d89c-124">請注意，類別`customerInfo`使用`Implements`陳述式表示類別實作的所有成員的個別的原始程式碼行上`ICustomerInfo`介面。</span><span class="sxs-lookup"><span data-stu-id="0d89c-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="0d89c-125">在類別中的每個成員接著會使用`Implements`關鍵字做為其成員宣告，以表示它會實作該介面成員的一部分。</span><span class="sxs-lookup"><span data-stu-id="0d89c-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d89c-126">範例</span><span class="sxs-lookup"><span data-stu-id="0d89c-126">Example</span></span>  
 <span data-ttu-id="0d89c-127">下列兩個程序顯示如何使用上述範例中實作的介面。</span><span class="sxs-lookup"><span data-stu-id="0d89c-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="0d89c-128">若要測試的實作，將這些程序加入至您的專案，並呼叫`testImplements`程序。</span><span class="sxs-lookup"><span data-stu-id="0d89c-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0d89c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d89c-129">See Also</span></span>  
 [<span data-ttu-id="0d89c-130">Implements</span><span class="sxs-lookup"><span data-stu-id="0d89c-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [<span data-ttu-id="0d89c-131">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="0d89c-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="0d89c-132">介面</span><span class="sxs-lookup"><span data-stu-id="0d89c-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
