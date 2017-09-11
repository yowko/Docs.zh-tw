---
title: "Property 程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Set statement, Property procedures
- Visual Basic code, procedures
- return values, Property procedures
- syntax, Property procedures
- procedures, property
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], custom
- property procedures
- Get statement, property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6ba662a8cf9748b719bfbd7205ce65989e79d05a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="aecdc-102">屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aecdc-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="aecdc-103">屬性程序是一系列的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]管理模組、 類別或結構的自訂屬性的陳述式。</span><span class="sxs-lookup"><span data-stu-id="aecdc-103">A property procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="aecdc-104">屬性的程序也稱為*屬性存取子*。</span><span class="sxs-lookup"><span data-stu-id="aecdc-104">Property procedures are also known as *property accessors*.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="aecdc-105">提供下列屬性程序︰</span><span class="sxs-lookup"><span data-stu-id="aecdc-105"> provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="aecdc-106">A`Get`程序會傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="aecdc-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="aecdc-107">存取在運算式中的屬性時呼叫。</span><span class="sxs-lookup"><span data-stu-id="aecdc-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="aecdc-108">A`Set`程序設定的屬性值，包括物件參考。</span><span class="sxs-lookup"><span data-stu-id="aecdc-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="aecdc-109">您將值指派給屬性時呼叫。</span><span class="sxs-lookup"><span data-stu-id="aecdc-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="aecdc-110">通常定義屬性程序中使用的組`Get`和`Set`陳述式，但是您可以定義單獨一種程序如果屬性是唯讀 ([Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)) 或唯寫 ([Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="aecdc-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="aecdc-111">您可以省略`Get`和`Set`程序時使用自動實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="aecdc-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="aecdc-112">如需詳細資訊，請參閱[Auto-Implemented 屬性](./auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="aecdc-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="aecdc-113">您可以在類別、 結構和模組中定義屬性。</span><span class="sxs-lookup"><span data-stu-id="aecdc-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="aecdc-114">屬性是`Public`根據預設，這表示您可以從任何位置呼叫它們可以存取屬性的容器應用程式中。</span><span class="sxs-lookup"><span data-stu-id="aecdc-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="aecdc-115">如需屬性和變數的比較，請參閱[屬性之間的差異和 Visual Basic 中的變數](./differences-between-properties-and-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="aecdc-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="aecdc-116">宣告語法</span><span class="sxs-lookup"><span data-stu-id="aecdc-116">Declaration Syntax</span></span>  
 <span data-ttu-id="aecdc-117">屬性本身定義所括住的程式碼區塊[屬性陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)和`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="aecdc-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="aecdc-118">在這個區塊中，每個屬性的程序會顯示為宣告陳述式括住的內部區塊 (`Get`或`Set`) 和比對`End`宣告。</span><span class="sxs-lookup"><span data-stu-id="aecdc-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="aecdc-119">宣告屬性和它的程序的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="aecdc-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
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
  
 <span data-ttu-id="aecdc-120">`Modifiers`可以存取層級和多載、 覆寫、 共用、 和遮蔽的相關資訊，以及屬性是否為唯讀或唯寫的。</span><span class="sxs-lookup"><span data-stu-id="aecdc-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="aecdc-121">`AccessLevel`上`Get`或`Set`程序可以是任何比指定的屬性本身的存取層級更具限制性的層級。</span><span class="sxs-lookup"><span data-stu-id="aecdc-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="aecdc-122">如需詳細資訊，請參閱[屬性陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="aecdc-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="aecdc-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="aecdc-123">Data Type</span></span>  
 <span data-ttu-id="aecdc-124">屬性的資料型別和主體的存取層級會定義在`Property`陳述式，不是以屬性程序。</span><span class="sxs-lookup"><span data-stu-id="aecdc-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="aecdc-125">屬性可以有一種資料型別。</span><span class="sxs-lookup"><span data-stu-id="aecdc-125">A property can have only one data type.</span></span> <span data-ttu-id="aecdc-126">例如，您不能定義屬性，以便存放`Decimal`值，但擷取`Double`值。</span><span class="sxs-lookup"><span data-stu-id="aecdc-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="aecdc-127">存取層級</span><span class="sxs-lookup"><span data-stu-id="aecdc-127">Access Level</span></span>  
 <span data-ttu-id="aecdc-128">不過，您可以定義主體的存取層級屬性，並在其中一個屬性程序的存取層級，進一步限制。</span><span class="sxs-lookup"><span data-stu-id="aecdc-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="aecdc-129">例如，您可以定義`Public`屬性，然後定義`Private Set`程序。</span><span class="sxs-lookup"><span data-stu-id="aecdc-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="aecdc-130">`Get`程序會維持`Public`。</span><span class="sxs-lookup"><span data-stu-id="aecdc-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="aecdc-131">您可以變更其中一個屬性的程序的存取層級，而且您只可讓它更具限制性的主體的存取層級。</span><span class="sxs-lookup"><span data-stu-id="aecdc-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="aecdc-132">如需詳細資訊，請參閱[如何︰ 宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="aecdc-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="aecdc-133">參數宣告</span><span class="sxs-lookup"><span data-stu-id="aecdc-133">Parameter Declaration</span></span>  
 <span data-ttu-id="aecdc-134">您每個參數宣告相同的方式就如同[Sub 程序](./sub-procedures.md)，差別只在於必須傳遞機制`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="aecdc-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="aecdc-135">參數清單中的每個參數的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="aecdc-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="aecdc-136">如果參數是選擇性的您也必須提供預設值，如其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="aecdc-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="aecdc-137">指定預設值的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="aecdc-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="aecdc-138">屬性值</span><span class="sxs-lookup"><span data-stu-id="aecdc-138">Property Value</span></span>  
 <span data-ttu-id="aecdc-139">在`Get`程序中，傳回值提供給屬性的值呼叫運算式。</span><span class="sxs-lookup"><span data-stu-id="aecdc-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="aecdc-140">在`Set`程序中，新的屬性值傳遞給參數`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="aecdc-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="aecdc-141">如果您明確宣告為參數，您必須使用相同的資料類型與屬性來進行宣告。</span><span class="sxs-lookup"><span data-stu-id="aecdc-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="aecdc-142">如果您未宣告的參數，編譯器會使用隱含參數`Value`來表示要指派給屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="aecdc-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="aecdc-143">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="aecdc-143">Calling Syntax</span></span>  
 <span data-ttu-id="aecdc-144">藉由參考屬性隱含地呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="aecdc-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="aecdc-145">使用屬性的名稱相同的方式，您會使用變數的名稱不同之處在於您必須提供值給所有引數不是選擇性的且您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="aecdc-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="aecdc-146">如果已不提供任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="aecdc-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="aecdc-147">語法隱含呼叫`Set`程序如下︰</span><span class="sxs-lookup"><span data-stu-id="aecdc-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="aecdc-148">語法隱含呼叫`Get`程序如下︰</span><span class="sxs-lookup"><span data-stu-id="aecdc-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="aecdc-149">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="aecdc-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="aecdc-150">下列屬性會將完整的名稱儲存為兩個構成名稱、 名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="aecdc-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="aecdc-151">當呼叫程式碼讀取`fullName`、`Get`程序結合了兩個構成的名稱，並傳回完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="aecdc-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="aecdc-152">當呼叫程式碼會指派新的完整名稱，`Set`程序會嘗試將它切為兩個構成名稱。</span><span class="sxs-lookup"><span data-stu-id="aecdc-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="aecdc-153">如果找不到空間，它會儲存它做為第一個名稱。</span><span class="sxs-lookup"><span data-stu-id="aecdc-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 <span data-ttu-id="aecdc-154">[!code-vb[VbVbcnProcedures #&8;](./codesnippet/VisualBasic/property-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="aecdc-154">[!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="aecdc-155">下列範例示範一般呼叫屬性程序的`fullName`。</span><span class="sxs-lookup"><span data-stu-id="aecdc-155">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 <span data-ttu-id="aecdc-156">[!code-vb[VbVbcnProcedures #&9;](./codesnippet/VisualBasic/property-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="aecdc-156">[!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecdc-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aecdc-157">See Also</span></span>  
 <span data-ttu-id="aecdc-158">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-158">[Procedures](./index.md) </span></span>  
<span data-ttu-id="aecdc-159"> [Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-159"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="aecdc-160"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-160"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="aecdc-161"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-161"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="aecdc-162"> [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-162"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="aecdc-163"> [如何︰ 建立屬性](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-163"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="aecdc-164"> [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-164"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="aecdc-165"> [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-165"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="aecdc-166"> [如何︰ 將值置入屬性](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="aecdc-166"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="aecdc-167"> [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="aecdc-167"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
