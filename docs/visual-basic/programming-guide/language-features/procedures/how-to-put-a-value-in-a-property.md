---
title: HOW TO：將值放在屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: e6aee5ea36c0315d5b01ae2734d17c9e7dab8e93
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341851"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="bd9e5-102">HOW TO：將值放在屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd9e5-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="bd9e5-103">您將屬性名稱放在指派陳述式左邊值儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="bd9e5-104">屬性的`Set`程序會將儲存的值，但您未明確呼叫它的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="bd9e5-105">就像您使用變數，您可以使用屬性。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="bd9e5-106">Visual Basic 呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="bd9e5-107">若要儲存在屬性中的值</span><span class="sxs-lookup"><span data-stu-id="bd9e5-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="bd9e5-108">使用指派陳述式左邊的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="bd9e5-109">下列範例會設定值的 Visual Basic`TimeOfDay`屬性到中午，隱含地呼叫其`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="bd9e5-110">如果此屬性會接受引數，請遵循使用括號來括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="bd9e5-111">如果不有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="bd9e5-112">以括弧括住，並以逗號分隔的引數清單括住的引數。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="bd9e5-113">請確定您提供的引數的屬性會定義的對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="bd9e5-114">指派陳述式右側所產生的值會儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="bd9e5-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9e5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd9e5-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="bd9e5-116">屬性程序</span><span class="sxs-lookup"><span data-stu-id="bd9e5-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="bd9e5-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="bd9e5-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bd9e5-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="bd9e5-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="bd9e5-119">Visual Basic 中屬性和變數的差別</span><span class="sxs-lookup"><span data-stu-id="bd9e5-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="bd9e5-120">HOW TO：建立屬性</span><span class="sxs-lookup"><span data-stu-id="bd9e5-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="bd9e5-121">HOW TO：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="bd9e5-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="bd9e5-122">HOW TO：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="bd9e5-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="bd9e5-123">HOW TO：宣告，並在 Visual Basic 中呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="bd9e5-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="bd9e5-124">HOW TO：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="bd9e5-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
