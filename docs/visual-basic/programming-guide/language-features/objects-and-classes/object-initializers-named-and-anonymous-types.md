---
title: 物件初始設定式：命名和匿名型別 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: e1f461cc98fb104f78a6c83a207cff7f4eda9227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046456"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="c66c7-102">物件初始設定式：命名和匿名型別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c66c7-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="c66c7-103">物件初始化運算式可讓您使用單一運算式來指定複雜物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="c66c7-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="c66c7-104">它們可以用來建立命名類型和匿名型別的實例。</span><span class="sxs-lookup"><span data-stu-id="c66c7-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="c66c7-105">宣告</span><span class="sxs-lookup"><span data-stu-id="c66c7-105">Declarations</span></span>  
 <span data-ttu-id="c66c7-106">已命名和匿名型別的實例宣告看起來幾乎完全相同, 但其效果並不相同。</span><span class="sxs-lookup"><span data-stu-id="c66c7-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="c66c7-107">每個類別都有自己的能力和限制。</span><span class="sxs-lookup"><span data-stu-id="c66c7-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="c66c7-108">下列範例顯示使用物件初始化運算式清單來宣告和初始化命名類別`Customer`之實例的便利方式。</span><span class="sxs-lookup"><span data-stu-id="c66c7-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="c66c7-109">請注意, 類別的名稱是在關鍵字`New`之後指定。</span><span class="sxs-lookup"><span data-stu-id="c66c7-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c66c7-110">匿名型別沒有可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="c66c7-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="c66c7-111">因此, 匿名型別的具現化不能包含類別名稱。</span><span class="sxs-lookup"><span data-stu-id="c66c7-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c66c7-112">這兩個宣告的需求和結果不同。</span><span class="sxs-lookup"><span data-stu-id="c66c7-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="c66c7-113">若`namedCust`為,具有`Name`屬性的類別必須已經存在,而且宣告會建立該類別的實例。`Customer`</span><span class="sxs-lookup"><span data-stu-id="c66c7-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="c66c7-114">針對`anonymousCust`, 編譯器會定義具有一個屬性的新類別、名`Name`為的字串, 並建立該類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="c66c7-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="c66c7-115">命名類型</span><span class="sxs-lookup"><span data-stu-id="c66c7-115">Named Types</span></span>  
 <span data-ttu-id="c66c7-116">物件初始化運算式提供簡單的方法來呼叫類型的函式, 然後在單一語句中設定部分或所有屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c66c7-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="c66c7-117">編譯器會針對語句叫用適當的函式: 如果沒有提供任何引數, 則為無參數的函式, 或如果傳送了一或多個引數, 則為參數化的函數</span><span class="sxs-lookup"><span data-stu-id="c66c7-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="c66c7-118">之後, 指定的屬性會依照它們在初始化運算式清單中的顯示順序來初始化。</span><span class="sxs-lookup"><span data-stu-id="c66c7-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="c66c7-119">初始化運算式清單中的每個初始設定都包含將初始值指派給類別的成員。</span><span class="sxs-lookup"><span data-stu-id="c66c7-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="c66c7-120">定義類別時, 會決定成員的名稱和資料類型。</span><span class="sxs-lookup"><span data-stu-id="c66c7-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="c66c7-121">在下列範例中, `Customer`類別必須存在, 而且必須具有名為`Name`且`City`可接受字串值的成員。</span><span class="sxs-lookup"><span data-stu-id="c66c7-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c66c7-122">或者, 您可以使用下列程式碼來取得相同的結果:</span><span class="sxs-lookup"><span data-stu-id="c66c7-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c66c7-123">這些宣告中的每一個都相當於下列範例, 其會`Customer`使用無參數的函式來建立物件, 然後使用`With`來指定`Name`和`City`屬性的初始值句.</span><span class="sxs-lookup"><span data-stu-id="c66c7-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c66c7-124">例如, 如果`Name` `Customer`類別包含參數化的函式, 可讓您傳送的值, 您也可以透過下列方式來宣告和初始化物件: `Customer`</span><span class="sxs-lookup"><span data-stu-id="c66c7-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="c66c7-125">您不需要初始化所有屬性, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c66c7-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="c66c7-126">不過, 初始化清單不可以是空的。</span><span class="sxs-lookup"><span data-stu-id="c66c7-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="c66c7-127">未初始化的屬性會保留其預設值。</span><span class="sxs-lookup"><span data-stu-id="c66c7-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="c66c7-128">具有命名類型的類型推斷</span><span class="sxs-lookup"><span data-stu-id="c66c7-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="c66c7-129">您可以藉`cust1`由結合物件初始化運算式和區欄位型別推斷, 縮短宣告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c66c7-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="c66c7-130">這可讓您省略變數`As`宣告中的子句。</span><span class="sxs-lookup"><span data-stu-id="c66c7-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="c66c7-131">變數的資料類型是從指派所建立的物件類型推斷而來。</span><span class="sxs-lookup"><span data-stu-id="c66c7-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="c66c7-132">在下列範例中, 的類型`cust6`是。 `Customer`</span><span class="sxs-lookup"><span data-stu-id="c66c7-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="c66c7-133">命名類型的相關備註</span><span class="sxs-lookup"><span data-stu-id="c66c7-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="c66c7-134">類別成員在物件初始化運算式清單中無法初始化一次以上。</span><span class="sxs-lookup"><span data-stu-id="c66c7-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="c66c7-135">的宣告會造成錯誤。 `cust7`</span><span class="sxs-lookup"><span data-stu-id="c66c7-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="c66c7-136">成員可以用來初始化本身或其他欄位。</span><span class="sxs-lookup"><span data-stu-id="c66c7-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="c66c7-137">如果成員在初始化之前被存取 (如的下列`cust8`宣告所示), 則會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="c66c7-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="c66c7-138">請記住, 當處理使用物件初始化運算式的宣告時, 第一件事就是叫用適當的函式。</span><span class="sxs-lookup"><span data-stu-id="c66c7-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="c66c7-139">之後, 初始化運算式清單中的個別欄位便會進行初始化。</span><span class="sxs-lookup"><span data-stu-id="c66c7-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="c66c7-140">在下列範例中, `Name`會為`cust8`指派的預設值, 並在中`cust9`指派初始化的值。</span><span class="sxs-lookup"><span data-stu-id="c66c7-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="c66c7-141">下列範例會`cust3`從和`cust4`使用參數化的函式, 以宣告`cust11`和初始化`cust10`和。</span><span class="sxs-lookup"><span data-stu-id="c66c7-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="c66c7-142">物件初始化運算式可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="c66c7-142">Object initializers can be nested.</span></span> <span data-ttu-id="c66c7-143">在下列範例中, `AddressClass`是具有兩個屬性 ( `City`和`State`) 的類別, 而`Customer`類別具有`Address`屬於實例的`AddressClass`屬性。</span><span class="sxs-lookup"><span data-stu-id="c66c7-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="c66c7-144">初始化清單不可以是空的。</span><span class="sxs-lookup"><span data-stu-id="c66c7-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="c66c7-145">要初始化的實例不可以是 Object 類型。</span><span class="sxs-lookup"><span data-stu-id="c66c7-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="c66c7-146">要初始化的類別成員不能是共用成員、唯讀成員、常數或方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c66c7-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="c66c7-147">無法為已初始化的類別成員編制索引或限定。</span><span class="sxs-lookup"><span data-stu-id="c66c7-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="c66c7-148">下列範例會引發編譯器錯誤:</span><span class="sxs-lookup"><span data-stu-id="c66c7-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="c66c7-149">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c66c7-149">Anonymous Types</span></span>  
 <span data-ttu-id="c66c7-150">匿名型別會使用物件初始化運算式, 來建立您未明確定義和命名的新類型實例。</span><span class="sxs-lookup"><span data-stu-id="c66c7-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="c66c7-151">相反地, 編譯器會根據您在物件初始化運算式清單中指定的屬性來產生型別。</span><span class="sxs-lookup"><span data-stu-id="c66c7-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="c66c7-152">因為未指定類型的名稱, 所以稱為*匿名型別*。</span><span class="sxs-lookup"><span data-stu-id="c66c7-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="c66c7-153">例如, 比較的下列宣告與先前`cust6`的宣告。</span><span class="sxs-lookup"><span data-stu-id="c66c7-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="c66c7-154">唯一的不同之處在于, 在資料類型之後`New`未指定任何名稱。</span><span class="sxs-lookup"><span data-stu-id="c66c7-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="c66c7-155">不過, 這種情況會有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="c66c7-155">However, what happens is quite different.</span></span> <span data-ttu-id="c66c7-156">編譯器會定義具有兩個屬性 ( `Name`和`City`) 的新匿名型別, 並使用指定的值建立它的實例。</span><span class="sxs-lookup"><span data-stu-id="c66c7-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="c66c7-157">型別推斷會將範例`Name`中`City`的和類型判斷為字串。</span><span class="sxs-lookup"><span data-stu-id="c66c7-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c66c7-158">匿名型別的名稱是由編譯器所產生, 而且可能會因編譯而異。</span><span class="sxs-lookup"><span data-stu-id="c66c7-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="c66c7-159">您的程式碼不應該使用或依賴匿名型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="c66c7-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="c66c7-160">因為類型的名稱無法使用, 所以您不能使用`As`子句`cust13`來宣告。</span><span class="sxs-lookup"><span data-stu-id="c66c7-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="c66c7-161">必須推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="c66c7-161">Its type must be inferred.</span></span> <span data-ttu-id="c66c7-162">如果沒有使用晚期繫結, 這會限制使用匿名型別來做為本機變數。</span><span class="sxs-lookup"><span data-stu-id="c66c7-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="c66c7-163">匿名型別提供查詢的[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]關鍵支援。</span><span class="sxs-lookup"><span data-stu-id="c66c7-163">Anonymous types provide critical support for [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="c66c7-164">如需在查詢中使用匿名型別的詳細資訊, 請參閱[匿名](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)型別和 Visual Basic 中的[LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="c66c7-164">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="c66c7-165">匿名型別的相關備註</span><span class="sxs-lookup"><span data-stu-id="c66c7-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="c66c7-166">一般來說, 匿名型別宣告中的所有或大部分屬性都是索引鍵屬性, 這是藉由在屬性名稱`Key`前面輸入關鍵字來表示。</span><span class="sxs-lookup"><span data-stu-id="c66c7-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="c66c7-167">如需索引鍵屬性的詳細資訊, 請參閱索引[鍵](../../../../visual-basic/language-reference/modifiers/key.md)。</span><span class="sxs-lookup"><span data-stu-id="c66c7-167">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="c66c7-168">就像命名類型, 匿名型別定義的初始化運算式清單必須宣告至少一個屬性。</span><span class="sxs-lookup"><span data-stu-id="c66c7-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="c66c7-169">宣告匿名型別的實例時, 編譯器會產生相符的匿名型別定義。</span><span class="sxs-lookup"><span data-stu-id="c66c7-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="c66c7-170">屬性的名稱和資料類型取自實例宣告, 並由編譯器在定義中包含。</span><span class="sxs-lookup"><span data-stu-id="c66c7-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="c66c7-171">屬性不會事先命名並定義, 就像是針對已命名的型別一樣。</span><span class="sxs-lookup"><span data-stu-id="c66c7-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="c66c7-172">系統會推斷其類型。</span><span class="sxs-lookup"><span data-stu-id="c66c7-172">Their types are inferred.</span></span> <span data-ttu-id="c66c7-173">您不能使用`As`子句來指定屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c66c7-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="c66c7-174">匿名型別也可以用數種其他方式來建立其屬性的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="c66c7-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="c66c7-175">例如, 匿名型別屬性可以同時接受變數的名稱和值, 或是另一個物件之屬性的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="c66c7-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="c66c7-176">如需有關在匿名型別中定義屬性之選項的詳細[資訊, 請參閱如何:在匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)宣告中推斷屬性名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="c66c7-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66c7-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c66c7-177">See also</span></span>

- [<span data-ttu-id="c66c7-178">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="c66c7-178">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="c66c7-179">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c66c7-179">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="c66c7-180">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="c66c7-180">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c66c7-181">如何：在匿名型別宣告中推斷屬性名稱和類型</span><span class="sxs-lookup"><span data-stu-id="c66c7-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="c66c7-182">Key</span><span class="sxs-lookup"><span data-stu-id="c66c7-182">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
- [<span data-ttu-id="c66c7-183">如何：使用物件初始化運算式宣告物件</span><span class="sxs-lookup"><span data-stu-id="c66c7-183">How to: Declare an Object by Using an Object Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
