---
title: 物件變數宣告
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
ms.openlocfilehash: 74b1401df3dbb2d744de74734d10cbcd92e9689e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077042"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="4f2e8-102">物件變數宣告 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f2e8-102">Object Variable Declaration (Visual Basic)</span></span>

<span data-ttu-id="4f2e8-103">您可以使用一般宣告語句來宣告物件變數。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="4f2e8-104">若為資料類型，您可以指定 `Object` (也就是， [物件資料類型](../../../language-reference/data-types/object-data-type.md)) 或要從中建立物件的更特定類別。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="4f2e8-105">將變數宣告為與宣告變數 `Object` 相同 <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4f2e8-106">當您宣告具有特定物件類別的變數時，它可以存取該類別所公開的所有方法和屬性，以及它所繼承的類別。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="4f2e8-107">如果您使用宣告變數 <xref:System.Object> ，它只能存取類別的成員 <xref:System.Object> ，除非您轉換 `Option Strict Off` 為允許晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="4f2e8-108">宣告語法</span><span class="sxs-lookup"><span data-stu-id="4f2e8-108">Declaration Syntax</span></span>  

 <span data-ttu-id="4f2e8-109">使用下列語法來宣告物件變數：</span><span class="sxs-lookup"><span data-stu-id="4f2e8-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="4f2e8-110">您也可以在宣告中指定 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)、 `Protected Friend` [私](../../../language-reference/modifiers/private.md)用、 [共用](../../../language-reference/modifiers/shared.md)或 [靜態](../../../language-reference/modifiers/static.md) 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-110">You can also specify [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md), or [Static](../../../language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="4f2e8-111">下列範例宣告有效：</span><span class="sxs-lookup"><span data-stu-id="4f2e8-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="4f2e8-112">晚期繫結和早期繫結</span><span class="sxs-lookup"><span data-stu-id="4f2e8-112">Late Binding and Early Binding</span></span>  

 <span data-ttu-id="4f2e8-113">有時候，在您的程式碼執行之前，特定類別是未知的。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="4f2e8-114">在此情況下，您必須宣告具有資料類型的物件變數 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="4f2e8-115">這會建立任何物件類型的一般參考，並且在執行時間指派特定類別。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="4f2e8-116">這稱為 *晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-116">This is called *late binding*.</span></span> <span data-ttu-id="4f2e8-117">晚期繫結需要額外的執行時間。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="4f2e8-118">它也會將您的程式碼限制為您最近指派給它的類別的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="4f2e8-119">如果您的程式碼嘗試存取不同類別的成員，這可能會導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="4f2e8-120">當您在編譯時期知道特定類別時，您應該將物件變數宣告為該類別。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="4f2e8-121">這稱為「早期繫結」\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-121">This is called *early binding*.</span></span> <span data-ttu-id="4f2e8-122">早期繫結可改善效能，並保證您的程式碼可以存取特定類別的所有方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="4f2e8-123">在上述範例宣告中，如果變數 `objA` 只使用類別的物件 <xref:System.Windows.Forms.Label?displayProperty=nameWithType> ，您應該 `As System.Windows.Forms.Label` 在其宣告中指定。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="4f2e8-124">早期繫結的優點</span><span class="sxs-lookup"><span data-stu-id="4f2e8-124">Advantages of Early Binding</span></span>  

 <span data-ttu-id="4f2e8-125">將物件變數宣告為特定類別，可提供幾個優點：</span><span class="sxs-lookup"><span data-stu-id="4f2e8-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="4f2e8-126">自動類型檢查</span><span class="sxs-lookup"><span data-stu-id="4f2e8-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="4f2e8-127">保證可以存取特定類別的所有成員</span><span class="sxs-lookup"><span data-stu-id="4f2e8-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="4f2e8-128">程式碼編輯器中的 Microsoft IntelliSense 支援</span><span class="sxs-lookup"><span data-stu-id="4f2e8-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="4f2e8-129">改善程式碼的可讀性</span><span class="sxs-lookup"><span data-stu-id="4f2e8-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="4f2e8-130">程式碼中的錯誤減少</span><span class="sxs-lookup"><span data-stu-id="4f2e8-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="4f2e8-131">在編譯時間而非執行時間攔截到的錯誤</span><span class="sxs-lookup"><span data-stu-id="4f2e8-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="4f2e8-132">更快速的程式碼執行</span><span class="sxs-lookup"><span data-stu-id="4f2e8-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="4f2e8-133">物件變數成員的存取權</span><span class="sxs-lookup"><span data-stu-id="4f2e8-133">Access to Object Variable Members</span></span>  

 <span data-ttu-id="4f2e8-134">當 `Option Strict` 開啟時 `On` ，物件變數只能存取您用以宣告之類別的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="4f2e8-135">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-135">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="4f2e8-136">在此範例中， `p` 只能使用 <xref:System.Object> 類別本身的成員，其並未包含 `Left` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="4f2e8-137">另一方面，已宣告 `q` 屬於 <xref:System.Windows.Forms.Label>類型，因此它可以使用 <xref:System.Windows.Forms.Label> 命名空間中 <xref:System.Windows.Forms> 類別的所有方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="4f2e8-138">物件變數的彈性</span><span class="sxs-lookup"><span data-stu-id="4f2e8-138">Flexibility of Object Variables</span></span>  

 <span data-ttu-id="4f2e8-139">使用繼承階層中的物件時，您可以選擇要用來宣告物件變數的類別。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="4f2e8-140">在進行這項選擇時，您必須針對物件指派的彈性，與對類別成員的存取進行平衡。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="4f2e8-141">例如，請考慮導向至類別的繼承階層架構 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="4f2e8-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="4f2e8-142">假設您的應用程式定義了一個名為的表單類別 `specialForm` ，而該類別繼承自類別 <xref:System.Windows.Forms.Form> 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="4f2e8-143">您可以宣告明確參考的物件變數 `specialForm` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="4f2e8-144">上述範例中的宣告會將變數限制 `nextForm` 為類別的物件 `specialForm` ，但它也會讓所有的方法和屬性可 `specialForm` 供使用 `nextForm` ，以及繼承之所有類別的所有成員 `specialForm` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="4f2e8-145">您可以藉由將物件變數宣告為類型，讓物件變數更為普遍 <xref:System.Windows.Forms.Form> ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="4f2e8-146">上述範例中的宣告可讓您將應用程式中的任何表單指派給 `anyForm` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="4f2e8-147">不過，雖然 `anyForm` 可以存取類別的所有成員 <xref:System.Windows.Forms.Form> ，但它無法使用針對特定表單（例如）所定義的任何其他方法或屬性 `specialForm` 。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="4f2e8-148">基類的所有成員都可供衍生類別使用，但基類無法使用衍生類別的其他成員。</span><span class="sxs-lookup"><span data-stu-id="4f2e8-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2e8-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f2e8-149">See also</span></span>

- [<span data-ttu-id="4f2e8-150">物件變數</span><span class="sxs-lookup"><span data-stu-id="4f2e8-150">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="4f2e8-151">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="4f2e8-151">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="4f2e8-152">物件變數值</span><span class="sxs-lookup"><span data-stu-id="4f2e8-152">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="4f2e8-153">如何：在 Visual Basic 中宣告物件變數，並指派物件給它</span><span class="sxs-lookup"><span data-stu-id="4f2e8-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="4f2e8-154">如何：存取物件的成員</span><span class="sxs-lookup"><span data-stu-id="4f2e8-154">How to: Access Members of an Object</span></span>](how-to-access-members-of-an-object.md)
- [<span data-ttu-id="4f2e8-155">New 運算子</span><span class="sxs-lookup"><span data-stu-id="4f2e8-155">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="4f2e8-156">Long</span><span class="sxs-lookup"><span data-stu-id="4f2e8-156">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="4f2e8-157">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="4f2e8-157">Local Type Inference</span></span>](local-type-inference.md)
