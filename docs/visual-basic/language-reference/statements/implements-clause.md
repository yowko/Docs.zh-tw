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
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929322"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="7ca74-102">Implements 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ca74-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="7ca74-103">表示類別或結構成員正為介面中定義的成員提供執行。</span><span class="sxs-lookup"><span data-stu-id="7ca74-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ca74-104">備註</span><span class="sxs-lookup"><span data-stu-id="7ca74-104">Remarks</span></span>  
<span data-ttu-id="7ca74-105">關鍵字與[Implements 語句不同。](../../../visual-basic/language-reference/statements/implements-statement.md) `Implements`</span><span class="sxs-lookup"><span data-stu-id="7ca74-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="7ca74-106">您可以使用`Implements`語句來指定類別或結構會執行一或多個介面，然後針對每個成員`Implements`使用關鍵字來指定它所要執行的介面和成員。</span><span class="sxs-lookup"><span data-stu-id="7ca74-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="7ca74-107">如果類別或結構實作為介面，它必須在`Implements` [class 語句](../../../visual-basic/language-reference/statements/class-statement.md)或[structure 語句](../../../visual-basic/language-reference/statements/structure-statement.md)之後加入語句，而且它必須執行介面所定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="7ca74-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="7ca74-108">重新實作</span><span class="sxs-lookup"><span data-stu-id="7ca74-108">Reimplementation</span></span>  
<span data-ttu-id="7ca74-109">在衍生類別中，您可以重新執行基類已實作為的介面成員。</span><span class="sxs-lookup"><span data-stu-id="7ca74-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="7ca74-110">這與覆寫基類成員的方式不同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ca74-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="7ca74-111">基類成員不需要是可覆[寫](../../../visual-basic/language-reference/modifiers/overridable.md)的根據重新實作。</span><span class="sxs-lookup"><span data-stu-id="7ca74-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="7ca74-112">您可以使用不同的名稱來重新實現成員。</span><span class="sxs-lookup"><span data-stu-id="7ca74-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="7ca74-113">`Implements`關鍵字可用於下列內容：</span><span class="sxs-lookup"><span data-stu-id="7ca74-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="7ca74-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="7ca74-115">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="7ca74-116">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="7ca74-117">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ca74-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ca74-118">See also</span></span>

- [<span data-ttu-id="7ca74-119">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="7ca74-120">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="7ca74-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="7ca74-122">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ca74-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
