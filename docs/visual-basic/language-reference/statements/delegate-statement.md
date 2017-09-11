---
title: "Delegate 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
dev_langs:
- VB
helpviewer_keywords:
- delegate keyword
- Delegate statement
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
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
ms.openlocfilehash: 052ef837dfe4f9d34081839eea47e35bc4824afd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="delegate-statement"></a><span data-ttu-id="c4ff7-102">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="c4ff7-102">Delegate Statement</span></span>
<span data-ttu-id="c4ff7-103">用來宣告委派。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-103">Used to declare a delegate.</span></span> <span data-ttu-id="c4ff7-104">委派是參考類型，這是指`Shared`方法的型別或物件的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-104">A delegate is a reference type that refers to a `Shared` method of a type or to an instance method of an object.</span></span> <span data-ttu-id="c4ff7-105">任何具有相符的參數和傳回型別程序可以用來建立這個委派類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-105">Any procedure with matching parameter and return types can be used to create an instance of this delegate class.</span></span> <span data-ttu-id="c4ff7-106">程序可以再接著會透過叫用委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-106">The procedure can then later be invoked by means of the delegate instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ff7-107">語法</span><span class="sxs-lookup"><span data-stu-id="c4ff7-107">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c4ff7-108">組件</span><span class="sxs-lookup"><span data-stu-id="c4ff7-108">Parts</span></span>  
  
