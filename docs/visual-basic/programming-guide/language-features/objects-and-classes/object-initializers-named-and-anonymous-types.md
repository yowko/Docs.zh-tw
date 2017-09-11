---
title: "物件初始設定式︰ 具名和匿名類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
dev_langs:
- VB
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d3c89fb0a7b7c535f1b46c208ac47f58513208ba
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="d6e37-102">物件初始設定式：具名和匿名類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6e37-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="d6e37-103">物件初始設定式可讓您使用單一運算式，指定複雜物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6e37-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="d6e37-104">它們可以用來建立執行個體的具名型別，而匿名型別。</span><span class="sxs-lookup"><span data-stu-id="d6e37-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="d6e37-105">宣告</span><span class="sxs-lookup"><span data-stu-id="d6e37-105">Declarations</span></span>  
 <span data-ttu-id="d6e37-106">具名和匿名型別的執行個體的宣告可以看起來幾乎相同，但其效果不相同。</span><span class="sxs-lookup"><span data-stu-id="d6e37-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="d6e37-107">每個類別都有能力和其本身的限制。</span><span class="sxs-lookup"><span data-stu-id="d6e37-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="d6e37-108">下列範例示範宣告和初始化具名類別的執行個體可方便`Customer`，使用物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="d6e37-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="d6e37-109">請注意類別的名稱會指定關鍵字之後`New`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 <span data-ttu-id="d6e37-110">[!code-vb[VbVbalrObjectInit #&1;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-110">[!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-111">匿名型別已經沒有可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6e37-111">An anonymous type has no usable name.</span></span> <span data-ttu-id="d6e37-112">因此匿名型別的具現化不能包含類別名稱。</span><span class="sxs-lookup"><span data-stu-id="d6e37-112">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 <span data-ttu-id="d6e37-113">[!code-vb[VbVbalrObjectInit #&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-113">[!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-114">需求和結果的兩個宣告都不相同。</span><span class="sxs-lookup"><span data-stu-id="d6e37-114">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="d6e37-115">如`namedCust`、`Customer`類別具有`Name`屬性必須存在，並宣告會建立該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6e37-115">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="d6e37-116">如`anonymousCust`，編譯器會定義一個屬性，名為字串的新類別`Name`，並建立該類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6e37-116">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="d6e37-117">具名型別</span><span class="sxs-lookup"><span data-stu-id="d6e37-117">Named Types</span></span>  
 <span data-ttu-id="d6e37-118">物件初始設定式會提供簡單的方法呼叫的型別建構函式，然後設定在單一陳述式中的 部分或所有屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d6e37-118">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="d6e37-119">編譯器會叫用適當的建構函式的陳述式︰ 預設建構函式如果不使用引數或如果會傳送一個或多個引數的參數化建構函式。</span><span class="sxs-lookup"><span data-stu-id="d6e37-119">The compiler invokes the appropriate constructor for the statement: the default constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="d6e37-120">之後，會顯示在 初始設定式清單的順序會初始化所指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6e37-120">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="d6e37-121">初始設定式清單中的每個初始設定包含指派初始值類別的成員。</span><span class="sxs-lookup"><span data-stu-id="d6e37-121">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="d6e37-122">在定義類別時，決定名稱和資料類型的成員。</span><span class="sxs-lookup"><span data-stu-id="d6e37-122">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="d6e37-123">在下列範例中，`Customer`類別必須存在，而且必須具有成員名稱為`Name`和`City`，可以接受的字串值。</span><span class="sxs-lookup"><span data-stu-id="d6e37-123">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 <span data-ttu-id="d6e37-124">[!code-vb[VbVbalrObjectInit #&3;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-124">[!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-125">或者，您可以使用下列程式碼取得相同的結果︰</span><span class="sxs-lookup"><span data-stu-id="d6e37-125">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 <span data-ttu-id="d6e37-126">[!code-vb[VbVbalrObjectInit #&4;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-126">[!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-127">這些宣告的每一個都是相當於下列的範例中，建立`Customer`物件使用預設建構函式，並接著指定的初始值`Name`和`City`屬性使用`With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d6e37-127">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the default constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 <span data-ttu-id="d6e37-128">[!code-vb[VbVbalrObjectInit #&5;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-128">[!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-129">如果`Customer`類別包含可讓您傳送的值中的參數化建構函式`Name`，比方說，也宣告及初始化`Customer`物件如下︰</span><span class="sxs-lookup"><span data-stu-id="d6e37-129">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 <span data-ttu-id="d6e37-130">[!code-vb[VbVbalrObjectInit #&6;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-130">[!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-131">您沒有初始化所有的屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d6e37-131">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 <span data-ttu-id="d6e37-132">[!code-vb[VbVbalrObjectInit #&7;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-132">[!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-133">不過，初始設定清單不能空白。</span><span class="sxs-lookup"><span data-stu-id="d6e37-133">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="d6e37-134">未初始化的屬性會保留其預設值。</span><span class="sxs-lookup"><span data-stu-id="d6e37-134">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="d6e37-135">具名型別的型別推斷</span><span class="sxs-lookup"><span data-stu-id="d6e37-135">Type Inference with Named Types</span></span>  
 <span data-ttu-id="d6e37-136">您可以縮短的宣告的程式碼`cust1`結合物件初始設定式和區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="d6e37-136">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="d6e37-137">這樣您就可以省略`As`在變數宣告中的子句。</span><span class="sxs-lookup"><span data-stu-id="d6e37-137">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="d6e37-138">指派所建立的物件型別來推斷變數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="d6e37-138">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="d6e37-139">在下列範例中，類型`cust6`是`Customer`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-139">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 <span data-ttu-id="d6e37-140">[!code-vb[VbVbalrObjectInit #&8;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-140">[!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]</span></span>  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="d6e37-141">具名型別的備註</span><span class="sxs-lookup"><span data-stu-id="d6e37-141">Remarks About Named Types</span></span>  
  
-   <span data-ttu-id="d6e37-142">類別成員無法初始化物件初始設定式清單中一個以上的時間。</span><span class="sxs-lookup"><span data-stu-id="d6e37-142">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="d6e37-143">宣告`cust7`會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="d6e37-143">The declaration of `cust7` causes an error.</span></span>  
  
     <span data-ttu-id="d6e37-144">[!code-vb[VbVbalrObjectInit #&9;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-144">[!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]</span></span>  
  
-   <span data-ttu-id="d6e37-145">成員可以用來初始化本身或其他欄位。</span><span class="sxs-lookup"><span data-stu-id="d6e37-145">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="d6e37-146">如果之前就已初始化，如下列宣告所示，存取成員`cust8`，將會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="d6e37-146">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="d6e37-147">請記住，處理使用物件初始設定式的宣告時，發生第一件事，會叫用適當的建構函式。</span><span class="sxs-lookup"><span data-stu-id="d6e37-147">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="d6e37-148">之後，會初始化初始設定式清單中的個別欄位。</span><span class="sxs-lookup"><span data-stu-id="d6e37-148">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="d6e37-149">在下列範例中，預設值為`Name`指派給`cust8`，並已初始化的值會指派在`cust9`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-149">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     <span data-ttu-id="d6e37-150">[!code-vb[VbVbalrObjectInit #&10;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-150">[!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]</span></span>  
  
     <span data-ttu-id="d6e37-151">下列範例會使用參數化建構函式從`cust3`和`cust4`宣告並初始化`cust10`和`cust11`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-151">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     <span data-ttu-id="d6e37-152">[!code-vb[VbVbalrObjectInit #&11;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-152">[!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]</span></span>  
  
-   <span data-ttu-id="d6e37-153">物件初始設定式可以是巢狀。</span><span class="sxs-lookup"><span data-stu-id="d6e37-153">Object initializers can be nested.</span></span> <span data-ttu-id="d6e37-154">在下列範例中，`AddressClass`是類別，有兩個屬性，`City`和`State`，而`Customer`類別具有`Address`的執行個體的屬性`AddressClass`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-154">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     <span data-ttu-id="d6e37-155">[!code-vb[VbVbalrObjectInit #&12;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-155">[!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]</span></span>  
  
-   <span data-ttu-id="d6e37-156">初始化清單不能空白。</span><span class="sxs-lookup"><span data-stu-id="d6e37-156">The initialization list cannot be empty.</span></span>  
  
-   <span data-ttu-id="d6e37-157">正在初始化的執行個體不能是型別物件。</span><span class="sxs-lookup"><span data-stu-id="d6e37-157">The instance being initialized cannot be of type Object.</span></span>  
  
-   <span data-ttu-id="d6e37-158">要初始化的類別成員不能共用的成員、 唯讀成員、 常數或方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d6e37-158">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
-   <span data-ttu-id="d6e37-159">要初始化的類別成員無法編製索引，或限定。</span><span class="sxs-lookup"><span data-stu-id="d6e37-159">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="d6e37-160">下列範例會產生編譯器錯誤︰</span><span class="sxs-lookup"><span data-stu-id="d6e37-160">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="d6e37-161">匿名類型</span><span class="sxs-lookup"><span data-stu-id="d6e37-161">Anonymous Types</span></span>  
 <span data-ttu-id="d6e37-162">匿名型別會使用物件初始設定式來建立新您沒有明確定義的型別和名稱的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6e37-162">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="d6e37-163">相反地，編譯器會產生根據您指定的屬性的型別在物件初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="d6e37-163">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="d6e37-164">未指定型別的名稱，因為它指*匿名型別*。</span><span class="sxs-lookup"><span data-stu-id="d6e37-164">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="d6e37-165">例如，比較下列宣告為與前一個`cust6`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-165">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 <span data-ttu-id="d6e37-166">[!code-vb[VbVbalrObjectInit #&13;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-166">[!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]</span></span>  
  
 <span data-ttu-id="d6e37-167">唯一的差別在語法上是沒有指定任何名稱之後,`New`資料類型。</span><span class="sxs-lookup"><span data-stu-id="d6e37-167">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="d6e37-168">不過，會發生什麼事都相當不同。</span><span class="sxs-lookup"><span data-stu-id="d6e37-168">However, what happens is quite different.</span></span> <span data-ttu-id="d6e37-169">編譯器會在定義新的匿名型別具有兩個屬性︰`Name`和`City`，並建立它的執行個體使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="d6e37-169">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="d6e37-170">型別推斷的型別會決定`Name`和`City`在範例中是字串。</span><span class="sxs-lookup"><span data-stu-id="d6e37-170">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d6e37-171">匿名型別名稱由編譯器產生，而有所不同編譯。</span><span class="sxs-lookup"><span data-stu-id="d6e37-171">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="d6e37-172">您的程式碼不應該使用或依賴匿名型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6e37-172">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="d6e37-173">因為沒有可用的型別名稱，您無法使用`As`子句來宣告`cust13`。</span><span class="sxs-lookup"><span data-stu-id="d6e37-173">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="d6e37-174">必須推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="d6e37-174">Its type must be inferred.</span></span> <span data-ttu-id="d6e37-175">不使用晚期繫結，這會限制匿名型別的本機變數使用。</span><span class="sxs-lookup"><span data-stu-id="d6e37-175">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="d6e37-176">匿名型別提供的重要支援[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="d6e37-176">Anonymous types provide critical support for [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries.</span></span> <span data-ttu-id="d6e37-177">匿名型別，在查詢中使用的相關資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e37-177">For more information about the use of anonymous types in queries, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="d6e37-178">匿名型別的備註</span><span class="sxs-lookup"><span data-stu-id="d6e37-178">Remarks About Anonymous Types</span></span>  
  
-   <span data-ttu-id="d6e37-179">一般來說，全部或大部分的匿名型別宣告中的屬性會是索引鍵屬性，以輸入關鍵字`Key`屬性名稱前面。</span><span class="sxs-lookup"><span data-stu-id="d6e37-179">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     <span data-ttu-id="d6e37-180">[!code-vb[VbVbalrObjectInit #&14;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-180">[!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]</span></span>  
  
     <span data-ttu-id="d6e37-181">如需索引鍵屬性的詳細資訊，請參閱[金鑰](../../../../visual-basic/language-reference/modifiers/key.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e37-181">For more information about key properties, see [Key](../../../../visual-basic/language-reference/modifiers/key.md).</span></span>  
  
-   <span data-ttu-id="d6e37-182">例如名為型別初始設定式清單的匿名型別定義都必須宣告一個以上的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6e37-182">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     <span data-ttu-id="d6e37-183">[!code-vb[VbVbalrObjectInit #&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-183">[!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]</span></span>  
  
-   <span data-ttu-id="d6e37-184">匿名型別的執行個體宣告時，編譯器會產生相符的匿名型別定義。</span><span class="sxs-lookup"><span data-stu-id="d6e37-184">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="d6e37-185">名稱和資料類型的屬性取自於執行個體宣告和定義中，編譯器會包含。</span><span class="sxs-lookup"><span data-stu-id="d6e37-185">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="d6e37-186">屬性不是具名的事先定義的具名型別會是。</span><span class="sxs-lookup"><span data-stu-id="d6e37-186">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="d6e37-187">會推斷其型別。</span><span class="sxs-lookup"><span data-stu-id="d6e37-187">Their types are inferred.</span></span> <span data-ttu-id="d6e37-188">您無法使用指定之屬性的資料型別`As`子句。</span><span class="sxs-lookup"><span data-stu-id="d6e37-188">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
-   <span data-ttu-id="d6e37-189">匿名型別也可以建立的名稱和值的屬性其他幾種。</span><span class="sxs-lookup"><span data-stu-id="d6e37-189">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="d6e37-190">例如，匿名型別屬性可能需要的名稱和值的變數，或名稱，另一個物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="d6e37-190">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     <span data-ttu-id="d6e37-191">[!code-vb[VbVbalrObjectInit #&15;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6e37-191">[!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]</span></span>  
  
     <span data-ttu-id="d6e37-192">如需匿名型別中定義屬性選項的詳細資訊，請參閱[How to︰ 推斷屬性名稱和匿名型別宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e37-192">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e37-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e37-193">See Also</span></span>  
 <span data-ttu-id="d6e37-194">[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="d6e37-194">[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="d6e37-195"> [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="d6e37-195"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="d6e37-196"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d6e37-196"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="d6e37-197"> [如何︰ 推斷屬性名稱和匿名型別宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md) </span><span class="sxs-lookup"><span data-stu-id="d6e37-197"> [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md) </span></span>  
<span data-ttu-id="d6e37-198"> [索引鍵](../../../../visual-basic/language-reference/modifiers/key.md) </span><span class="sxs-lookup"><span data-stu-id="d6e37-198"> [Key](../../../../visual-basic/language-reference/modifiers/key.md) </span></span>  
<span data-ttu-id="d6e37-199"> [如何：使用物件初始設定式宣告物件](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)</span><span class="sxs-lookup"><span data-stu-id="d6e37-199"> [How to: Declare an Object by Using an Object Initializer](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)</span></span>
