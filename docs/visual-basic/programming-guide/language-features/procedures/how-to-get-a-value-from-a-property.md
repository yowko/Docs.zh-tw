---
title: 如何：取得屬性值
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339820"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="3f80d-102">如何：取得屬性值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f80d-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="3f80d-103">您可以藉由在運算式中包含屬性名稱，來抓取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3f80d-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="3f80d-104">屬性的 `Get` 程式會抓取值，但您不會依名稱明確地呼叫它。</span><span class="sxs-lookup"><span data-stu-id="3f80d-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="3f80d-105">您可以使用屬性，就像使用變數一樣。</span><span class="sxs-lookup"><span data-stu-id="3f80d-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="3f80d-106">Visual Basic 會呼叫屬性的程式。</span><span class="sxs-lookup"><span data-stu-id="3f80d-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="3f80d-107">從屬性取得值</span><span class="sxs-lookup"><span data-stu-id="3f80d-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="3f80d-108">在運算式中使用屬性名稱，方法與使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="3f80d-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="3f80d-109">您可以在任何可使用變數或常數的地方使用屬性。</span><span class="sxs-lookup"><span data-stu-id="3f80d-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="3f80d-110">-或-</span><span class="sxs-lookup"><span data-stu-id="3f80d-110">-or-</span></span>  
  
     <span data-ttu-id="3f80d-111">在指派語句中的等號（`=`）後面，使用屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3f80d-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="3f80d-112">下列範例會讀取 Visual Basic `Now` 屬性的值，並隱含地呼叫其 `Get` 程式。</span><span class="sxs-lookup"><span data-stu-id="3f80d-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="3f80d-113">如果屬性接受引數，請在屬性名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="3f80d-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="3f80d-114">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="3f80d-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="3f80d-115">將引數放在括弧內的引數清單中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="3f80d-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="3f80d-116">請務必以屬性定義對應參數的相同順序來提供引數。</span><span class="sxs-lookup"><span data-stu-id="3f80d-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="3f80d-117">屬性的值會當做變數或常數來參與運算式，或是儲存在指派語句左側的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="3f80d-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f80d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f80d-118">See also</span></span>

- [<span data-ttu-id="3f80d-119">程序</span><span class="sxs-lookup"><span data-stu-id="3f80d-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3f80d-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="3f80d-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3f80d-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="3f80d-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3f80d-122">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="3f80d-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="3f80d-123">Visual Basic 中的屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="3f80d-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="3f80d-124">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="3f80d-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="3f80d-125">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="3f80d-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="3f80d-126">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="3f80d-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="3f80d-127">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="3f80d-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="3f80d-128">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="3f80d-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
