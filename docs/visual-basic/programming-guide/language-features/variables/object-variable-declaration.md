---
title: 物件變數宣告 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959974"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="c437d-102">物件變數宣告 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c437d-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="c437d-103">您可以使用一般的宣告陳述式來宣告物件變數。</span><span class="sxs-lookup"><span data-stu-id="c437d-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="c437d-104">資料類型，針對您指定下列其中一個`Object`(也就是[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)) 或更特定的類別來源物件的建立。</span><span class="sxs-lookup"><span data-stu-id="c437d-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="c437d-105">宣告一個變數`Object`等同於它宣告為<xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c437d-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c437d-106">當您宣告變數與特定物件類別時，它可以存取所有的方法和該類別和它所繼承的類別所公開的屬性。</span><span class="sxs-lookup"><span data-stu-id="c437d-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="c437d-107">如果您宣告變數<xref:System.Object>，它可以存取的成員<xref:System.Object>類別，除非您開啟`Option Strict Off`允許晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="c437d-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c437d-108">宣告語法</span><span class="sxs-lookup"><span data-stu-id="c437d-108">Declaration Syntax</span></span>  
 <span data-ttu-id="c437d-109">您可以使用下列語法來宣告物件變數：</span><span class="sxs-lookup"><span data-stu-id="c437d-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="c437d-110">您也可以指定[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)， `Protected Friend`，[私人](../../../../visual-basic/language-reference/modifiers/private.md)，[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，或[靜態](../../../../visual-basic/language-reference/modifiers/static.md)宣告中。</span><span class="sxs-lookup"><span data-stu-id="c437d-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="c437d-111">下列範例宣告是有效的：</span><span class="sxs-lookup"><span data-stu-id="c437d-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="c437d-112">晚期繫結，以及早期繫結</span><span class="sxs-lookup"><span data-stu-id="c437d-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="c437d-113">有時候特定的類別是未知的程式碼執行之前。</span><span class="sxs-lookup"><span data-stu-id="c437d-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="c437d-114">在此情況下，您必須宣告物件變數`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="c437d-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="c437d-115">這會建立任何類型的物件，一般參考，並在執行階段指派特定的類別。</span><span class="sxs-lookup"><span data-stu-id="c437d-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="c437d-116">這就叫做*晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="c437d-116">This is called *late binding*.</span></span> <span data-ttu-id="c437d-117">晚期繫結需要額外的執行時間。</span><span class="sxs-lookup"><span data-stu-id="c437d-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="c437d-118">它也會限制您的程式碼的方法和您最近已指派給它之類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="c437d-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="c437d-119">如果您的程式碼嘗試存取不同類別的成員，這可能會導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="c437d-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="c437d-120">當您知道的特定類別在編譯時期時，您應該宣告為該類別的物件變數。</span><span class="sxs-lookup"><span data-stu-id="c437d-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="c437d-121">這稱為「早期繫結」。</span><span class="sxs-lookup"><span data-stu-id="c437d-121">This is called *early binding*.</span></span> <span data-ttu-id="c437d-122">早期繫結可以改善效能，並保證您的程式碼存取所有的方法和屬性的特定類別。</span><span class="sxs-lookup"><span data-stu-id="c437d-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="c437d-123">在上述範例宣告中，如果變數`objA`使用的類別的物件<xref:System.Windows.Forms.Label?displayProperty=nameWithType>，您應該指定`As System.Windows.Forms.Label`在其宣告中。</span><span class="sxs-lookup"><span data-stu-id="c437d-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="c437d-124">早期繫結的優點</span><span class="sxs-lookup"><span data-stu-id="c437d-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="c437d-125">物件變數宣告為特定的類別會提供數個優點：</span><span class="sxs-lookup"><span data-stu-id="c437d-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="c437d-126">自動類型檢查</span><span class="sxs-lookup"><span data-stu-id="c437d-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="c437d-127">保證特定類別的所有成員存取</span><span class="sxs-lookup"><span data-stu-id="c437d-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="c437d-128">Microsoft IntelliSense 支援在程式碼編輯器</span><span class="sxs-lookup"><span data-stu-id="c437d-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="c437d-129">您的程式碼更容易閱讀</span><span class="sxs-lookup"><span data-stu-id="c437d-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="c437d-130">在您的程式碼中的錯誤更少</span><span class="sxs-lookup"><span data-stu-id="c437d-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="c437d-131">在攔截到的錯誤編譯時間，而非執行階段</span><span class="sxs-lookup"><span data-stu-id="c437d-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="c437d-132">更快的程式碼執行</span><span class="sxs-lookup"><span data-stu-id="c437d-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="c437d-133">物件變數成員的存取</span><span class="sxs-lookup"><span data-stu-id="c437d-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="c437d-134">當`Option Strict`已開啟`On`，物件變數可以存取的方法和與您用以宣告之類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="c437d-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="c437d-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="c437d-135">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="c437d-136">在此範例中， `p` 只能使用 <xref:System.Object> 類別本身的成員，其並未包含 `Left` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c437d-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="c437d-137">另一方面，已宣告 `q` 屬於 <xref:System.Windows.Forms.Label>類型，因此它可以使用 <xref:System.Windows.Forms.Label> 命名空間中 <xref:System.Windows.Forms> 類別的所有方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="c437d-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="c437d-138">物件變數的彈性</span><span class="sxs-lookup"><span data-stu-id="c437d-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="c437d-139">當使用繼承階層架構中的物件，您必須選擇要用於宣告物件變數的類別。</span><span class="sxs-lookup"><span data-stu-id="c437d-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="c437d-140">在進行這項選擇，您必須平衡對類別成員的存取權的物件指派的彈性。</span><span class="sxs-lookup"><span data-stu-id="c437d-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="c437d-141">例如，請考慮繼承階層架構，會導致<xref:System.Windows.Forms.Form?displayProperty=nameWithType>類別：</span><span class="sxs-lookup"><span data-stu-id="c437d-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="c437d-142">假設您的應用程式定義表單類別，稱為`specialForm`，該項則繼承自類別<xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="c437d-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="c437d-143">您可以宣告物件變數，指的是專為`specialForm`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c437d-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="c437d-144">在上述範例中宣告限制變數`nextForm`類別的物件`specialForm`，但它也會使得所有方法和屬性`specialForm`能夠`nextForm`，以及從它的所有類別的所有成員`specialForm`繼承。</span><span class="sxs-lookup"><span data-stu-id="c437d-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="c437d-145">您可以讓較一般的物件變數宣告為類型<xref:System.Windows.Forms.Form>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c437d-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="c437d-146">在上述範例中宣告可讓您指派您的應用程式中的任何表單`anyForm`。</span><span class="sxs-lookup"><span data-stu-id="c437d-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="c437d-147">不過，雖然`anyForm`可以存取類別的所有成員<xref:System.Windows.Forms.Form>，它不能使用的任何其他的方法或屬性，例如定義特定表單`specialForm`。</span><span class="sxs-lookup"><span data-stu-id="c437d-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="c437d-148">基底類別的所有成員都都可以使用衍生的類別，但在衍生類別的其他成員都則無法使用的基底類別。</span><span class="sxs-lookup"><span data-stu-id="c437d-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c437d-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c437d-149">See also</span></span>

- [<span data-ttu-id="c437d-150">物件變數</span><span class="sxs-lookup"><span data-stu-id="c437d-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="c437d-151">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="c437d-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="c437d-152">物件變數值</span><span class="sxs-lookup"><span data-stu-id="c437d-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="c437d-153">如何：宣告物件變數，並在 Visual Basic 中將物件指派給它</span><span class="sxs-lookup"><span data-stu-id="c437d-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="c437d-154">如何：存取物件的成員</span><span class="sxs-lookup"><span data-stu-id="c437d-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="c437d-155">New 運算子</span><span class="sxs-lookup"><span data-stu-id="c437d-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="c437d-156">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="c437d-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c437d-157">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="c437d-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
