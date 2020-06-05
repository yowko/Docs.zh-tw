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
ms.openlocfilehash: 2c92cd4a869acbb7c8c52fbf4117112967386498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387890"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="99ac9-102">如何：取得屬性值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99ac9-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="99ac9-103">您可以藉由在運算式中包含屬性名稱，來抓取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="99ac9-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="99ac9-104">屬性的程式會抓取 `Get` 值，但您不會依名稱明確地呼叫它。</span><span class="sxs-lookup"><span data-stu-id="99ac9-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="99ac9-105">您可以使用屬性，就像使用變數一樣。</span><span class="sxs-lookup"><span data-stu-id="99ac9-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="99ac9-106">Visual Basic 會呼叫屬性的程式。</span><span class="sxs-lookup"><span data-stu-id="99ac9-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="99ac9-107">從屬性取得值</span><span class="sxs-lookup"><span data-stu-id="99ac9-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="99ac9-108">在運算式中使用屬性名稱，方法與使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="99ac9-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="99ac9-109">您可以在任何可使用變數或常數的地方使用屬性。</span><span class="sxs-lookup"><span data-stu-id="99ac9-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="99ac9-110">-或-</span><span class="sxs-lookup"><span data-stu-id="99ac9-110">-or-</span></span>  
  
     <span data-ttu-id="99ac9-111">在指派語句中的等號（）後面，使用屬性名稱 `=` 。</span><span class="sxs-lookup"><span data-stu-id="99ac9-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="99ac9-112">下列範例會讀取 Visual Basic 屬性的值 `Now` ，並隱含地呼叫其程式 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="99ac9-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="99ac9-113">如果屬性接受引數，請在屬性名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="99ac9-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="99ac9-114">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="99ac9-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="99ac9-115">將引數放在括弧內的引數清單中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="99ac9-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="99ac9-116">請務必以屬性定義對應參數的相同順序來提供引數。</span><span class="sxs-lookup"><span data-stu-id="99ac9-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="99ac9-117">屬性的值會當做變數或常數來參與運算式，或是儲存在指派語句左側的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="99ac9-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ac9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99ac9-118">See also</span></span>

- [<span data-ttu-id="99ac9-119">程序</span><span class="sxs-lookup"><span data-stu-id="99ac9-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="99ac9-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="99ac9-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="99ac9-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="99ac9-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="99ac9-122">Property Statement</span><span class="sxs-lookup"><span data-stu-id="99ac9-122">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="99ac9-123">Visual Basic 中屬性和變數的差異</span><span class="sxs-lookup"><span data-stu-id="99ac9-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="99ac9-124">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="99ac9-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="99ac9-125">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="99ac9-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="99ac9-126">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="99ac9-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="99ac9-127">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="99ac9-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="99ac9-128">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="99ac9-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
