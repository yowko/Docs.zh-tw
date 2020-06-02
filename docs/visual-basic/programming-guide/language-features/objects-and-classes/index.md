---
title: 物件和類別
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 10e257a1cbc8778565a9838aeef423522f9d2970
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290613"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="54bbd-102">Visual Basic 中的物件和類別</span><span class="sxs-lookup"><span data-stu-id="54bbd-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="54bbd-103">「物件」\*\* 是可視為一個單位的程式碼和資料組合。</span><span class="sxs-lookup"><span data-stu-id="54bbd-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="54bbd-104">物件可以是應用程式的一部分，例如控制項或表單。</span><span class="sxs-lookup"><span data-stu-id="54bbd-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="54bbd-105">整個應用程式也可以是一個物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-105">An entire application can also be an object.</span></span>

<span data-ttu-id="54bbd-106">當您在 Visual Basic 中建立應用程式時，您會經常使用物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="54bbd-107">您可以使用 Visual Basic 所提供的物件，例如控制項、表單和資料存取物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="54bbd-108">您也可以使用來自 Visual Basic 應用程式中其他應用程式的物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="54bbd-109">您甚至可以建立自己的物件，並為其定義其他屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="54bbd-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="54bbd-110">物件的作用類似針對程式預製的建置組塊 - 它們可讓您撰寫一段程式碼一次，然後不斷地重複使用。</span><span class="sxs-lookup"><span data-stu-id="54bbd-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="54bbd-111">本主題會詳細討論物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="54bbd-112">物件和類別</span><span class="sxs-lookup"><span data-stu-id="54bbd-112">Objects and classes</span></span>

<span data-ttu-id="54bbd-113">Visual Basic 中的每個物件都是由*類別*所定義。</span><span class="sxs-lookup"><span data-stu-id="54bbd-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="54bbd-114">類別會描述物件的變數、屬性、程序及事件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="54bbd-115">物件是類別的執行個體；當您定義類別之後，就能視需要建立最多的物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="54bbd-116">若要了解物件和其類別之間的關聯性，請想像餅乾壓模與餅乾。</span><span class="sxs-lookup"><span data-stu-id="54bbd-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="54bbd-117">餅乾壓模是類別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-117">The cookie cutter is the class.</span></span> <span data-ttu-id="54bbd-118">它會定義每塊餅乾的特性，例如大小和形狀。</span><span class="sxs-lookup"><span data-stu-id="54bbd-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="54bbd-119">類別可用來建立物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-119">The class is used to create objects.</span></span> <span data-ttu-id="54bbd-120">物件則是餅乾。</span><span class="sxs-lookup"><span data-stu-id="54bbd-120">The objects are the cookies.</span></span>

<span data-ttu-id="54bbd-121">您必須先建立物件，才可以存取其成員，但 [`Shared`](../../../language-reference/modifiers/shared.md) 不含類別的物件即可存取的成員除外。</span><span class="sxs-lookup"><span data-stu-id="54bbd-121">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="54bbd-122">從類別建立物件</span><span class="sxs-lookup"><span data-stu-id="54bbd-122">Create an object from a class</span></span>

