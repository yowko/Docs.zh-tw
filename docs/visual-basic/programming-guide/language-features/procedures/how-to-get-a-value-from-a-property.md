---
title: HOW TO：取得值，屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302929"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="81159-102">HOW TO：取得值，屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81159-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="81159-103">您可以在運算式中包含屬性名稱，以擷取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="81159-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="81159-104">屬性的`Get`程序會擷取值，但您未明確呼叫它的名稱。</span><span class="sxs-lookup"><span data-stu-id="81159-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="81159-105">就像您使用變數，您可以使用屬性。</span><span class="sxs-lookup"><span data-stu-id="81159-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="81159-106">Visual Basic 呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="81159-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="81159-107">若要擷取屬性的值</span><span class="sxs-lookup"><span data-stu-id="81159-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="81159-108">使用屬性名稱的運算式中您會使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="81159-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="81159-109">您可以使用屬性，您可以使用變數或常數的任何位置。</span><span class="sxs-lookup"><span data-stu-id="81159-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="81159-110">-或-</span><span class="sxs-lookup"><span data-stu-id="81159-110">-or-</span></span>  
  
     <span data-ttu-id="81159-111">使用下列相等的屬性名稱 (`=`) 登入在指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="81159-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="81159-112">下列範例會讀取值的 Visual Basic`Now`屬性，會隱含地呼叫其`Get`程序。</span><span class="sxs-lookup"><span data-stu-id="81159-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="81159-113">如果此屬性會接受引數，請遵循使用括號來括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="81159-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="81159-114">如果不有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="81159-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="81159-115">以括弧括住，並以逗號分隔的引數清單括住的引數。</span><span class="sxs-lookup"><span data-stu-id="81159-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="81159-116">請確定您提供的引數的屬性會定義的對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="81159-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="81159-117">如同變數運算式在參與的屬性的值或常數會或儲存在變數或指派陳述式左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="81159-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81159-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81159-118">See also</span></span>

- [<span data-ttu-id="81159-119">程序</span><span class="sxs-lookup"><span data-stu-id="81159-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="81159-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="81159-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="81159-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="81159-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="81159-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="81159-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="81159-123">Visual Basic 中屬性和變數的差別</span><span class="sxs-lookup"><span data-stu-id="81159-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="81159-124">HOW TO：建立屬性</span><span class="sxs-lookup"><span data-stu-id="81159-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="81159-125">HOW TO：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="81159-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="81159-126">HOW TO：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="81159-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="81159-127">HOW TO：宣告，並在 Visual Basic 中呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="81159-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="81159-128">HOW TO：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="81159-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
