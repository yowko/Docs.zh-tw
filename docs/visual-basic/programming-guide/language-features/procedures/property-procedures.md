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
ms.openlocfilehash: f3b57ae45815fbd91cad17cddbed4d01037eb92f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002094"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="d913f-102">屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d913f-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="d913f-103">屬性程式是一系列的 Visual Basic 語句，可操作模組、類別或結構上的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="d913f-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="d913f-104">屬性程式也稱為*屬性存取*子。</span><span class="sxs-lookup"><span data-stu-id="d913f-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="d913f-105">Visual Basic 提供下列屬性程式：</span><span class="sxs-lookup"><span data-stu-id="d913f-105">Visual Basic provides for the following property procedures:</span></span>  
  
- <span data-ttu-id="d913f-106">@No__t-0 程式會傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d913f-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="d913f-107">當您存取運算式中的屬性時，就會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d913f-107">It is called when you access the property in an expression.</span></span>  
  
- <span data-ttu-id="d913f-108">@No__t-0 程式會將屬性設定為值，包括物件參考。</span><span class="sxs-lookup"><span data-stu-id="d913f-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="d913f-109">當您將值指派給屬性時，就會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d913f-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="d913f-110">您通常會使用 `Get` 和 `Set` 語句來定義成對的屬性程式，但如果該屬性為唯讀（[Get 語句](../../../../visual-basic/language-reference/statements/get-statement.md)）或僅限寫入（[Set 語句](../../../../visual-basic/language-reference/statements/set-statement.md)），則可以單獨定義其中一個程式。</span><span class="sxs-lookup"><span data-stu-id="d913f-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="d913f-111">使用自動執行的屬性時，您可以省略 `Get` 和 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="d913f-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="d913f-112">如需詳細資訊，請參閱[自動實作的屬性](./auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d913f-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="d913f-113">您可以在類別、結構和模組中定義屬性。</span><span class="sxs-lookup"><span data-stu-id="d913f-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="d913f-114">根據預設，屬性 @no__t 為0，這表示您可以從應用程式中可存取屬性容器的任何位置呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="d913f-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="d913f-115">如需屬性和變數的比較，請參閱[Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="d913f-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="d913f-116">宣告語法</span><span class="sxs-lookup"><span data-stu-id="d913f-116">Declaration Syntax</span></span>  
 <span data-ttu-id="d913f-117">屬性本身是由[屬性語句](../../../../visual-basic/language-reference/statements/property-statement.md)中包含的程式碼區塊和 `End Property` 語句所定義。</span><span class="sxs-lookup"><span data-stu-id="d913f-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="d913f-118">在此區塊內，每個屬性程式會顯示為包含在宣告語句內的內部區塊（`Get` 或 `Set`），以及相符的 `End` 宣告。</span><span class="sxs-lookup"><span data-stu-id="d913f-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="d913f-119">宣告屬性和其程式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="d913f-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```vb  
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
  
 <span data-ttu-id="d913f-120">@No__t-0 可以指定有關多載、覆寫、共用和遮蔽的存取層級和資訊，以及屬性為唯讀或僅限寫入。</span><span class="sxs-lookup"><span data-stu-id="d913f-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="d913f-121">@No__t-1 或 @no__t 2 程式上的 `AccessLevel` 可以是比為屬性本身指定之存取層級更嚴格的任何層級。</span><span class="sxs-lookup"><span data-stu-id="d913f-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="d913f-122">如需詳細資訊，請參閱[Property 語句](../../../../visual-basic/language-reference/statements/property-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d913f-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="d913f-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="d913f-123">Data Type</span></span>  
 <span data-ttu-id="d913f-124">屬性的資料類型和主體存取層級是在 `Property` 語句中定義，而不是在屬性程式中。</span><span class="sxs-lookup"><span data-stu-id="d913f-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="d913f-125">屬性只能有一個資料類型。</span><span class="sxs-lookup"><span data-stu-id="d913f-125">A property can have only one data type.</span></span> <span data-ttu-id="d913f-126">例如，您無法定義屬性來儲存 `Decimal` 值，但會抓取 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="d913f-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="d913f-127">存取層級</span><span class="sxs-lookup"><span data-stu-id="d913f-127">Access Level</span></span>  
 <span data-ttu-id="d913f-128">不過，您可以定義屬性的主體存取層級，並在其中一個屬性程式中進一步限制存取層級。</span><span class="sxs-lookup"><span data-stu-id="d913f-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="d913f-129">例如，您可以定義 `Public` 屬性，然後定義 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="d913f-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="d913f-130">@No__t-0 程式仍然 `Public`。</span><span class="sxs-lookup"><span data-stu-id="d913f-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="d913f-131">您只能在其中一個屬性程式中變更存取層級，而且只能讓它比主要存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="d913f-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="d913f-132">如需詳細資訊，請參閱[如何：宣告具有混合存取層級 @ no__t-0 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d913f-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="d913f-133">參數宣告</span><span class="sxs-lookup"><span data-stu-id="d913f-133">Parameter Declaration</span></span>  
 <span data-ttu-id="d913f-134">您可以用與[Sub 程式](./sub-procedures.md)相同的方式宣告每個參數，但傳遞機制必須 `ByVal`。</span><span class="sxs-lookup"><span data-stu-id="d913f-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="d913f-135">參數清單中每個參數的語法如下：</span><span class="sxs-lookup"><span data-stu-id="d913f-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="d913f-136">如果參數是選擇性的，您也必須提供預設值做為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="d913f-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="d913f-137">指定預設值的語法如下：</span><span class="sxs-lookup"><span data-stu-id="d913f-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="d913f-138">屬性值</span><span class="sxs-lookup"><span data-stu-id="d913f-138">Property Value</span></span>  
 <span data-ttu-id="d913f-139">在 `Get` 程式中，傳回值會提供給呼叫運算式做為屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d913f-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="d913f-140">在 `Set` 程式中，新的屬性值會傳遞給 `Set` 語句的參數。</span><span class="sxs-lookup"><span data-stu-id="d913f-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="d913f-141">如果您明確宣告參數，則必須使用與屬性相同的資料類型來宣告它。</span><span class="sxs-lookup"><span data-stu-id="d913f-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="d913f-142">如果您未宣告參數，編譯器會使用隱含參數 `Value` 來代表要指派給屬性的新值。</span><span class="sxs-lookup"><span data-stu-id="d913f-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="d913f-143">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="d913f-143">Calling Syntax</span></span>  
 <span data-ttu-id="d913f-144">藉由參考屬性，您可以隱含地叫用屬性程式。</span><span class="sxs-lookup"><span data-stu-id="d913f-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="d913f-145">使用屬性的名稱與使用變數名稱的方式相同，不同之處在于您必須為非選擇性的所有引數提供值，而且必須將引數清單括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="d913f-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="d913f-146">如果未提供任何引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="d913f-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="d913f-147">對 `Set` 程式之隱含呼叫的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d913f-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="d913f-148">對 `Get` 程式之隱含呼叫的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d913f-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="d913f-149">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="d913f-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="d913f-150">下列屬性會將完整名稱儲存為兩個組成名稱、名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="d913f-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="d913f-151">當呼叫程式碼讀取 `fullName` 時，@no__t 1 程式會合並兩個組成名稱，並傳回完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d913f-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="d913f-152">當呼叫程式碼指派新的完整名稱時，@no__t 0 程式會嘗試將它分成兩個組成的名稱。</span><span class="sxs-lookup"><span data-stu-id="d913f-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="d913f-153">如果找不到空間，則會將它全部儲存為名字。</span><span class="sxs-lookup"><span data-stu-id="d913f-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="d913f-154">下列範例顯示對 `fullName` 的屬性程式的一般呼叫。</span><span class="sxs-lookup"><span data-stu-id="d913f-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="d913f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d913f-155">See also</span></span>

- [<span data-ttu-id="d913f-156">程序</span><span class="sxs-lookup"><span data-stu-id="d913f-156">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d913f-157">函式程序</span><span class="sxs-lookup"><span data-stu-id="d913f-157">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d913f-158">運算子程序</span><span class="sxs-lookup"><span data-stu-id="d913f-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d913f-159">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="d913f-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d913f-160">Visual Basic 中的屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="d913f-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- <span data-ttu-id="d913f-161">[如何：建立屬性 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="d913f-161">[How to: Create a Property](./how-to-create-a-property.md)</span></span>
- <span data-ttu-id="d913f-162">[如何：呼叫屬性程式 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="d913f-162">[How to: Call a Property Procedure](./how-to-call-a-property-procedure.md)</span></span>
- <span data-ttu-id="d913f-163">[如何：在 Visual Basic @ no__t-0 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="d913f-163">[How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)</span></span>
- <span data-ttu-id="d913f-164">[如何：將值放在屬性 @ no__t-0 中</span><span class="sxs-lookup"><span data-stu-id="d913f-164">[How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md)</span></span>
- <span data-ttu-id="d913f-165">[如何：從屬性 @ no__t-0 取得值</span><span class="sxs-lookup"><span data-stu-id="d913f-165">[How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