1. <span data-ttu-id="54bbd-123">判斷您想要建立物件的類別，或定義您自己的類別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-123">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="54bbd-124">例如：</span><span class="sxs-lookup"><span data-stu-id="54bbd-124">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="54bbd-125">撰寫 [Dim 陳述式](../../../language-reference/statements/dim-statement.md)來建立變數，而您可以將類別執行個體指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="54bbd-125">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="54bbd-126">變數必須是所需類別的型別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-126">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="54bbd-127">新增 [New 運算子](../../../language-reference/operators/new-operator.md)關鍵字，將變數初始化為類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bbd-127">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="54bbd-128">您現在可以透過物件變數存取類別的成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-128">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="54bbd-129">可能的話，您應該將變數宣告為您想要指派給它的類別型別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-129">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="54bbd-130">這稱為「早期繫結」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-130">This is called *early binding*.</span></span> <span data-ttu-id="54bbd-131">如果您在編譯時期不知道類別類型，可藉由將變數宣告為 [Object 資料類型](../../../language-reference/data-types/object-data-type.md)來叫用「晚期繫結」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-131">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="54bbd-132">不過，晚期繫結會讓效能降低，並限制存取執行階段物件的成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-132">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="54bbd-133">如需詳細資訊，請參閱[物件變數宣告](../variables/object-variable-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-133">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="54bbd-134">多個執行個體</span><span class="sxs-lookup"><span data-stu-id="54bbd-134">Multiple instances</span></span>

<span data-ttu-id="54bbd-135">從類別新建的物件通常是彼此相同的。</span><span class="sxs-lookup"><span data-stu-id="54bbd-135">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="54bbd-136">不過，當它們以個別物件存在之後，就能個別變更其變數和屬性，而與其他執行個體無關。</span><span class="sxs-lookup"><span data-stu-id="54bbd-136">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="54bbd-137">例如，如果您在表單中新增三個核取方塊，每個核取方塊物件都是 <xref:System.Windows.Forms.CheckBox> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bbd-137">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="54bbd-138">個別的 <xref:System.Windows.Forms.CheckBox> 物件會共用一組由類別所定義的通用特性和功能 (屬性、變數、程序及事件)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-138">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="54bbd-139">但是，每個物件都有自己的名稱、可個別啟用及停用，而且可以放在表單的不同位置。</span><span class="sxs-lookup"><span data-stu-id="54bbd-139">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="54bbd-140">物件成員</span><span class="sxs-lookup"><span data-stu-id="54bbd-140">Object members</span></span>

<span data-ttu-id="54bbd-141">物件是應用程式的元素，代表類別的「執行個體」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-141">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="54bbd-142">欄位、屬性、方法及事件都是物件的建置組塊，並構成它們的「成員」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-142">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="54bbd-143">成員存取</span><span class="sxs-lookup"><span data-stu-id="54bbd-143">Member Access</span></span>

<span data-ttu-id="54bbd-144">您可以存取物件的成員，方法是依序指定物件變數的名稱、句點 (`.`) 及成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="54bbd-144">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="54bbd-145">下列範例會設定 <xref:System.Windows.Forms.Label> 物件的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="54bbd-145">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="54bbd-146">成員的 IntelliSense 清單</span><span class="sxs-lookup"><span data-stu-id="54bbd-146">IntelliSense listing of members</span></span>

<span data-ttu-id="54bbd-147">當您叫用 IntelliSense 的 [列出成員] 選項時 (例如，當您輸入句號 (`.`) 做為成員存取運算子時)，它會列出類別的成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-147">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="54bbd-148">如果您在宣告為該類別執行個體的變數名稱後面輸入句點，IntelliSense 會列出所有執行個體成員，而不會列出任何共用的成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-148">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="54bbd-149">如果您在類別名稱本身後面輸入句點，則 IntelliSense 會列出所有共用的成員，但不會列出任何執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-149">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="54bbd-150">如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-150">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="54bbd-151">欄位和屬性</span><span class="sxs-lookup"><span data-stu-id="54bbd-151">Fields and properties</span></span>

<span data-ttu-id="54bbd-152">「欄位」\*\* 和「屬性」\*\* 表示物件中所儲存的資訊。</span><span class="sxs-lookup"><span data-stu-id="54bbd-152">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="54bbd-153">您可以利用在程序中擷取和設定區域變數的相同方式，使用指派陳述式來擷取和設定它們的值。</span><span class="sxs-lookup"><span data-stu-id="54bbd-153">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="54bbd-154">下列範例會擷取 <xref:System.Windows.Forms.Label> 物件的 <xref:System.Windows.Forms.Control.Width%2A> 屬性，並設定 <xref:System.Windows.Forms.Control.ForeColor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="54bbd-154">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="54bbd-155">請注意，也會呼叫欄位做為「成員變數」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-155">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="54bbd-156">使用屬性程序的時機：</span><span class="sxs-lookup"><span data-stu-id="54bbd-156">Use property procedures when:</span></span>

- <span data-ttu-id="54bbd-157">您需要控制何時以及如何設定或擷取值。</span><span class="sxs-lookup"><span data-stu-id="54bbd-157">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="54bbd-158">屬性具有一組定義明確且需要驗證的值。</span><span class="sxs-lookup"><span data-stu-id="54bbd-158">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="54bbd-159">設定值會導致一些可察覺的物件狀態變更，例如 `IsVisible` 屬性。</span><span class="sxs-lookup"><span data-stu-id="54bbd-159">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="54bbd-160">設定此屬性會導致其他內部變數的變更，或其他屬性值的變更。</span><span class="sxs-lookup"><span data-stu-id="54bbd-160">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="54bbd-161">您必須先執行一組步驟，才能設定或擷取此屬性。</span><span class="sxs-lookup"><span data-stu-id="54bbd-161">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="54bbd-162">使用欄位的時機：</span><span class="sxs-lookup"><span data-stu-id="54bbd-162">Use fields when:</span></span>

- <span data-ttu-id="54bbd-163">值為自我驗證的型別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-163">The value is of a self-validating type.</span></span> <span data-ttu-id="54bbd-164">例如，如果將 `True` 或 `False` 以外的值指派給 `Boolean` 變數，就會發生錯誤或自動資料轉換。</span><span class="sxs-lookup"><span data-stu-id="54bbd-164">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="54bbd-165">位於資料型別所支援範圍內的任何值都是有效的。</span><span class="sxs-lookup"><span data-stu-id="54bbd-165">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="54bbd-166">這適用許多型別為 `Single` 或 `Double` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="54bbd-166">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="54bbd-167">屬性是 `String` 資料型別，而且對於字串的大小或值沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="54bbd-167">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="54bbd-168">如需詳細資訊，請參閱[屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-168">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="54bbd-169">一律將非固定欄位保持為私用。</span><span class="sxs-lookup"><span data-stu-id="54bbd-169">Always keep the non-constant fields private.</span></span> <span data-ttu-id="54bbd-170">當您想要將它設為公用時，請改用屬性。</span><span class="sxs-lookup"><span data-stu-id="54bbd-170">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="54bbd-171">方法</span><span class="sxs-lookup"><span data-stu-id="54bbd-171">Methods</span></span>

<span data-ttu-id="54bbd-172">「方法」\*\* 是物件可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="54bbd-172">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="54bbd-173">例如，<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> 是 <xref:System.Windows.Forms.ComboBox> 物件的方法，可新增項目至下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="54bbd-173">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="54bbd-174">下列範例示範 <xref:System.Windows.Forms.Timer> 物件的 <xref:System.Windows.Forms.Timer.Start%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="54bbd-174">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="54bbd-175">請注意，方法只是物件所公開的「程序」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-175">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="54bbd-176">如需詳細資訊，請參閱[程序](../procedures/index.md)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-176">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="54bbd-177">事件</span><span class="sxs-lookup"><span data-stu-id="54bbd-177">Events</span></span>

<span data-ttu-id="54bbd-178">事件是物件所識別的動作 (例如按一下滑鼠按鈕或按下按鍵)，而您可以撰寫程式碼來回應。</span><span class="sxs-lookup"><span data-stu-id="54bbd-178">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="54bbd-179">事件可能因使用者動作或程式碼而發生，或由系統所導致。</span><span class="sxs-lookup"><span data-stu-id="54bbd-179">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="54bbd-180">您可以將對事件發出訊號的程式碼視為「引發」\*\* 事件，而將回應事件的程式碼視為「處理」\*\* 它。</span><span class="sxs-lookup"><span data-stu-id="54bbd-180">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="54bbd-181">您也可以開發自己的自訂事件，透過您的物件來引發並由其他物件來處理。</span><span class="sxs-lookup"><span data-stu-id="54bbd-181">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="54bbd-182">如需詳細資訊，請參閱[事件](../events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-182">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="54bbd-183">執行個體成員和共用的成員</span><span class="sxs-lookup"><span data-stu-id="54bbd-183">Instance members and shared members</span></span>

<span data-ttu-id="54bbd-184">當您從類別建立物件時，會產生該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bbd-184">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="54bbd-185">未使用 [Shared](../../../language-reference/modifiers/shared.md) 關鍵字宣告的成員是「執行個體成員」\*\*，它們完全屬於該特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bbd-185">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="54bbd-186">一個執行個體中的執行個體成員，與同一個類別的另一個執行個體中相同的成員無關。</span><span class="sxs-lookup"><span data-stu-id="54bbd-186">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="54bbd-187">例如，執行個體成員變數可以在不同執行個體中具有不同的值。</span><span class="sxs-lookup"><span data-stu-id="54bbd-187">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="54bbd-188">使用 `Shared` 關鍵字宣告的成員是「共用的成員」\*\*，它們屬於整個類別，而不屬於任何特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bbd-188">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="54bbd-189">共用的成員只會存在一次，而不論您為它的類別建立了多少個執行個體，或者，即使您未建立任何執行個體也一樣。</span><span class="sxs-lookup"><span data-stu-id="54bbd-189">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="54bbd-190">例如，共用的成員變數只有一個值，可供可存取該類別的所有程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="54bbd-190">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="54bbd-191">存取非共用成員</span><span class="sxs-lookup"><span data-stu-id="54bbd-191">Accessing non-shared members</span></span>

1. <span data-ttu-id="54bbd-192">確定物件是從它的類別所建立，並將它指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="54bbd-192">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="54bbd-193">在存取成員的語句中，遵循具有*成員存取運算子*（）的物件變數名稱，然後 `.` 是成員名稱。</span><span class="sxs-lookup"><span data-stu-id="54bbd-193">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="54bbd-194">存取共用的成員</span><span class="sxs-lookup"><span data-stu-id="54bbd-194">Accessing shared members</span></span>

- <span data-ttu-id="54bbd-195">在類別名稱後面加上*成員存取運算子*（ `.` ），然後是成員名稱。</span><span class="sxs-lookup"><span data-stu-id="54bbd-195">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="54bbd-196">您應一律透過類別名稱直接存取物件的 `Shared` 成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-196">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="54bbd-197">如果您已經從類別建立物件，也可以透過物件的變數存取 `Shared` 成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-197">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="54bbd-198">類別和模組之間的差異</span><span class="sxs-lookup"><span data-stu-id="54bbd-198">Differences between classes and modules</span></span>

<span data-ttu-id="54bbd-199">類別和模組的主要差異是，類別可以具現化為物件，而標準模組不行。</span><span class="sxs-lookup"><span data-stu-id="54bbd-199">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="54bbd-200">因為只有一個標準模組資料的複本，所以，當您程式的某一部分變更了標準模組中的公用變數時，如果該程式的任何其他部分接著讀取該變數，則會取得相同的值 。</span><span class="sxs-lookup"><span data-stu-id="54bbd-200">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="54bbd-201">相較之下，每個具現化物件適用的物件資料會個別存在。</span><span class="sxs-lookup"><span data-stu-id="54bbd-201">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="54bbd-202">另一個差異是，不同於標準模組，類別可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="54bbd-202">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="54bbd-203">如果類別是以[MustInherit](../../../language-reference/modifiers/mustinherit.md)修飾詞標記，則無法直接具現化。</span><span class="sxs-lookup"><span data-stu-id="54bbd-203">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="54bbd-204">不過，它仍然與模組不同，因為它可以在無法繼承模組時被繼承。</span><span class="sxs-lookup"><span data-stu-id="54bbd-204">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="54bbd-205">將 `Shared` 修飾詞套用到類別成員時，它會與類別本身而不是類別的特定執行個體相關聯。</span><span class="sxs-lookup"><span data-stu-id="54bbd-205">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="54bbd-206">使用類別名稱直接存取成員，相同方式可用來存取模組成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-206">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="54bbd-207">類別和模組也會針對它們的成員使用不同的範圍。</span><span class="sxs-lookup"><span data-stu-id="54bbd-207">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="54bbd-208">在類別內定義的成員範圍會在類別的特定執行個體內，而且只存在於物件的存留期。</span><span class="sxs-lookup"><span data-stu-id="54bbd-208">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="54bbd-209">若要從類別外部存取類別成員，您必須使用 *Object*.*Member* 格式的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="54bbd-209">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="54bbd-210">另一方面，在模組內宣告的成員預設是可公開存取的，而且可由任何可存取該模組的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="54bbd-210">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="54bbd-211">這表示，標準模組中的變數是有效的全域變數 (因為您可以在專案中的任何位置看見它們)，並存在於程式的存留期。</span><span class="sxs-lookup"><span data-stu-id="54bbd-211">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="54bbd-212">重複使用類別和物件</span><span class="sxs-lookup"><span data-stu-id="54bbd-212">Reusing classes and objects</span></span>

<span data-ttu-id="54bbd-213">物件可讓您宣告變數和程序一次，接著就能在需要時重複使用它們。</span><span class="sxs-lookup"><span data-stu-id="54bbd-213">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="54bbd-214">例如，如果您想要在應用程式中加入拼字檢查程式，您可以定義所有變數和支援函式來提供拼字檢查功能。</span><span class="sxs-lookup"><span data-stu-id="54bbd-214">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="54bbd-215">如果您以類別形式建立拼字檢查程式，接著就能藉由加入對已編譯組件的參考，在其他應用程式中重複使用它。</span><span class="sxs-lookup"><span data-stu-id="54bbd-215">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="54bbd-216">更棒的是，您或許能夠使用其他人已經開發的拼字檢查程式類別來簡化您的一些工作。</span><span class="sxs-lookup"><span data-stu-id="54bbd-216">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="54bbd-217">.NET 提供許多可供使用的元件範例。</span><span class="sxs-lookup"><span data-stu-id="54bbd-217">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="54bbd-218">下列範例使用 <xref:System> 命名空間中的 <xref:System.TimeZone> 類別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-218">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="54bbd-219"><xref:System.TimeZone> 提供可讓您擷取目前電腦系統時區相關資訊的成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-219"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="54bbd-220">在上述範例中，第一個 [Dim 陳述式](../../../language-reference/statements/dim-statement.md)會宣告 <xref:System.TimeZone> 類型的物件變數，並將 <xref:System.TimeZone.CurrentTimeZone%2A> 屬性所傳回的 <xref:System.TimeZone> 物件指派給它。</span><span class="sxs-lookup"><span data-stu-id="54bbd-220">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="54bbd-221">物件之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="54bbd-221">Relationships among objects</span></span>

<span data-ttu-id="54bbd-222">物件可以透過數種方式彼此相關。</span><span class="sxs-lookup"><span data-stu-id="54bbd-222">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="54bbd-223">主要的關聯性種類是「階層式」\*\* 和「內含項目」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-223">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="54bbd-224">階層式關聯性</span><span class="sxs-lookup"><span data-stu-id="54bbd-224">Hierarchical relationship</span></span>

<span data-ttu-id="54bbd-225">當類別衍生自更基本的類別時，即表示它們具有「階層式關聯性」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-225">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="54bbd-226">在描述屬於更一般類別的子型別的項目時，類別階層架構就很實用。</span><span class="sxs-lookup"><span data-stu-id="54bbd-226">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="54bbd-227">在下列範例中，假設您想要定義一種特殊的 <xref:System.Windows.Forms.Button>，其作用就像一般的 <xref:System.Windows.Forms.Button>，但也會公開可反轉前景和背景色彩的方法。</span><span class="sxs-lookup"><span data-stu-id="54bbd-227">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="54bbd-228">定義衍生自已經存在類別的類別</span><span class="sxs-lookup"><span data-stu-id="54bbd-228">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="54bbd-229">使用 [Class 陳述式](../../../language-reference/statements/class-statement.md)來定義您需要從中建立物件的類別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-229">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="54bbd-230">請確定 `End Class` 陳述式會接在類別中程式碼最後一行的後面。</span><span class="sxs-lookup"><span data-stu-id="54bbd-230">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="54bbd-231">根據預設，當您輸入 `Class` 陳述式時，整合式開發環境 (IDE) 會自動產生 `End Class`。</span><span class="sxs-lookup"><span data-stu-id="54bbd-231">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="54bbd-232">在 `Class` 陳述式正後方加上 [Inherits 陳述式](../../../language-reference/statements/inherits-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-232">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="54bbd-233">指定要從中衍生新類別的類別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-233">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="54bbd-234">您的新類別會繼承由基底類別定義的所有成員。</span><span class="sxs-lookup"><span data-stu-id="54bbd-234">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="54bbd-235">加入衍生類別所公開之其他成員適用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="54bbd-235">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="54bbd-236">例如，您可以加入 `ReverseColors` 方法，而您的衍生類別可能看起來如下：</span><span class="sxs-lookup"><span data-stu-id="54bbd-236">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="54bbd-237">如果您從類別建立物件 `ReversibleButton` ，它可以存取類別的所有成員 <xref:System.Windows.Forms.Button> ，以及 `ReverseColors` 方法和您在中定義的任何其他新成員 `ReversibleButton` 。</span><span class="sxs-lookup"><span data-stu-id="54bbd-237">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="54bbd-238">衍生的類別會繼承來自其基礎類別的成員，可讓您在類別階層中進行時增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="54bbd-238">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="54bbd-239">如需詳細資訊，請參閱[繼承的基本概念](inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-239">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="54bbd-240">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="54bbd-240">Compile the code</span></span>

<span data-ttu-id="54bbd-241">確定編譯器可以存取您想要從中衍生新類別的類別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-241">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="54bbd-242">這可能表示要提供它的完整名稱，如同在上述範例中，或在 [Imports 陳述式 (.NET 命名空間和型別)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)中識別它的命名空間。</span><span class="sxs-lookup"><span data-stu-id="54bbd-242">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="54bbd-243">如果類別位於不同專案，則您可能需要加入對該專案的參考。</span><span class="sxs-lookup"><span data-stu-id="54bbd-243">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="54bbd-244">如需詳細資訊，請參閱[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。</span><span class="sxs-lookup"><span data-stu-id="54bbd-244">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="54bbd-245">內含項目關聯性</span><span class="sxs-lookup"><span data-stu-id="54bbd-245">Containment relationship</span></span>

<span data-ttu-id="54bbd-246">另一個可讓物件相關聯的方法是「內含項目關係」\*\*。</span><span class="sxs-lookup"><span data-stu-id="54bbd-246">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="54bbd-247">容器物件邏輯上會封裝其他物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-247">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="54bbd-248">例如，<xref:System.OperatingSystem> 物件在邏輯上會包含 <xref:System.Version> 物件，這會透過其 <xref:System.OperatingSystem.Version%2A> 屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="54bbd-248">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="54bbd-249">請注意，容器物件實際上不會包含任何其他物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-249">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="54bbd-250">集合</span><span class="sxs-lookup"><span data-stu-id="54bbd-250">Collections</span></span>

<span data-ttu-id="54bbd-251">物件內含項目的一個特定型別是由「集合」\*\* 來代表。</span><span class="sxs-lookup"><span data-stu-id="54bbd-251">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="54bbd-252">集合是一組可列舉的相似物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-252">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="54bbd-253">Visual Basic 在 For Each 中支援特定的語法 ... [下一個語句](../../../language-reference/statements/for-each-next-statement.md)，可讓您逐一查看集合的專案。</span><span class="sxs-lookup"><span data-stu-id="54bbd-253">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="54bbd-254">此外，集合通常可讓您使用 <xref:Microsoft.VisualBasic.Collection.Item%2A>，依其索引來擷取項目，或者將它們關聯至唯一字串來擷取項目。</span><span class="sxs-lookup"><span data-stu-id="54bbd-254">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="54bbd-255">比起陣列，集合更容易使用，因為它們讓您不需使用索引，就能新增或移除項目。</span><span class="sxs-lookup"><span data-stu-id="54bbd-255">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="54bbd-256">由於集合易於使用，因此，通常會用來儲存表單和控制項。</span><span class="sxs-lookup"><span data-stu-id="54bbd-256">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="54bbd-257">相關主題</span><span class="sxs-lookup"><span data-stu-id="54bbd-257">Related topics</span></span>

<span data-ttu-id="54bbd-258">[逐步解說：定義類別](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-258">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="54bbd-259">提供如何建立類別的逐步說明。</span><span class="sxs-lookup"><span data-stu-id="54bbd-259">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="54bbd-260">[多載屬性和方法](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-260">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="54bbd-261">多載屬性和方法</span><span class="sxs-lookup"><span data-stu-id="54bbd-261">Overloaded Properties and Methods</span></span>

<span data-ttu-id="54bbd-262">[繼承基本概念](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-262">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="54bbd-263">涵蓋繼承修飾詞，覆寫方法和屬性、MyClass 及 MyBase。</span><span class="sxs-lookup"><span data-stu-id="54bbd-263">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="54bbd-264">[物件存留期：物件的建立和終結方式](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-264">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="54bbd-265">討論類別執行個體的建立與處置。</span><span class="sxs-lookup"><span data-stu-id="54bbd-265">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="54bbd-266">[匿名型別](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-266">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="54bbd-267">描述如何建立和使用匿名型別，讓您不需撰寫資料型別的類別定義，就能建立物件。</span><span class="sxs-lookup"><span data-stu-id="54bbd-267">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="54bbd-268">[物件初始化運算式：命名和匿名型別](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-268">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="54bbd-269">討論物件初始設定式，它們可用於透過使用單一運算式來建立具名和匿名型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bbd-269">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="54bbd-270">[如何：在匿名型別宣告中推斷屬性名稱和類型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="54bbd-270">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="54bbd-271">說明如何在匿名型別宣告中推斷屬性名稱和型別。</span><span class="sxs-lookup"><span data-stu-id="54bbd-271">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="54bbd-272">提供成功和失敗的推斷範例。</span><span class="sxs-lookup"><span data-stu-id="54bbd-272">Provides examples of successful and unsuccessful inference.</span></span>
