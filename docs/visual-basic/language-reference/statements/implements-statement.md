---
title: Implements 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 805813506b957afb326c71ee4bbb15837726e4e5
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244734"
---
# <a name="implements-statement"></a><span data-ttu-id="dfcb0-102">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="dfcb0-102">Implements Statement</span></span>
<span data-ttu-id="dfcb0-103">指定一個或多個介面，或介面成員必須實作在類別中出現的結構定義。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfcb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfcb0-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="dfcb0-105">組件</span><span class="sxs-lookup"><span data-stu-id="dfcb0-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="dfcb0-106">必要。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-106">Required.</span></span> <span data-ttu-id="dfcb0-107">其屬性、 程序和事件會由對應的成員，在類別或結構實作介面。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="dfcb0-108">必要。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-108">Required.</span></span> <span data-ttu-id="dfcb0-109">目前正在實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfcb0-110">備註</span><span class="sxs-lookup"><span data-stu-id="dfcb0-110">Remarks</span></span>  
 <span data-ttu-id="dfcb0-111">介面是集合的原型代表的成員 （屬性、 程序和事件） 封裝的介面。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="dfcb0-112">介面包含宣告的成員;類別和結構實作這些成員。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="dfcb0-113">如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="dfcb0-114">`Implements`陳述式必須緊接`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="dfcb0-115">當您實作的介面時，您必須實作的介面中宣告的所有成員。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="dfcb0-116">省略任何成員會被視為語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="dfcb0-117">若要實作的個別成員，指定[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)關鍵字 (這是分開`Implements`陳述式) 當您宣告類別或結構中的成員。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="dfcb0-118">如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="dfcb0-119">類別可以使用[私人](../../../visual-basic/language-reference/modifiers/private.md)實作的屬性和程序，但這些成員都只能由實作類別的執行個體放入變數宣告為介面的型別轉型存取。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfcb0-120">範例</span><span class="sxs-lookup"><span data-stu-id="dfcb0-120">Example</span></span>  
 <span data-ttu-id="dfcb0-121">下列範例示範如何使用`Implements`陳述式來實作介面的成員。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="dfcb0-122">它會定義名為的介面`ICustomerInfo`事件、 屬性，與程序。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="dfcb0-123">此類別`customerInfo`實作介面中定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="dfcb0-124">請注意，類別`customerInfo`會使用`Implements`陳述式來指示此類別會實作的所有成員的個別的原始程式碼行上`ICustomerInfo`介面。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="dfcb0-125">接著會使用類別中的每個成員`Implements`關鍵字做為其成員宣告，以表示它會實作該介面成員的一部分。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfcb0-126">範例</span><span class="sxs-lookup"><span data-stu-id="dfcb0-126">Example</span></span>  
 <span data-ttu-id="dfcb0-127">下列兩個程序顯示如何使用在上述範例中實作的介面。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="dfcb0-128">若要測試實作，將這些程序新增到專案，並呼叫`testImplements`程序。</span><span class="sxs-lookup"><span data-stu-id="dfcb0-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dfcb0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfcb0-129">See Also</span></span>  
 [<span data-ttu-id="dfcb0-130">Implements</span><span class="sxs-lookup"><span data-stu-id="dfcb0-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [<span data-ttu-id="dfcb0-131">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="dfcb0-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="dfcb0-132">介面</span><span class="sxs-lookup"><span data-stu-id="dfcb0-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
