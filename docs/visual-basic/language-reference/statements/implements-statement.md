---
title: Implements 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: b982057d2094f807b68d5190dfad388fb9a2c65a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873242"
---
# <a name="implements-statement"></a><span data-ttu-id="62c89-102">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="62c89-102">Implements Statement</span></span>

<span data-ttu-id="62c89-103">指定必須在出現之類別或結構定義中實作為的一或多個介面或介面成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c89-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="62c89-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="62c89-105">組件</span><span class="sxs-lookup"><span data-stu-id="62c89-105">Parts</span></span>  

 `interfacename`  
 <span data-ttu-id="62c89-106">必要。</span><span class="sxs-lookup"><span data-stu-id="62c89-106">Required.</span></span> <span data-ttu-id="62c89-107">介面，其屬性、程式和事件是由類別或結構中的對應成員所執行。</span><span class="sxs-lookup"><span data-stu-id="62c89-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="62c89-108">必要。</span><span class="sxs-lookup"><span data-stu-id="62c89-108">Required.</span></span> <span data-ttu-id="62c89-109">正在執行之介面的成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62c89-110">備註</span><span class="sxs-lookup"><span data-stu-id="62c89-110">Remarks</span></span>  

 <span data-ttu-id="62c89-111">「介面」（interface）是代表介面所封裝)  (屬性、程式和事件之成員的原型集合。</span><span class="sxs-lookup"><span data-stu-id="62c89-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="62c89-112">介面只包含成員的宣告;類別和結構會執行這些成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="62c89-113">如需詳細資訊，請參閱[介面](../../programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="62c89-113">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="62c89-114">`Implements`語句必須緊接在 `Class` 或語句後面 `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="62c89-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="62c89-115">當您執行介面時，您必須執行介面中宣告的所有成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="62c89-116">省略任何成員都會被視為語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="62c89-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="62c89-117">若要執行個別成員，請指定 [Implements](implements-clause.md) 關鍵字 (`Implements` 當您在類別或結構中宣告成員時，會與語句) 分開。</span><span class="sxs-lookup"><span data-stu-id="62c89-117">To implement an individual member, you specify the [Implements](implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="62c89-118">如需詳細資訊，請參閱[介面](../../programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="62c89-118">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="62c89-119">類別可以使用屬性和程式的 [私](../modifiers/private.md) 用實作為，但這些成員只能藉由將實類別的實例轉換為宣告為介面型別的變數來存取。</span><span class="sxs-lookup"><span data-stu-id="62c89-119">Classes can use [Private](../modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62c89-120">範例</span><span class="sxs-lookup"><span data-stu-id="62c89-120">Example</span></span>  

 <span data-ttu-id="62c89-121">下列範例示範如何使用 `Implements` 語句來執行介面的成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="62c89-122">它會定義一個名為的介面，該介面 `ICustomerInfo` 具有事件、屬性和程式。</span><span class="sxs-lookup"><span data-stu-id="62c89-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="62c89-123">類別會執行 `customerInfo` 介面中定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="62c89-124">請注意，類別會 `customerInfo` `Implements` 在個別的源程式碼上使用語句，以指出該類別會實作為介面的所有成員 `ICustomerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="62c89-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="62c89-125">然後，類別中的每個成員 `Implements` 都會使用關鍵字做為其成員宣告的一部分，以表示它會執行該介面成員。</span><span class="sxs-lookup"><span data-stu-id="62c89-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62c89-126">範例</span><span class="sxs-lookup"><span data-stu-id="62c89-126">Example</span></span>  

 <span data-ttu-id="62c89-127">下列兩個程式示範如何使用在上述範例中所執行的介面。</span><span class="sxs-lookup"><span data-stu-id="62c89-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="62c89-128">若要測試執行，請將這些程式加入至您的專案，並呼叫程式 `testImplements` 。</span><span class="sxs-lookup"><span data-stu-id="62c89-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="62c89-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62c89-129">See also</span></span>

- [<span data-ttu-id="62c89-130">實作</span><span class="sxs-lookup"><span data-stu-id="62c89-130">Implements</span></span>](implements-clause.md)
- [<span data-ttu-id="62c89-131">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="62c89-131">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="62c89-132">介面</span><span class="sxs-lookup"><span data-stu-id="62c89-132">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
