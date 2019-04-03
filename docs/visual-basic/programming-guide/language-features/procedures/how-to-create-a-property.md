---
title: HOW TO：建立屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 3e3f1168a983b2fa608cbadffba0531afef7c92b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816842"
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="23ff0-102">HOW TO：建立屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23ff0-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="23ff0-103">您將屬性定義之間`Property`陳述式和`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="23ff0-104">您在此定義中定義`Get`程序，`Set`程序，或兩者。</span><span class="sxs-lookup"><span data-stu-id="23ff0-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="23ff0-105">所有屬性的程式碼位於內這些程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="23ff0-106">`Get`程序會擷取屬性的值，而`Set`程序儲存值。</span><span class="sxs-lookup"><span data-stu-id="23ff0-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="23ff0-107">如果您想要讀取/寫入存取的屬性，您必須定義兩個程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="23ff0-108">唯讀屬性，您只會定義`Get`，和唯寫屬性，您只會定義`Set`。</span><span class="sxs-lookup"><span data-stu-id="23ff0-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="23ff0-109">若要建立屬性</span><span class="sxs-lookup"><span data-stu-id="23ff0-109">To create a property</span></span>  
  
1.  <span data-ttu-id="23ff0-110">之外任何屬性或程序，使用[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)，後面接著`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-110">Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="23ff0-111">如果屬性不接受參數，請依照下列`Property`關鍵字的程序中，則參數清單括號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="23ff0-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="23ff0-112">括號後面`As`子句來指定屬性的值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="23ff0-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="23ff0-113">您必須指定資料類型，即使是針對唯寫屬性。</span><span class="sxs-lookup"><span data-stu-id="23ff0-113">You must specify the data type even for a write-only property.</span></span>  
  
4.  <span data-ttu-id="23ff0-114">新增`Get`和`Set`程序，適當地。</span><span class="sxs-lookup"><span data-stu-id="23ff0-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="23ff0-115">請參閱下列指示。</span><span class="sxs-lookup"><span data-stu-id="23ff0-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="23ff0-116">若要建立 Get 的程序擷取的屬性值</span><span class="sxs-lookup"><span data-stu-id="23ff0-116">To create a Get procedure that retrieves a property value</span></span>  
  
1.  <span data-ttu-id="23ff0-117">之間`Property`並`End Property`陳述式，撰寫[Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)，後面接著`End Get`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="23ff0-118">您不需要定義任何參數`Get`程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2.  <span data-ttu-id="23ff0-119">將程式碼陳述式，來擷取屬性的值之間放`Get`和`End Get`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="23ff0-120">此程式碼可以包含其他計算和資料操作，除了產生，並傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="23ff0-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3.  <span data-ttu-id="23ff0-121">使用`Return`屬性的值傳回至呼叫端程式碼的陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="23ff0-122">您必須撰寫`Get`讀 / 寫屬性和唯讀屬性的程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="23ff0-123">您必須定義`Get`唯寫屬性的程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="23ff0-124">若要建立的設定程序寫入屬性的值</span><span class="sxs-lookup"><span data-stu-id="23ff0-124">To create a Set procedure that writes a property's value</span></span>  
  
1.  <span data-ttu-id="23ff0-125">之間`Property`並`End Property`陳述式，撰寫[Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md)，後面接著`End Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2.  <span data-ttu-id="23ff0-126">在 `Set`陳述式，請依照下列`Set`使用的參數清單括號括住關鍵字。</span><span class="sxs-lookup"><span data-stu-id="23ff0-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="23ff0-127">這個參數清單必須包含至少一個值參數呼叫的程式碼所傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="23ff0-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="23ff0-128">此值參數的預設名稱是`Value`，但如果適用的話，您可以使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="23ff0-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="23ff0-129">Value 參數必須有相同的資料類型與屬性本身。</span><span class="sxs-lookup"><span data-stu-id="23ff0-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3.  <span data-ttu-id="23ff0-130">將程式碼陳述式，將值儲存在屬性之間`Set`和`End Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23ff0-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="23ff0-131">此程式碼可以包含其他計算和資料操作，除了驗證和儲存屬性的值。</span><span class="sxs-lookup"><span data-stu-id="23ff0-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4.  <span data-ttu-id="23ff0-132">您可以使用 value 參數來接受呼叫的程式碼所提供的值。</span><span class="sxs-lookup"><span data-stu-id="23ff0-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="23ff0-133">您可以直接在指派陳述式中儲存此值或計算儲存的內部值的運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="23ff0-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="23ff0-134">您必須撰寫`Set`讀 / 寫屬性和唯寫屬性的程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="23ff0-135">您必須定義`Set`唯讀屬性的程序。</span><span class="sxs-lookup"><span data-stu-id="23ff0-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23ff0-136">範例</span><span class="sxs-lookup"><span data-stu-id="23ff0-136">Example</span></span>  
 <span data-ttu-id="23ff0-137">下列範例會建立將完整的名稱儲存為兩個組成的名稱、 名字和姓氏的讀取/寫入屬性。</span><span class="sxs-lookup"><span data-stu-id="23ff0-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="23ff0-138">當呼叫端程式碼的讀取`fullName`，則`Get`程序結合了兩個組成的名稱，並傳回的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="23ff0-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="23ff0-139">當呼叫端程式碼會指派新的完整名稱，`Set`程序會嘗試將它分成兩個組成的名稱。</span><span class="sxs-lookup"><span data-stu-id="23ff0-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="23ff0-140">如果找不到一個空格，它會儲存它做為第一個名稱。</span><span class="sxs-lookup"><span data-stu-id="23ff0-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="23ff0-141">下列範例示範一般呼叫屬性程序的`fullName`。</span><span class="sxs-lookup"><span data-stu-id="23ff0-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="23ff0-142">第一次呼叫設定屬性值，第二個呼叫會擷取它。</span><span class="sxs-lookup"><span data-stu-id="23ff0-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="23ff0-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23ff0-143">See also</span></span>

- [<span data-ttu-id="23ff0-144">程序</span><span class="sxs-lookup"><span data-stu-id="23ff0-144">Procedures</span></span>](./index.md)
- [<span data-ttu-id="23ff0-145">屬性程序</span><span class="sxs-lookup"><span data-stu-id="23ff0-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="23ff0-146">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="23ff0-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="23ff0-147">在 Visual Basic 中屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="23ff0-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="23ff0-148">如何：宣告混合的存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="23ff0-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="23ff0-149">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="23ff0-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="23ff0-150">如何：宣告，並在 Visual Basic 中呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="23ff0-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="23ff0-151">如何：將值放在屬性中</span><span class="sxs-lookup"><span data-stu-id="23ff0-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="23ff0-152">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="23ff0-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
