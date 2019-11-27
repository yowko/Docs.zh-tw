---
title: 如何：建立屬性
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349706"
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="6dd39-102">如何：建立屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6dd39-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="6dd39-103">您可以將屬性定義括在 `Property` 語句和 `End Property` 語句之間。</span><span class="sxs-lookup"><span data-stu-id="6dd39-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="6dd39-104">在此定義中，您可以定義 `Get` 程式、`Set` 程式或兩者。</span><span class="sxs-lookup"><span data-stu-id="6dd39-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="6dd39-105">所有屬性的程式碼都位於這些程式內。</span><span class="sxs-lookup"><span data-stu-id="6dd39-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="6dd39-106">`Get` 程式會抓取屬性的值，而 `Set` 程式會儲存值。</span><span class="sxs-lookup"><span data-stu-id="6dd39-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="6dd39-107">如果您想要屬性具有讀取/寫入存取權，您必須定義這兩個程式。</span><span class="sxs-lookup"><span data-stu-id="6dd39-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="6dd39-108">針對唯讀屬性，您只會定義 `Get`，而對於僅限寫入屬性，只會定義 `Set`。</span><span class="sxs-lookup"><span data-stu-id="6dd39-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="6dd39-109">建立屬性</span><span class="sxs-lookup"><span data-stu-id="6dd39-109">To create a property</span></span>  
  
1. <span data-ttu-id="6dd39-110">在任何屬性或程式之外，請使用[Property 語句](../../../../visual-basic/language-reference/statements/property-statement.md)，後面接著 `End Property` 語句。</span><span class="sxs-lookup"><span data-stu-id="6dd39-110">Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2. <span data-ttu-id="6dd39-111">如果屬性接受參數，請在 `Property` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單。</span><span class="sxs-lookup"><span data-stu-id="6dd39-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="6dd39-112">請在括弧後面加上 `As` 子句，以指定屬性值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6dd39-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="6dd39-113">您必須指定資料類型，即使是僅限寫入的屬性。</span><span class="sxs-lookup"><span data-stu-id="6dd39-113">You must specify the data type even for a write-only property.</span></span>  
  
4. <span data-ttu-id="6dd39-114">視需要新增 `Get` 和 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="6dd39-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="6dd39-115">請參閱下列指示。</span><span class="sxs-lookup"><span data-stu-id="6dd39-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="6dd39-116">若要建立可抓取屬性值的 Get 程式</span><span class="sxs-lookup"><span data-stu-id="6dd39-116">To create a Get procedure that retrieves a property value</span></span>  
  
1. <span data-ttu-id="6dd39-117">在 `Property` 和 `End Property` 語句之間，撰寫[Get 語句](../../../../visual-basic/language-reference/statements/get-statement.md)，後面接著 `End Get` 語句。</span><span class="sxs-lookup"><span data-stu-id="6dd39-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="6dd39-118">您不需要定義 `Get` 程式的任何參數。</span><span class="sxs-lookup"><span data-stu-id="6dd39-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2. <span data-ttu-id="6dd39-119">放置程式碼語句，以在 `Get` 和 `End Get` 語句之間抓取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="6dd39-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="6dd39-120">除了產生並傳回屬性的值之外，此程式碼還可以包含其他計算和資料操作。</span><span class="sxs-lookup"><span data-stu-id="6dd39-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3. <span data-ttu-id="6dd39-121">使用 `Return` 語句，將屬性的值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="6dd39-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="6dd39-122">您必須針對讀寫屬性和唯讀屬性撰寫 `Get` 程式。</span><span class="sxs-lookup"><span data-stu-id="6dd39-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="6dd39-123">您不能定義僅限寫入屬性的 `Get` 程式。</span><span class="sxs-lookup"><span data-stu-id="6dd39-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="6dd39-124">建立寫入屬性值的 Set 程式</span><span class="sxs-lookup"><span data-stu-id="6dd39-124">To create a Set procedure that writes a property's value</span></span>  
  
1. <span data-ttu-id="6dd39-125">在 `Property` 和 `End Property` 語句之間，撰寫[Set 語句](../../../../visual-basic/language-reference/statements/set-statement.md)，後面接著 `End Set` 語句。</span><span class="sxs-lookup"><span data-stu-id="6dd39-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2. <span data-ttu-id="6dd39-126">在 `Set` 語句中，以括弧括住參數清單的 `Set` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6dd39-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="6dd39-127">此參數清單必須至少包含呼叫端程式碼所傳遞值的值參數。</span><span class="sxs-lookup"><span data-stu-id="6dd39-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="6dd39-128">此值參數的預設名稱為 `Value`，但您可以視需要使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dd39-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="6dd39-129">Value 參數必須與屬性本身具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6dd39-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3. <span data-ttu-id="6dd39-130">將程式碼語句放在 `Set` 和 `End Set` 語句之間的屬性中儲存值。</span><span class="sxs-lookup"><span data-stu-id="6dd39-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="6dd39-131">除了驗證和儲存屬性的值之外，此程式碼還可以包含其他計算和資料操作。</span><span class="sxs-lookup"><span data-stu-id="6dd39-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4. <span data-ttu-id="6dd39-132">使用 value 參數來接受呼叫程式碼所提供的值。</span><span class="sxs-lookup"><span data-stu-id="6dd39-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="6dd39-133">您可以直接將此值儲存在指派語句中，或在運算式中使用它來計算要儲存的內部值。</span><span class="sxs-lookup"><span data-stu-id="6dd39-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="6dd39-134">您必須針對讀寫屬性和寫入屬性撰寫 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="6dd39-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="6dd39-135">您不能為唯讀屬性定義 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="6dd39-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dd39-136">範例</span><span class="sxs-lookup"><span data-stu-id="6dd39-136">Example</span></span>  
 <span data-ttu-id="6dd39-137">下列範例會建立讀取/寫入屬性，將完整名稱儲存為兩個組成名稱、名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="6dd39-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="6dd39-138">當呼叫程式碼讀取 `fullName`時，`Get` 程式會結合兩個組成名稱，並傳回完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6dd39-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="6dd39-139">當呼叫程式碼指派新的完整名稱時，`Set` 程式會嘗試將它分成兩個組成的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dd39-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="6dd39-140">如果找不到空間，則會將它全部儲存為名字。</span><span class="sxs-lookup"><span data-stu-id="6dd39-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="6dd39-141">下列範例會顯示 `fullName`的屬性程式的一般呼叫。</span><span class="sxs-lookup"><span data-stu-id="6dd39-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="6dd39-142">第一個呼叫會設定屬性值，而第二個呼叫會將它抓取。</span><span class="sxs-lookup"><span data-stu-id="6dd39-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="6dd39-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd39-143">See also</span></span>

- [<span data-ttu-id="6dd39-144">程序</span><span class="sxs-lookup"><span data-stu-id="6dd39-144">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6dd39-145">屬性程序</span><span class="sxs-lookup"><span data-stu-id="6dd39-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="6dd39-146">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="6dd39-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6dd39-147">Visual Basic 中的屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="6dd39-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="6dd39-148">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="6dd39-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="6dd39-149">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="6dd39-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="6dd39-150">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="6dd39-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="6dd39-151">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="6dd39-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="6dd39-152">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="6dd39-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
