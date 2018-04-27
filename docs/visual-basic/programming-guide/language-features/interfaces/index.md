---
title: 介面 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 558eae39b38161d01d599bba6c3121839560884b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="interfaces-visual-basic"></a><span data-ttu-id="982a5-102">介面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982a5-102">Interfaces (Visual Basic)</span></span>
<span data-ttu-id="982a5-103">「介面」可定義類別可實作的屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="982a5-103">*Interfaces* define the properties, methods, and events that classes can implement.</span></span> <span data-ttu-id="982a5-104">介面可讓您將功能定義為一小組緊密相關的屬性、方法和事件；這會降低相容性問題，因為您可以為您的介面開發增強的實作，而不會危及現有程式碼。</span><span class="sxs-lookup"><span data-stu-id="982a5-104">Interfaces allow you to define features as small groups of closely related properties, methods, and events; this reduces compatibility problems because you can develop enhanced implementations for your interfaces without jeopardizing existing code.</span></span> <span data-ttu-id="982a5-105">只要開發額外的介面和實作，您就可以隨時加入新功能。</span><span class="sxs-lookup"><span data-stu-id="982a5-105">You can add new features at any time by developing additional interfaces and implementations.</span></span>  
  
 <span data-ttu-id="982a5-106">另有幾個原因，會讓您想要使用介面而非類別繼承：</span><span class="sxs-lookup"><span data-stu-id="982a5-106">There are several other reasons why you might want to use interfaces instead of class inheritance:</span></span>  
  
-   <span data-ttu-id="982a5-107">介面是較適用於，當您的應用程式需要許多可能不相關的物件類型來提供特定功能時。</span><span class="sxs-lookup"><span data-stu-id="982a5-107">Interfaces are better suited to situations in which your applications require many possibly unrelated object types to provide certain functionality.</span></span>  
  
-   <span data-ttu-id="982a5-108">介面比基底類別更有彈性，因為您可以定義可實作多個介面的單一實作。</span><span class="sxs-lookup"><span data-stu-id="982a5-108">Interfaces are more flexible than base classes because you can define a single implementation that can implement multiple interfaces.</span></span>  
  
-   <span data-ttu-id="982a5-109">介面較適合不必從基底類別繼承實作的情況。</span><span class="sxs-lookup"><span data-stu-id="982a5-109">Interfaces are better in situations in which you do not have to inherit implementation from a base class.</span></span>  
  
-   <span data-ttu-id="982a5-110">當您無法使用類別繼承時，介面相當有用。</span><span class="sxs-lookup"><span data-stu-id="982a5-110">Interfaces are useful when you cannot use class inheritance.</span></span> <span data-ttu-id="982a5-111">例如，結構不能從類別繼承，但它們可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="982a5-111">For example, structures cannot inherit from classes, but they can implement interfaces.</span></span>  
  