|<span data-ttu-id="c4ff7-109">詞彙</span><span class="sxs-lookup"><span data-stu-id="c4ff7-109">Term</span></span>|<span data-ttu-id="c4ff7-110">定義</span><span class="sxs-lookup"><span data-stu-id="c4ff7-110">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="c4ff7-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-111">Optional.</span></span> <span data-ttu-id="c4ff7-112">這個委派所套用的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-112">List of attributes that apply to this delegate.</span></span> <span data-ttu-id="c4ff7-113">以逗號分隔多個屬性。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-113">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="c4ff7-114">您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧括住 (「`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-114">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>|  
|`accessmodifier`|<span data-ttu-id="c4ff7-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-115">Optional.</span></span> <span data-ttu-id="c4ff7-116">指定哪些程式碼可以存取的委派。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-116">Specifies what code can access the delegate.</span></span> <span data-ttu-id="c4ff7-117">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c4ff7-117">Can be one of the following:</span></span><br /><br /><span data-ttu-id="c4ff7-118"> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-118"> -   [Public](../../../visual-basic/language-reference/modifiers/public.md).</span></span> <span data-ttu-id="c4ff7-119">任何可以存取的項目宣告委派的程式碼可以存取它。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-119">Any code that can access the element that declares the delegate can access it.</span></span><br /><span data-ttu-id="c4ff7-120">-   [受保護的](../../../visual-basic/language-reference/modifiers/protected.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-120">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md).</span></span> <span data-ttu-id="c4ff7-121">只有在委派的類別或衍生的類別中的程式碼可以存取它。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-121">Only code within the delegate's class or a derived class can access it.</span></span><br /><span data-ttu-id="c4ff7-122">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-122">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md).</span></span> <span data-ttu-id="c4ff7-123">相同的組件中的程式碼可以存取的委派。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-123">Only code within the same assembly can access the delegate.</span></span><br /><span data-ttu-id="c4ff7-124">-   [私用](../../../visual-basic/language-reference/modifiers/private.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-124">-   [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="c4ff7-125">宣告委派的項目內的程式碼可以存取它。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-125">Only code within the element that declares the delegate can access it.</span></span><br /><br /> <span data-ttu-id="c4ff7-126">您可以指定`Protected Friend`啟用委派的類別、 衍生的類別或相同的組件內的程式碼存取權。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-126">You can specify `Protected Friend` to enable access from code within the delegate's class, a derived class, or the same assembly.</span></span>|  
|`Shadows`|<span data-ttu-id="c4ff7-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-127">Optional.</span></span> <span data-ttu-id="c4ff7-128">表示此委派會重新宣告，並隱藏基底類別中的多載項目集的相同具名的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-128">Indicates that this delegate redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="c4ff7-129">您可以使用任何其他類型遮蔽任何一種已宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-129">You can shadow any kind of declared element with any other kind.</span></span><br /><br /> <span data-ttu-id="c4ff7-130">無法從遮蔽項目的衍生類別內使用遮蔽的項目，除了從無法存取遮蔽項目的位置以外。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-130">A shadowed element is unavailable from within the derived class that shadows it, except from where the shadowing element is inaccessible.</span></span> <span data-ttu-id="c4ff7-131">例如，如果`Private`項目會遮蔽基底類別的項目，並沒有存取權限的程式碼`Private`項目會改為存取基底類別的項目。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-131">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>|  
|`Sub`|<span data-ttu-id="c4ff7-132">選擇性，但其中`Sub`或`Function`必須出現。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-132">Optional, but either `Sub` or `Function` must appear.</span></span> <span data-ttu-id="c4ff7-133">將此程序作為委派宣告`Sub`沒有傳回值的程序。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-133">Declares this procedure as a delegate `Sub` procedure that does not return a value.</span></span>|  
|`Function`|<span data-ttu-id="c4ff7-134">選擇性，但其中`Sub`或`Function`必須出現。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-134">Optional, but either `Sub` or `Function` must appear.</span></span> <span data-ttu-id="c4ff7-135">將此程序作為委派宣告`Function`傳回值的程序。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-135">Declares this procedure as a delegate `Function` procedure that returns a value.</span></span>|  
|`name`|<span data-ttu-id="c4ff7-136">必要項。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-136">Required.</span></span> <span data-ttu-id="c4ff7-137">為目前的委派型別。依照標準變數命名慣例。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-137">Name of the delegate type; follows standard variable naming conventions.</span></span>|  
|`typeparamlist`|<span data-ttu-id="c4ff7-138">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-138">Optional.</span></span> <span data-ttu-id="c4ff7-139">這個委派型別參數的清單。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-139">List of type parameters for this delegate.</span></span> <span data-ttu-id="c4ff7-140">多個類型參數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-140">Multiple type parameters are separated by commas.</span></span> <span data-ttu-id="c4ff7-141">（選擇性） 每個類型參數可以宣告變數使用`In`和`Out`泛型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-141">Optionally, each type parameter can be declared variant by using `In` and `Out` generic modifiers.</span></span> <span data-ttu-id="c4ff7-142">您必須將[類型清單](../../../visual-basic/language-reference/statements/type-list.md)括號括住，並介紹它與`Of`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-142">You must enclose the [Type List](../../../visual-basic/language-reference/statements/type-list.md) in parentheses and introduce it with the `Of` keyword.</span></span>|  
|`parameterlist`|<span data-ttu-id="c4ff7-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-143">Optional.</span></span> <span data-ttu-id="c4ff7-144">呼叫時，會傳遞至程序的參數清單。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-144">List of parameters that are passed to the procedure when it is called.</span></span> <span data-ttu-id="c4ff7-145">您必須將[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)括號括住。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-145">You must enclose the [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) in parentheses.</span></span>|  
|`type`|<span data-ttu-id="c4ff7-146">如果您指定為必要項`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-146">Required if you specify a `Function` procedure.</span></span> <span data-ttu-id="c4ff7-147">傳回值的資料型別。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-147">Data type of the return value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4ff7-148">備註</span><span class="sxs-lookup"><span data-stu-id="c4ff7-148">Remarks</span></span>  
 <span data-ttu-id="c4ff7-149">`Delegate`陳述式會定義委派類別的參數和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-149">The `Delegate` statement defines the parameter and return types of a delegate class.</span></span> <span data-ttu-id="c4ff7-150">任何具有相符的參數和傳回型別程序可以用來建立這個委派類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-150">Any procedure with matching parameters and return types can be used to create an instance of this delegate class.</span></span> <span data-ttu-id="c4ff7-151">此程序可以接著會叫用透過委派執行個體，藉由呼叫的委派`Invoke`方法。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-151">The procedure can then later be invoked by means of the delegate instance, by calling the delegate's `Invoke` method.</span></span>  
  
 <span data-ttu-id="c4ff7-152">在命名空間、 模組、 類別或結構的層級，但程序內不可以宣告委派。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-152">Delegates can be declared at the namespace, module, class, or structure level, but not within a procedure.</span></span>  
  
 <span data-ttu-id="c4ff7-153">每個委派類別會為傳遞的建構函式定義物件方法的規格。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-153">Each delegate class defines a constructor that is passed the specification of an object method.</span></span> <span data-ttu-id="c4ff7-154">委派建構函式的引數必須是方法或 lambda 運算式的參考。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-154">An argument to a delegate constructor must be a reference to a method, or a lambda expression.</span></span>  
  
 <span data-ttu-id="c4ff7-155">若要指定方法的參考，請使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="c4ff7-155">To specify a reference to a method, use the following syntax:</span></span>  
  
 <span data-ttu-id="c4ff7-156">`AddressOf` [`expression`.]`methodname`</span><span class="sxs-lookup"><span data-stu-id="c4ff7-156">`AddressOf` [`expression`.]`methodname`</span></span>  
  
 <span data-ttu-id="c4ff7-157">編譯時期型別`expression`必須是類別或介面，包含指定之名稱的簽章符合委派類別的簽章的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-157">The compile-time type of the `expression` must be the name of a class or an interface that contains a method of the specified name whose signature matches the signature of the delegate class.</span></span> <span data-ttu-id="c4ff7-158">`methodname`可以是共用的方法或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-158">The `methodname` can be either a shared method or an instance method.</span></span> <span data-ttu-id="c4ff7-159">`methodname`不是選擇性的即使您建立類別的預設方法的委派。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-159">The `methodname` is not optional, even if you create a delegate for the default method of the class.</span></span>  
  
 <span data-ttu-id="c4ff7-160">若要指定 lambda 運算式，請使用下列語法︰</span><span class="sxs-lookup"><span data-stu-id="c4ff7-160">To specify a lambda expression, use the following syntax:</span></span>  
  
 <span data-ttu-id="c4ff7-161">`Function`([`parm` As `type`, `parm2` As `type2`, ...])`expression`</span><span class="sxs-lookup"><span data-stu-id="c4ff7-161">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span></span>  
  
 <span data-ttu-id="c4ff7-162">函式的簽章必須符合委派類型。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-162">The signature of the function must match that of the delegate type.</span></span> <span data-ttu-id="c4ff7-163">如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-163">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="c4ff7-164">如需委派的詳細資訊，請參閱[委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-164">For more information about delegates, see [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4ff7-165">範例</span><span class="sxs-lookup"><span data-stu-id="c4ff7-165">Example</span></span>  
 <span data-ttu-id="c4ff7-166">下列範例會使用`Delegate`陳述式來宣告委派，以便操作兩個數字並傳回一個數字。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-166">The following example uses the `Delegate` statement to declare a delegate for operating on two numbers and returning a number.</span></span> <span data-ttu-id="c4ff7-167">`DelegateTest`方法會採用這種類型的委派的執行個體，並將其操作的編號組。</span><span class="sxs-lookup"><span data-stu-id="c4ff7-167">The `DelegateTest` method takes an instance of a delegate of this type and uses it to operate on pairs of numbers.</span></span>  
  
 <span data-ttu-id="c4ff7-168">[!code-vb[VbVbalrDelegates #&14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4ff7-168">[!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ff7-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4ff7-169">See Also</span></span>  
 <span data-ttu-id="c4ff7-170">[AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-170">[AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="c4ff7-171"> [Of](../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-171"> [Of](../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="c4ff7-172"> [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-172"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="c4ff7-173"> [如何︰ 使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-173"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="c4ff7-174"> [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-174"> [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="c4ff7-175"> [共變數和反變數](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-175"> [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span></span>  
<span data-ttu-id="c4ff7-176"> [在](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="c4ff7-176"> [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) </span></span>  
<span data-ttu-id="c4ff7-177"> [向外](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="c4ff7-177"> [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span></span>
