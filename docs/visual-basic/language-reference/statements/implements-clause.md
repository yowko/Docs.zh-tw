---
title: Implements 子句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="74710-102">Implements 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74710-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="74710-103">表示類別或結構的成員提供介面中定義之成員的實作。</span><span class="sxs-lookup"><span data-stu-id="74710-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74710-104">備註</span><span class="sxs-lookup"><span data-stu-id="74710-104">Remarks</span></span>  
<span data-ttu-id="74710-105">`Implements`關鍵字不相同[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="74710-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="74710-106">您使用`Implements`陳述式，以指定的類別或結構實作一或多個介面，您所使用之每個成員然後`Implements`關鍵字來指定哪個介面和成員實作。</span><span class="sxs-lookup"><span data-stu-id="74710-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="74710-107">如果類別或結構實作介面時，其必須包括`Implements`陳述式之後立即[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)或[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)，而且它必須實作所有成員介面定義。</span><span class="sxs-lookup"><span data-stu-id="74710-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="74710-108">重新實作</span><span class="sxs-lookup"><span data-stu-id="74710-108">Reimplementation</span></span>  
<span data-ttu-id="74710-109">在衍生類別中，您可以重新實作介面成員的基底類別實作的。</span><span class="sxs-lookup"><span data-stu-id="74710-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="74710-110">這是覆寫基底類別成員，在下列方面不同：</span><span class="sxs-lookup"><span data-stu-id="74710-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="74710-111">基底類別成員不需要是[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)必須重新實作。</span><span class="sxs-lookup"><span data-stu-id="74710-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="74710-112">您可以重新實作的成員使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="74710-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="74710-113">`Implements`關鍵字可以使用下列內容：</span><span class="sxs-lookup"><span data-stu-id="74710-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="74710-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="74710-115">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="74710-116">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="74710-117">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="74710-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74710-118">See Also</span></span>  
 [<span data-ttu-id="74710-119">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="74710-120">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="74710-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="74710-122">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="74710-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