## <a name="declaring-interfaces"></a><span data-ttu-id="982a5-112">宣告介面</span><span class="sxs-lookup"><span data-stu-id="982a5-112">Declaring Interfaces</span></span>  
 <span data-ttu-id="982a5-113">介面定義內含於 `Interface` 和 `End Interface` 陳述式之間。</span><span class="sxs-lookup"><span data-stu-id="982a5-113">Interface definitions are enclosed within the `Interface` and `End Interface` statements.</span></span> <span data-ttu-id="982a5-114">遵循 `Interface` 陳述式，您可以新增選擇性的 `Inherits` 陳述式，其中列出一或多個繼承的介面。</span><span class="sxs-lookup"><span data-stu-id="982a5-114">Following the `Interface` statement, you can add an optional `Inherits` statement that lists one or more inherited interfaces.</span></span> <span data-ttu-id="982a5-115">`Inherits` 陳述式必須在宣告中所有其他陳述式之前 (註解除外)。</span><span class="sxs-lookup"><span data-stu-id="982a5-115">The `Inherits` statements must precede all other statements in the declaration except comments.</span></span> <span data-ttu-id="982a5-116">介面定義中剩餘的陳述式應該是 `Event`、`Sub`、`Function`、`Property`、`Interface`、`Class`、`Structure` 和 `Enum` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="982a5-116">The remaining statements in the interface definition should be `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, and `Enum` statements.</span></span> <span data-ttu-id="982a5-117">介面不能包含任何實作程式碼，或實作程式碼相關聯的陳述式，例如 `End Sub` 或 `End Property`。</span><span class="sxs-lookup"><span data-stu-id="982a5-117">Interfaces cannot contain any implementation code or statements associated with implementation code, such as `End Sub` or `End Property`.</span></span>  
  
 <span data-ttu-id="982a5-118">在命名空間中，介面陳述式預設為 `Friend`，但它們也可以明確宣告為 `Public` 或 `Friend`。</span><span class="sxs-lookup"><span data-stu-id="982a5-118">In a namespace, interface statements are `Friend` by default, but they can also be explicitly declared as `Public` or `Friend`.</span></span> <span data-ttu-id="982a5-119">類別、模組、介面和結構中定義的介面預設為 `Public`，但它們也可以明確宣告為 `Public`、`Friend`、`Protected` 或 `Private`。</span><span class="sxs-lookup"><span data-stu-id="982a5-119">Interfaces defined within classes, modules, interfaces, and structures are `Public` by default, but they can also be explicitly declared as `Public`, `Friend`, `Protected`, or `Private`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="982a5-120">`Shadows` 關鍵字可以套用至所有介面成員。</span><span class="sxs-lookup"><span data-stu-id="982a5-120">The `Shadows` keyword can be applied to all interface members.</span></span> <span data-ttu-id="982a5-121">`Overloads` 關鍵字可以套用至介面定義中宣告的 `Sub`、`Function` 和 `Property` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="982a5-121">The `Overloads` keyword can be applied to `Sub`, `Function`, and `Property` statements declared in an interface definition.</span></span> <span data-ttu-id="982a5-122">此外，`Property` 陳述式可以有 `Default`、`ReadOnly` 或 `WriteOnly` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="982a5-122">In addition, `Property` statements can have the `Default`, `ReadOnly`, or `WriteOnly` modifiers.</span></span> <span data-ttu-id="982a5-123">不允許其他修飾詞，即 `Public`、`Private`、`Friend`、`Protected`、`Shared`、`Overrides`、`MustOverride` 或 `Overridable`。</span><span class="sxs-lookup"><span data-stu-id="982a5-123">None of the other modifiers—`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, or `Overridable`—are allowed.</span></span> <span data-ttu-id="982a5-124">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="982a5-124">For more information, see [Declaration Contexts and Default Access Levels](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="982a5-125">例如，下列程式碼會定義一個介面，其包含一個函式、一個屬性與一個事件。</span><span class="sxs-lookup"><span data-stu-id="982a5-125">For example, the following code defines an interface with one function, one property, and one event.</span></span>  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="982a5-126">實作介面</span><span class="sxs-lookup"><span data-stu-id="982a5-126">Implementing Interfaces</span></span>  
 <span data-ttu-id="982a5-127">Visual Basic 保留字`Implements`使用兩種方式。</span><span class="sxs-lookup"><span data-stu-id="982a5-127">The Visual Basic reserved word `Implements` is used in two ways.</span></span> <span data-ttu-id="982a5-128">`Implements` 陳述式表示類別或結構實作介面。</span><span class="sxs-lookup"><span data-stu-id="982a5-128">The `Implements` statement signifies that a class or structure implements an interface.</span></span> <span data-ttu-id="982a5-129">`Implements` 關鍵字表示類別成員或結構成員實作特定介面成員。</span><span class="sxs-lookup"><span data-stu-id="982a5-129">The `Implements` keyword signifies that a class member or structure member implements a specific interface member.</span></span>  
  
### <a name="implements-statement"></a><span data-ttu-id="982a5-130">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="982a5-130">Implements Statement</span></span>  
 <span data-ttu-id="982a5-131">如果類別或結構實作一或多個介面，它在 `Class` 或 `Structure` 陳述式後面必須緊接著 `Implements` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="982a5-131">If a class or structure implements one or more interfaces, it must include the `Implements` statement immediately after the `Class` or `Structure` statement.</span></span> <span data-ttu-id="982a5-132">`Implements` 陳述式需要由類別實作的介面清單 (以逗號分隔)。</span><span class="sxs-lookup"><span data-stu-id="982a5-132">The `Implements` statement requires a comma-separated list of interfaces to be implemented by a class.</span></span> <span data-ttu-id="982a5-133">類別或結構必須使用 `Implements` 關鍵字實作所有介面成員。</span><span class="sxs-lookup"><span data-stu-id="982a5-133">The class or structure must implement all interface members using the `Implements` keyword.</span></span>  
  
### <a name="implements-keyword"></a><span data-ttu-id="982a5-134">Implements 關鍵字</span><span class="sxs-lookup"><span data-stu-id="982a5-134">Implements Keyword</span></span>  
 <span data-ttu-id="982a5-135">`Implements` 關鍵字需要實作介面成員之逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="982a5-135">The `Implements` keyword requires a comma-separated list of interface members to be implemented.</span></span> <span data-ttu-id="982a5-136">一般而言，只會指定單一介面成員，但您可以指定多個成員。</span><span class="sxs-lookup"><span data-stu-id="982a5-136">Generally, only a single interface member is specified, but you can specify multiple members.</span></span> <span data-ttu-id="982a5-137">介面成員的規格包含介面名稱 (必須在類別內的實作陳述式中指定)、句號，以及要實作的成員函式、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="982a5-137">The specification of an interface member consists of the interface name, which must be specified in an implements statement within the class; a period; and the name of the member function, property, or event to be implemented.</span></span> <span data-ttu-id="982a5-138">實作介面成員的成員名稱可以使用任何合法的識別項，並不限於`InterfaceName_MethodName`舊版的 Visual Basic 中使用的慣例。</span><span class="sxs-lookup"><span data-stu-id="982a5-138">The name of a member that implements an interface member can use any legal identifier, and it is not limited to the `InterfaceName_MethodName` convention used in earlier versions of Visual Basic.</span></span>  
  
 <span data-ttu-id="982a5-139">例如，下列程式碼顯示如何宣告實作介面的方法、且名為 `Sub1` 的副程式：</span><span class="sxs-lookup"><span data-stu-id="982a5-139">For example, the following code shows how to declare a subroutine named `Sub1` that implements a method of an interface:</span></span>  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 <span data-ttu-id="982a5-140">實作成員的參數類型和傳回型別，必須符合介面中的介面屬性或成員宣告。</span><span class="sxs-lookup"><span data-stu-id="982a5-140">The parameter types and return types of the implementing member must match the interface property or member declaration in the interface.</span></span> <span data-ttu-id="982a5-141">最常見的實作介面項目的方式是使用與介面同名的成員，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="982a5-141">The most common way to implement an element of an interface is with a member that has the same name as the interface, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="982a5-142">若要宣告介面方法的實作，您可以使用執行個體方法宣告上的任何合法屬性，包括 `Overloads`、`Overrides`、`Overridable`、`Public`、`Private`、`Protected`、`Friend`、`Protected Friend`、`MustOverride`、`Default` 和 `Static`。</span><span class="sxs-lookup"><span data-stu-id="982a5-142">To declare the implementation of an interface method, you can use any attributes that are legal on instance method declarations, including `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, and `Static`.</span></span> <span data-ttu-id="982a5-143">`Shared` 屬性無效，因為它會定義類別而非執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="982a5-143">The `Shared` attribute is not legal since it defines a class rather than an instance method.</span></span>  
  
 <span data-ttu-id="982a5-144">使用 `Implements`，您也可以撰寫單一方法來實作一個介面中定義的多個方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="982a5-144">Using `Implements`, you can also write a single method that implements multiple methods defined in an interface, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 <span data-ttu-id="982a5-145">您可以使用私用成員來實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="982a5-145">You can use a private member to implement an interface member.</span></span> <span data-ttu-id="982a5-146">當私用成員實作介面的成員時，該成員會經由介面成為可用，即使不是直接在類別的物件變數上使用亦然。</span><span class="sxs-lookup"><span data-stu-id="982a5-146">When a private member implements a member of an interface, that member becomes available by way of the interface even though it is not available directly on object variables for the class.</span></span>  
  
### <a name="interface-implementation-examples"></a><span data-ttu-id="982a5-147">介面實作範例</span><span class="sxs-lookup"><span data-stu-id="982a5-147">Interface Implementation Examples</span></span>  
 <span data-ttu-id="982a5-148">實作介面的類別必須實作其所有屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="982a5-148">Classes that implement an interface must implement all its properties, methods, and events.</span></span>  
  
 <span data-ttu-id="982a5-149">下列範例會定義兩個介面。</span><span class="sxs-lookup"><span data-stu-id="982a5-149">The following example defines two interfaces.</span></span> <span data-ttu-id="982a5-150">第二個介面 `Interface2` 繼承 `Interface1`，並定義額外的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="982a5-150">The second interface, `Interface2`, inherits `Interface1` and defines an additional property and method.</span></span>  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 <span data-ttu-id="982a5-151">下一個範例會實作 `Interface1`，即上述範例中定義的介面：</span><span class="sxs-lookup"><span data-stu-id="982a5-151">The next example implements `Interface1`, the interface defined in the previous example:</span></span>  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 <span data-ttu-id="982a5-152">最後一個範例會實作 `Interface2`，包括繼承自 `Interface1` 的方法：</span><span class="sxs-lookup"><span data-stu-id="982a5-152">The final example implements `Interface2`, including a method inherited from `Interface1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 <span data-ttu-id="982a5-153">您可以使用 readwrite 屬性來實作 readonly 屬性 (也就是您不需要在實作類別中將它宣告為 readonly)。</span><span class="sxs-lookup"><span data-stu-id="982a5-153">You can implement a readonly property with a readwrite property (that is, you do not have to declare it readonly in the implementing class).</span></span>  <span data-ttu-id="982a5-154">實作介面保證至少會實作此介面所宣告的成員，但是您可以提供更多功能，例如可讓您使用可寫入的屬性。</span><span class="sxs-lookup"><span data-stu-id="982a5-154">Implementing an interface promises to implement at least the members that the interface declares, but you can offer more functionality, such as allowing your property to be writable.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="982a5-155">相關主題</span><span class="sxs-lookup"><span data-stu-id="982a5-155">Related Topics</span></span>  
  
|<span data-ttu-id="982a5-156">標題</span><span class="sxs-lookup"><span data-stu-id="982a5-156">Title</span></span>|<span data-ttu-id="982a5-157">描述</span><span class="sxs-lookup"><span data-stu-id="982a5-157">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="982a5-158">逐步解說：建立和實作介面</span><span class="sxs-lookup"><span data-stu-id="982a5-158">Walkthrough: Creating and Implementing Interfaces</span></span>](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|<span data-ttu-id="982a5-159">提供詳細的程序，引導您定義和實作您自己的介面之程序。</span><span class="sxs-lookup"><span data-stu-id="982a5-159">Provides a detailed procedure that takes you through the process of defining and implementing your own interface.</span></span>|  
|[<span data-ttu-id="982a5-160">泛型介面中的變異數</span><span class="sxs-lookup"><span data-stu-id="982a5-160">Variance in Generic Interfaces</span></span>](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="982a5-161">討論泛型介面中的共變性與逆變性，並提供.NET Framework 中的 Variant 泛型介面清單。</span><span class="sxs-lookup"><span data-stu-id="982a5-161">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
