---
title: 物件初始設定式：具名和匿名類型 (Visual Basic)
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
ms.openlocfilehash: f65352ebd9ca12aaed6b469c5df136301e9f839c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620535"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="ce549-102">物件初始設定式：具名和匿名類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce549-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="ce549-103">物件初始設定式可讓您使用單一運算式中指定的複雜物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ce549-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="ce549-104">它們可用來建立執行個體的具名型別和匿名型別。</span><span class="sxs-lookup"><span data-stu-id="ce549-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="ce549-105">宣告</span><span class="sxs-lookup"><span data-stu-id="ce549-105">Declarations</span></span>  
 <span data-ttu-id="ce549-106">具名和匿名型別的執行個體的宣告可以看起來幾乎完全相同，但其效果不相同。</span><span class="sxs-lookup"><span data-stu-id="ce549-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="ce549-107">每個類別目錄具有功能以及其本身的限制。</span><span class="sxs-lookup"><span data-stu-id="ce549-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="ce549-108">下列範例示範宣告和初始化具名的類別的執行個體的便利方式`Customer`，使用物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="ce549-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="ce549-109">請注意，類別的名稱關鍵字後面指定`New`。</span><span class="sxs-lookup"><span data-stu-id="ce549-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 <span data-ttu-id="ce549-110">匿名型別已經沒有可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce549-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="ce549-111">因此匿名型別的具現化不能包含的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="ce549-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 <span data-ttu-id="ce549-112">需求和兩個宣告的結果不相同。</span><span class="sxs-lookup"><span data-stu-id="ce549-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="ce549-113">針對`namedCust`，則`Customer`類別，具有`Name`屬性必須已經存在，並宣告會建立該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce549-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="ce549-114">針對`anonymousCust`，編譯器會定義新的類別具有一個屬性，一個字串稱為`Name`，並建立該類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce549-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="ce549-115">具名的類型</span><span class="sxs-lookup"><span data-stu-id="ce549-115">Named Types</span></span>  
 <span data-ttu-id="ce549-116">物件初始設定式會提供簡單的方式來呼叫類型的建構函式，並在單一陳述式將部分或所有屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ce549-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="ce549-117">編譯器會叫用適當的建構函式陳述式： 預設建構函式如果不使用引數呈現或如果會傳送一或多個引數的參數化建構函式。</span><span class="sxs-lookup"><span data-stu-id="ce549-117">The compiler invokes the appropriate constructor for the statement: the default constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="ce549-118">在那之後，初始設定式清單中出現的順序會初始化指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ce549-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="ce549-119">初始設定式清單中的每個初始設定包含初始值之類別成員的指派。</span><span class="sxs-lookup"><span data-stu-id="ce549-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="ce549-120">當已定義類別時，決定的名稱和資料類型的成員。</span><span class="sxs-lookup"><span data-stu-id="ce549-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="ce549-121">在下列範例中，`Customer`的類別必須存在，並必須有成員具名`Name`和`City`，可以接受的字串值。</span><span class="sxs-lookup"><span data-stu-id="ce549-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 <span data-ttu-id="ce549-122">或者，您也可以使用下列程式碼取得相同的結果：</span><span class="sxs-lookup"><span data-stu-id="ce549-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 <span data-ttu-id="ce549-123">每個這些宣告就相當於下列的範例中，建立`Customer`物件使用預設建構函式，然後再指定初始值`Name`並`City`屬性使用`With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ce549-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the default constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 <span data-ttu-id="ce549-124">如果`Customer`類別包含可讓您傳送的值中的參數化建構函式`Name`，例如，您可以也宣告並初始化`Customer`物件如下：</span><span class="sxs-lookup"><span data-stu-id="ce549-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 <span data-ttu-id="ce549-125">您沒有初始化所有的屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ce549-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 <span data-ttu-id="ce549-126">不過，在初始設定清單不可為空白。</span><span class="sxs-lookup"><span data-stu-id="ce549-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="ce549-127">未初始化的屬性會保留其預設值。</span><span class="sxs-lookup"><span data-stu-id="ce549-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="ce549-128">使用具名類型的型別推斷</span><span class="sxs-lookup"><span data-stu-id="ce549-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="ce549-129">您可以縮短的宣告的程式碼`cust1`藉由結合物件初始設定式和區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="ce549-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="ce549-130">這可讓您省略`As`在變數宣告中的子句。</span><span class="sxs-lookup"><span data-stu-id="ce549-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="ce549-131">變數的資料型別會從指派所建立的物件型別推斷。</span><span class="sxs-lookup"><span data-stu-id="ce549-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="ce549-132">在下列範例中，類型`cust6`是`Customer`。</span><span class="sxs-lookup"><span data-stu-id="ce549-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="ce549-133">具名類型的相關註解</span><span class="sxs-lookup"><span data-stu-id="ce549-133">Remarks About Named Types</span></span>  
  
-   <span data-ttu-id="ce549-134">類別成員無法初始化物件初始設定式清單中一個以上的時間。</span><span class="sxs-lookup"><span data-stu-id="ce549-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="ce549-135">Deklarace`cust7`會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce549-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   <span data-ttu-id="ce549-136">成員可以用來初始化本身或另一個欄位中。</span><span class="sxs-lookup"><span data-stu-id="ce549-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="ce549-137">如果它已初始化以前，如下列宣告所示，存取成員`cust8`，將會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="ce549-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="ce549-138">請記住，處理會使用物件初始設定式的宣告時，會發生第一件事是適當的建構函式會叫用。</span><span class="sxs-lookup"><span data-stu-id="ce549-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="ce549-139">在那之後，會初始化初始設定式清單中的個別欄位。</span><span class="sxs-lookup"><span data-stu-id="ce549-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="ce549-140">在下列範例中，預設值`Name`指派給`cust8`，並初始化的值指派在`cust9`。</span><span class="sxs-lookup"><span data-stu-id="ce549-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     <span data-ttu-id="ce549-141">下列範例會使用參數化建構函式從`cust3`並`cust4`來宣告和初始化`cust10`和`cust11`。</span><span class="sxs-lookup"><span data-stu-id="ce549-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   <span data-ttu-id="ce549-142">物件初始設定式可以是巢狀。</span><span class="sxs-lookup"><span data-stu-id="ce549-142">Object initializers can be nested.</span></span> <span data-ttu-id="ce549-143">在下列範例中，`AddressClass`是具有兩個屬性的類別`City`並`State`，而`Customer`類別具有`Address`的執行個體的屬性`AddressClass`。</span><span class="sxs-lookup"><span data-stu-id="ce549-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   <span data-ttu-id="ce549-144">在初始設定清單不可為空白。</span><span class="sxs-lookup"><span data-stu-id="ce549-144">The initialization list cannot be empty.</span></span>  
  
-   <span data-ttu-id="ce549-145">正在初始化的執行個體不能屬於類型物件。</span><span class="sxs-lookup"><span data-stu-id="ce549-145">The instance being initialized cannot be of type Object.</span></span>  
  
-   <span data-ttu-id="ce549-146">要初始化的類別成員不能共用的成員、 唯讀成員、 常數或方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="ce549-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
-   <span data-ttu-id="ce549-147">要初始化的類別成員無法編製索引，或限定。</span><span class="sxs-lookup"><span data-stu-id="ce549-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="ce549-148">下列範例會產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="ce549-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="ce549-149">匿名類型</span><span class="sxs-lookup"><span data-stu-id="ce549-149">Anonymous Types</span></span>  
 <span data-ttu-id="ce549-150">匿名型別會使用物件初始設定式來建立新您未明確定義的型別和名稱的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ce549-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="ce549-151">相反地，編譯器會產生類型，以根據您指定的屬性在物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="ce549-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="ce549-152">未指定類型的名稱，因為它指*匿名型別*。</span><span class="sxs-lookup"><span data-stu-id="ce549-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="ce549-153">例如，比較到較早的下列宣告`cust6`。</span><span class="sxs-lookup"><span data-stu-id="ce549-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 <span data-ttu-id="ce549-154">唯一的差別在語法上是沒有指定任何名稱之後,`New`資料類型。</span><span class="sxs-lookup"><span data-stu-id="ce549-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="ce549-155">不過，會發生什麼事都相當不同。</span><span class="sxs-lookup"><span data-stu-id="ce549-155">However, what happens is quite different.</span></span> <span data-ttu-id="ce549-156">編譯器會定義新的匿名型別，有兩個屬性，`Name`和`City`，並建立它的執行個體使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="ce549-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="ce549-157">類型推斷的類型可決定`Name`和`City`在範例中為字串。</span><span class="sxs-lookup"><span data-stu-id="ce549-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ce549-158">匿名型別名稱由編譯器產生，並可能會有所不同的編譯。</span><span class="sxs-lookup"><span data-stu-id="ce549-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="ce549-159">您的程式碼不應該使用或依賴匿名型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce549-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="ce549-160">因為型別名稱無法使用，您無法使用`As`子句來宣告`cust13`。</span><span class="sxs-lookup"><span data-stu-id="ce549-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="ce549-161">必須推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="ce549-161">Its type must be inferred.</span></span> <span data-ttu-id="ce549-162">不使用晚期繫結，這會限制使用本機變數的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="ce549-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="ce549-163">匿名型別提供重要支援[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="ce549-163">Anonymous types provide critical support for [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="ce549-164">在查詢中的匿名型別的用法的相關資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)並[在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="ce549-164">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="ce549-165">匿名型別的備註</span><span class="sxs-lookup"><span data-stu-id="ce549-165">Remarks About Anonymous Types</span></span>  
  
-   <span data-ttu-id="ce549-166">一般來說，所有或大部分的匿名類型宣告中的屬性會是索引鍵屬性，由輸入關鍵字`Key`屬性名稱前面。</span><span class="sxs-lookup"><span data-stu-id="ce549-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     <span data-ttu-id="ce549-167">如需有關索引鍵屬性的詳細資訊，請參閱[金鑰](../../../../visual-basic/language-reference/modifiers/key.md)。</span><span class="sxs-lookup"><span data-stu-id="ce549-167">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
-   <span data-ttu-id="ce549-168">匿名型別定義都必須宣告至少一個屬性，例如具名類型初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="ce549-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   <span data-ttu-id="ce549-169">宣告匿名類型的執行個體時，編譯器會產生相符的匿名型別定義。</span><span class="sxs-lookup"><span data-stu-id="ce549-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="ce549-170">名稱和資料類型的屬性會從執行個體宣告，而且會包含在定義中，編譯器。</span><span class="sxs-lookup"><span data-stu-id="ce549-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="ce549-171">屬性不是名為和具名型別，其方式時，預先定義。</span><span class="sxs-lookup"><span data-stu-id="ce549-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="ce549-172">會推斷其類型。</span><span class="sxs-lookup"><span data-stu-id="ce549-172">Their types are inferred.</span></span> <span data-ttu-id="ce549-173">您無法使用，以指定屬性的資料型別`As`子句。</span><span class="sxs-lookup"><span data-stu-id="ce549-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
-   <span data-ttu-id="ce549-174">匿名型別也可以建立的名稱和其屬性的值以數種其他方式。</span><span class="sxs-lookup"><span data-stu-id="ce549-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="ce549-175">例如，匿名型別屬性可能需要的名稱和變數，或名稱的值與另一個物件的屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ce549-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     <span data-ttu-id="ce549-176">如需匿名型別中定義屬性選項的詳細資訊，請參閱[How to:推斷屬性名稱和匿名類型宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="ce549-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce549-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce549-177">See also</span></span>
- [<span data-ttu-id="ce549-178">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="ce549-178">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ce549-179">匿名類型</span><span class="sxs-lookup"><span data-stu-id="ce549-179">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="ce549-180">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="ce549-180">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ce549-181">如何：推斷屬性名稱和匿名類型宣告中的類型</span><span class="sxs-lookup"><span data-stu-id="ce549-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="ce549-182">Key</span><span class="sxs-lookup"><span data-stu-id="ce549-182">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
- [<span data-ttu-id="ce549-183">如何：使用物件初始設定式宣告物件</span><span class="sxs-lookup"><span data-stu-id="ce549-183">How to: Declare an Object by Using an Object Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
