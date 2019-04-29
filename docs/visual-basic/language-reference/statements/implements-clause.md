---
title: Implements 子句 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 05de1d9f8966c17d84deba34f27819cce4aff3fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637756"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="0cbe3-102">Implements 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cbe3-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="0cbe3-103">表示類別或結構成員會提供介面中定義之成員的實作。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cbe3-104">備註</span><span class="sxs-lookup"><span data-stu-id="0cbe3-104">Remarks</span></span>  
<span data-ttu-id="0cbe3-105">`Implements`關鍵字不相同[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="0cbe3-106">您使用`Implements`陳述式來指定類別或結構實作一或多個介面，而且您所使用之每個成員然後`Implements`關鍵字來指定哪些介面的成員實作。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="0cbe3-107">如果類別或結構實作介面時，它必須包含`Implements`陳述式之後立即[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)或是[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)，而且它必須實作的所有成員由介面定義。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="0cbe3-108">重新實作</span><span class="sxs-lookup"><span data-stu-id="0cbe3-108">Reimplementation</span></span>  
<span data-ttu-id="0cbe3-109">在衍生類別中，您可以重新實作的基底類別已實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="0cbe3-110">這是覆寫基底類別成員，在下列方面不同：</span><span class="sxs-lookup"><span data-stu-id="0cbe3-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="0cbe3-111">基底類別成員不一定要[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)必須重新實作。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="0cbe3-112">您可以重新實作的成員使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cbe3-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="0cbe3-113">`Implements`關鍵字可以用在下列情況：</span><span class="sxs-lookup"><span data-stu-id="0cbe3-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="0cbe3-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="0cbe3-115">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="0cbe3-116">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="0cbe3-117">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0cbe3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cbe3-118">See also</span></span>

- [<span data-ttu-id="0cbe3-119">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="0cbe3-120">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="0cbe3-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="0cbe3-122">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0cbe3-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
