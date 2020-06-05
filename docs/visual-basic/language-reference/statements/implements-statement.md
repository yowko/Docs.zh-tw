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
ms.openlocfilehash: 7fb43934d8c200ff29b1caf63cec830b2c6633ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404546"
---
# <a name="implements-statement"></a><span data-ttu-id="abce5-102">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="abce5-102">Implements Statement</span></span>
<span data-ttu-id="abce5-103">指定一個或多個介面或介面成員，必須在其出現所在的類別或結構定義中執行。</span><span class="sxs-lookup"><span data-stu-id="abce5-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abce5-104">語法</span><span class="sxs-lookup"><span data-stu-id="abce5-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="abce5-105">組件</span><span class="sxs-lookup"><span data-stu-id="abce5-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="abce5-106">必要。</span><span class="sxs-lookup"><span data-stu-id="abce5-106">Required.</span></span> <span data-ttu-id="abce5-107">介面，其屬性、程式和事件會由類別或結構中的對應成員來執行。</span><span class="sxs-lookup"><span data-stu-id="abce5-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="abce5-108">必要。</span><span class="sxs-lookup"><span data-stu-id="abce5-108">Required.</span></span> <span data-ttu-id="abce5-109">正在執行之介面的成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abce5-110">備註</span><span class="sxs-lookup"><span data-stu-id="abce5-110">Remarks</span></span>  
 <span data-ttu-id="abce5-111">「介面」（interface）是原型的集合，代表介面封裝的成員（屬性、程式和事件）。</span><span class="sxs-lookup"><span data-stu-id="abce5-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="abce5-112">介面只包含成員的宣告;類別和結構會執行這些成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="abce5-113">如需詳細資訊，請參閱[介面](../../programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="abce5-113">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="abce5-114">`Implements`語句必須緊接在 `Class` 或語句之後 `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="abce5-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="abce5-115">當您執行介面時，您必須執行介面中宣告的所有成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="abce5-116">省略任何成員會被視為語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="abce5-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="abce5-117">若要執行個別成員， [Implements](implements-clause.md) `Implements` 當您在類別或結構中宣告成員時，可以指定 Implements 關鍵字（與語句分開）。</span><span class="sxs-lookup"><span data-stu-id="abce5-117">To implement an individual member, you specify the [Implements](implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="abce5-118">如需詳細資訊，請參閱[介面](../../programming-guide/language-features/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="abce5-118">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="abce5-119">類別可以使用屬性和程式的[私](../modifiers/private.md)用實作為，但只有將實做類別的實例轉換成宣告為介面類別型的變數，才能存取這些成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-119">Classes can use [Private](../modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abce5-120">範例</span><span class="sxs-lookup"><span data-stu-id="abce5-120">Example</span></span>  
 <span data-ttu-id="abce5-121">下列範例顯示如何使用 `Implements` 語句來執行介面的成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="abce5-122">它會 `ICustomerInfo` 使用事件、屬性和程式來定義名為的介面。</span><span class="sxs-lookup"><span data-stu-id="abce5-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="abce5-123">類別會執行 `customerInfo` 介面中定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="abce5-124">請注意，類別會 `customerInfo` `Implements` 在個別的源程式碼上使用語句，表示該類別會執行介面的所有成員 `ICustomerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="abce5-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="abce5-125">然後，類別中的每個成員 `Implements` 都會使用關鍵字做為其成員宣告的一部分，以表示它會實作為該介面成員。</span><span class="sxs-lookup"><span data-stu-id="abce5-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abce5-126">範例</span><span class="sxs-lookup"><span data-stu-id="abce5-126">Example</span></span>  
 <span data-ttu-id="abce5-127">下列兩個程式顯示如何使用上述範例中所實的介面。</span><span class="sxs-lookup"><span data-stu-id="abce5-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="abce5-128">若要測試執行，請將這些程式新增至您的專案，並呼叫程式 `testImplements` 。</span><span class="sxs-lookup"><span data-stu-id="abce5-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="abce5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abce5-129">See also</span></span>

- [<span data-ttu-id="abce5-130">實作</span><span class="sxs-lookup"><span data-stu-id="abce5-130">Implements</span></span>](implements-clause.md)
- [<span data-ttu-id="abce5-131">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="abce5-131">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="abce5-132">介面</span><span class="sxs-lookup"><span data-stu-id="abce5-132">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
