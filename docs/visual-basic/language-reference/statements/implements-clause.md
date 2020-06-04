---
title: Implements 子句
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
ms.openlocfilehash: 46ab1a1148e8d73d91293aedfc407e5efdc7cfb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404559"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="9fb2c-102">Implements 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fb2c-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="9fb2c-103">表示類別或結構成員正為介面中定義的成員提供執行。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fb2c-104">備註</span><span class="sxs-lookup"><span data-stu-id="9fb2c-104">Remarks</span></span>  
<span data-ttu-id="9fb2c-105">`Implements`關鍵字與[Implements 語句](implements-statement.md)不同。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-105">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="9fb2c-106">您可以使用 `Implements` 語句來指定類別或結構會執行一或多個介面，然後針對每個成員使用 `Implements` 關鍵字來指定它所要執行的介面和成員。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="9fb2c-107">如果類別或結構實作為介面，它必須在 `Implements` [class 語句](class-statement.md)或[structure 語句](structure-statement.md)之後加入語句，而且它必須執行介面所定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="9fb2c-108">重新實作</span><span class="sxs-lookup"><span data-stu-id="9fb2c-108">Reimplementation</span></span>  
<span data-ttu-id="9fb2c-109">在衍生類別中，您可以重新執行基類已實作為的介面成員。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="9fb2c-110">這與覆寫基類成員的方式不同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9fb2c-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="9fb2c-111">基類成員不需要是可覆[寫](../modifiers/overridable.md)的根據重新實作。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-111">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="9fb2c-112">您可以使用不同的名稱來重新實現成員。</span><span class="sxs-lookup"><span data-stu-id="9fb2c-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="9fb2c-113">`Implements`關鍵字可用於下列內容：</span><span class="sxs-lookup"><span data-stu-id="9fb2c-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="9fb2c-114">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-114">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="9fb2c-115">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-115">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="9fb2c-116">Property Statement</span><span class="sxs-lookup"><span data-stu-id="9fb2c-116">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="9fb2c-117">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-117">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9fb2c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fb2c-118">See also</span></span>

- [<span data-ttu-id="9fb2c-119">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-119">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="9fb2c-120">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-120">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="9fb2c-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-121">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="9fb2c-122">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="9fb2c-122">Structure Statement</span></span>](structure-statement.md)
