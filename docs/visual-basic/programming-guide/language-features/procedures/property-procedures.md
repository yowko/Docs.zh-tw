---
title: 屬性程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828339"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="b9afd-102">屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9afd-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="b9afd-103">屬性程序是一系列的 Visual Basic 陳述式，以操作上的模組、 類別或結構的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="b9afd-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="b9afd-104">屬性程序是也稱為*屬性存取子*。</span><span class="sxs-lookup"><span data-stu-id="b9afd-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="b9afd-105">Visual Basic 提供下列屬性程序：</span><span class="sxs-lookup"><span data-stu-id="b9afd-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="b9afd-106">A`Get`程序會傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b9afd-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="b9afd-107">它會呼叫存取在運算式中的屬性時。</span><span class="sxs-lookup"><span data-stu-id="b9afd-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="b9afd-108">A`Set`程序會將屬性設定值，包括物件參考。</span><span class="sxs-lookup"><span data-stu-id="b9afd-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="b9afd-109">當您指派給屬性的值時，被呼叫它。</span><span class="sxs-lookup"><span data-stu-id="b9afd-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="b9afd-110">您通常是定義屬性程序中使用的組`Get`並`Set`陳述式，但是您可以定義其中一個單獨的程序如果屬性為唯讀 ([Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)) 或唯寫 ([設定陳述式](../../../../visual-basic/language-reference/statements/set-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="b9afd-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="b9afd-111">您可以省略`Get`和`Set`程序時使用的自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="b9afd-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="b9afd-112">如需詳細資訊，請參閱[自動實作的屬性](./auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b9afd-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="b9afd-113">您可以在類別、 結構和模組中定義屬性。</span><span class="sxs-lookup"><span data-stu-id="b9afd-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="b9afd-114">屬性是`Public`根據預設，這表示您可以從任何地方呼叫它們可以存取屬性的容器應用程式中。</span><span class="sxs-lookup"><span data-stu-id="b9afd-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="b9afd-115">如需屬性和變數的比較，請參閱 <<c0> [ 屬性之間的差異和 Visual Basic 中的變數](./differences-between-properties-and-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b9afd-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="b9afd-116">宣告語法</span><span class="sxs-lookup"><span data-stu-id="b9afd-116">Declaration Syntax</span></span>  
 <span data-ttu-id="b9afd-117">屬性本身定義所包圍的程式碼區塊[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)而`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b9afd-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="b9afd-118">在這個區塊中，每一個屬性程序，會顯示為宣告陳述式括住的內部區塊 (`Get`或是`Set`) 和比對`End`宣告。</span><span class="sxs-lookup"><span data-stu-id="b9afd-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="b9afd-119">宣告屬性和它的程序的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9afd-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="b9afd-120">`Modifiers`可以也因為屬性是否為唯讀或唯寫的指定存取層級和多載、 覆寫、 共用和陰影的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b9afd-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="b9afd-121">`AccessLevel`上`Get`或`Set`程序可以是任何層級所指定的屬性本身的存取層級更具限制性。</span><span class="sxs-lookup"><span data-stu-id="b9afd-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="b9afd-122">如需詳細資訊，請參閱 < [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b9afd-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="b9afd-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="b9afd-123">Data Type</span></span>  
 <span data-ttu-id="b9afd-124">屬性的資料類型和主體的存取層級會定義在`Property`陳述式，不在屬性程序。</span><span class="sxs-lookup"><span data-stu-id="b9afd-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="b9afd-125">屬性可以有只有一個資料型別。</span><span class="sxs-lookup"><span data-stu-id="b9afd-125">A property can have only one data type.</span></span> <span data-ttu-id="b9afd-126">例如，您不能定義屬性，以便存放`Decimal`值，但擷取`Double`值。</span><span class="sxs-lookup"><span data-stu-id="b9afd-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="b9afd-127">存取層級</span><span class="sxs-lookup"><span data-stu-id="b9afd-127">Access Level</span></span>  
 <span data-ttu-id="b9afd-128">不過，您可以定義主體的存取層級的屬性，並進一步限制存取層級，在其中一個屬性程序。</span><span class="sxs-lookup"><span data-stu-id="b9afd-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="b9afd-129">例如，您可以定義`Public`屬性，然後定義`Private Set`程序。</span><span class="sxs-lookup"><span data-stu-id="b9afd-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="b9afd-130">`Get`程序會維持`Public`。</span><span class="sxs-lookup"><span data-stu-id="b9afd-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="b9afd-131">您可以變更其中一個屬性的程序中的存取層級，您可以只讓它更具限制性的主體的存取層級。</span><span class="sxs-lookup"><span data-stu-id="b9afd-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="b9afd-132">如需詳細資訊，請參閱[如何：宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="b9afd-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="b9afd-133">參數宣告</span><span class="sxs-lookup"><span data-stu-id="b9afd-133">Parameter Declaration</span></span>  
 <span data-ttu-id="b9afd-134">您所進行的相同方式宣告的每個參數[Sub 程序](./sub-procedures.md)，但必須是傳遞機制`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="b9afd-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="b9afd-135">參數清單中的每個參數的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9afd-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="b9afd-136">如果參數是選擇性的您還必須提供預設值做為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="b9afd-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="b9afd-137">指定預設值的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9afd-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="b9afd-138">屬性值</span><span class="sxs-lookup"><span data-stu-id="b9afd-138">Property Value</span></span>  
 <span data-ttu-id="b9afd-139">在 `Get`程序中，傳回的值提供給屬性的值呼叫運算式。</span><span class="sxs-lookup"><span data-stu-id="b9afd-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="b9afd-140">在 `Set`程序中，新的屬性值傳遞給參數`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b9afd-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="b9afd-141">如果您明確宣告的參數，您必須使用相同的資料類型的屬性來進行宣告。</span><span class="sxs-lookup"><span data-stu-id="b9afd-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="b9afd-142">如果您未宣告的參數，編譯器會使用隱含參數`Value`來表示要指派給屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="b9afd-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="b9afd-143">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="b9afd-143">Calling Syntax</span></span>  
 <span data-ttu-id="b9afd-144">藉由參考屬性中以隱含方式呼叫的屬性程序時。</span><span class="sxs-lookup"><span data-stu-id="b9afd-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="b9afd-145">使用屬性的名稱相同的方式，您會使用變數的名稱，不同之處在於您必須提供值的所有引數不是選擇性的且您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="b9afd-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="b9afd-146">如果已不提供任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="b9afd-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="b9afd-147">語法隱含呼叫`Set`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9afd-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="b9afd-148">語法隱含呼叫`Get`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9afd-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="b9afd-149">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="b9afd-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="b9afd-150">下列屬性會將完整的名稱儲存為兩個組成的名稱、 名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="b9afd-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="b9afd-151">當呼叫端程式碼的讀取`fullName`，則`Get`程序結合了兩個組成的名稱，並傳回的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b9afd-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="b9afd-152">當呼叫端程式碼會指派新的完整名稱，`Set`程序會嘗試將它分成兩個組成的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9afd-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="b9afd-153">如果找不到一個空格，它會儲存它做為第一個名稱。</span><span class="sxs-lookup"><span data-stu-id="b9afd-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="b9afd-154">下列範例示範一般呼叫屬性程序的`fullName`。</span><span class="sxs-lookup"><span data-stu-id="b9afd-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b9afd-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9afd-155">See also</span></span>

- [<span data-ttu-id="b9afd-156">程序</span><span class="sxs-lookup"><span data-stu-id="b9afd-156">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b9afd-157">函式程序</span><span class="sxs-lookup"><span data-stu-id="b9afd-157">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="b9afd-158">運算子程序</span><span class="sxs-lookup"><span data-stu-id="b9afd-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="b9afd-159">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="b9afd-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b9afd-160">在 Visual Basic 中屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="b9afd-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="b9afd-161">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="b9afd-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="b9afd-162">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="b9afd-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="b9afd-163">如何：宣告，並在 Visual Basic 中呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="b9afd-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="b9afd-164">如何：將值放在屬性中</span><span class="sxs-lookup"><span data-stu-id="b9afd-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="b9afd-165">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="b9afd-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
