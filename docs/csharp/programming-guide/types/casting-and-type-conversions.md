---
title: "轉型和類型轉換 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: "52"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8729677b0c7bee60f0ebeb07439b1c0e71508aa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="c5bbc-102">轉型和類型轉換 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c5bbc-102">Casting and Type Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="c5bbc-103">因為 C# 在編譯時期是靜態類型，所以宣告變數之後，除非該類型可轉換為變數的類型，否則無法再次宣告或用來儲存另一個類型的值。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or used to store values of another type unless that type is convertible to the variable's type.</span></span> <span data-ttu-id="c5bbc-104">例如，沒有從整數到任何任意字串的轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-104">For example, there is no conversion from an integer to any arbitrary string.</span></span> <span data-ttu-id="c5bbc-105">因此，將 `i` 宣告為整數之後，無法對其指派字串 "Hello"，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-105">Therefore, after you declare `i` as an integer, you cannot assign the string "Hello" to it, as is shown in the following code.</span></span>  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 <span data-ttu-id="c5bbc-106">不過，您有時可能需要將值複製至另一種類型的變數或方法參數。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="c5bbc-107">例如，您的整數變數可能需要傳遞給參數類型為 `double` 的方法。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="c5bbc-108">或者，您可能需要將類別變數指派給介面類型的變數。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="c5bbc-109">這些類型的作業稱為「類型轉換」。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="c5bbc-110">在 C# 中，您可以執行下列類型的轉換：</span><span class="sxs-lookup"><span data-stu-id="c5bbc-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
-   <span data-ttu-id="c5bbc-111">**隱含轉換**︰因為轉換為型別安全，所以不需要特殊語法，因此將不會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="c5bbc-112">範例包括從較小到較大整數型別的轉換，以及從衍生類別到基底類別的轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
-   <span data-ttu-id="c5bbc-113">**明確轉換 (轉換)**：明確轉換需要轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="c5bbc-114">如果資訊可能會在轉換時遺失，或轉換因其他原因而失敗，則需要轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="c5bbc-115">一般範例包括將數字轉換為較少有效位數或較小範圍的類型，以及將基底類別執行個體轉換為衍生類別。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
-   <span data-ttu-id="c5bbc-116">**使用者定義的轉換**：使用者定義的轉換是透過特殊方法所執行，而您可以定義特殊方法來啟用沒有基底類別/衍生類別關聯性之自訂類型間的明確和隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="c5bbc-117">如需詳細資訊，請參閱[轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
-   <span data-ttu-id="c5bbc-118">**使用協助程式類別轉換**：若要轉換不相容類型 (例如，整數和 <xref:System.DateTime?displayProperty=nameWithType> 物件，或十六進位字串和位元組陣列)，您可以使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別、<xref:System.Convert?displayProperty=nameWithType> 類別，以及內建數字類型的 `Parse` 方法 (例如，<xref:System.Int32.Parse%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c5bbc-119">如需詳細資訊，請參閱[如何：將位元組陣列轉換為整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)、[如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)和[如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="c5bbc-120">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="c5bbc-120">Implicit Conversions</span></span>  
 <span data-ttu-id="c5bbc-121">針對內建數字類型，如果要儲存的值可以放入變數中，而不需進行截斷或四捨五入，則可以進行隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="c5bbc-122">例如，[long](../../../csharp/language-reference/keywords/long.md) (8 位元組整數) 類型的變數可以儲存 [int](../../../csharp/language-reference/keywords/int.md) (32 位元電腦上的 4 個位元組) 可儲存的任何值。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-122">For example, a variable of type [long](../../../csharp/language-reference/keywords/long.md) (8 byte integer) can store any value that an [int](../../../csharp/language-reference/keywords/int.md) (4 bytes on a 32-bit computer) can store.</span></span> <span data-ttu-id="c5bbc-123">在下列範例中，編譯器會先將右側的值隱含地轉換為類型 `long`，再將它指派給 `bigNum`。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-123">In the following example, the compiler implicitly converts the value on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 <span data-ttu-id="c5bbc-124">如需所有隱含數值轉換的完整清單，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-124">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="c5bbc-125">針對參考型別，一律會執行從某個類別到其任何一個直接或間接基底類別或介面的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-125">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="c5bbc-126">因為衍生類別一律會包含基底類別的所有成員，所以不需要特殊語法。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-126">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="c5bbc-127">明確轉換</span><span class="sxs-lookup"><span data-stu-id="c5bbc-127">Explicit Conversions</span></span>  
 <span data-ttu-id="c5bbc-128">不過，如果進行轉換，而有遺失資訊的風險，則編譯器需要您執行稱為「轉換」的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-128">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="c5bbc-129">轉換是一種方式，可明確通知編譯器，您想要進行轉換並且了解可能發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-129">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="c5bbc-130">若要執行轉換，請在要轉換的值或變數前面的括弧中指定要轉換為的類型。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-130">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="c5bbc-131">下列程式會將 [double](../../../csharp/language-reference/keywords/double.md) 轉型為 [int](../../../csharp/language-reference/keywords/int.md)。沒有轉型，就不會編譯程式。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-131">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/keywords/int.md). The program will not compile without the cast.</span></span>  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 <span data-ttu-id="c5bbc-132">如需允許的明確數值轉換清單，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-132">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="c5bbc-133">針對參考型別，如果您需要將基底類型轉換為衍生類型，則需要明確轉換︰</span><span class="sxs-lookup"><span data-stu-id="c5bbc-133">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 <span data-ttu-id="c5bbc-134">參考型別之間的轉型作業不會變更基礎物件的執行階段類型；它只會變更將用作該物件之參考值的類型。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-134">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="c5bbc-135">如需詳細資訊，請參閱[多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-135">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="c5bbc-136">執行階段的類型轉換例外狀況</span><span class="sxs-lookup"><span data-stu-id="c5bbc-136">Type Conversion Exceptions at Run Time</span></span>  
 <span data-ttu-id="c5bbc-137">在某些參考型別轉換中，編譯器無法判斷轉換是否有效。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-137">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="c5bbc-138">正確編譯的轉型作業可能會在執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-138">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="c5bbc-139">如下列範例所示，在執行階段失敗的型別轉型將導致擲回 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-139">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 <span data-ttu-id="c5bbc-140">C# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 運算子，可讓您先測試相容性，再實際執行轉型。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-140">C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="c5bbc-141">如需詳細資訊，請參閱[如何：使用 as 和 is 運算子進行安全轉型](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="c5bbc-141">For more information, see [How to: Safely Cast by Using as and is Operators](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c5bbc-142">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c5bbc-142">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="c5bbc-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5bbc-143">See Also</span></span>  
 [<span data-ttu-id="c5bbc-144">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c5bbc-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5bbc-145">型別</span><span class="sxs-lookup"><span data-stu-id="c5bbc-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="c5bbc-146">() 運算子</span><span class="sxs-lookup"><span data-stu-id="c5bbc-146">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)  
 [<span data-ttu-id="c5bbc-147">explicit</span><span class="sxs-lookup"><span data-stu-id="c5bbc-147">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="c5bbc-148">implicit</span><span class="sxs-lookup"><span data-stu-id="c5bbc-148">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="c5bbc-149">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="c5bbc-149">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [<span data-ttu-id="c5bbc-150">產生的型別轉換</span><span class="sxs-lookup"><span data-stu-id="c5bbc-150">Generalized Type Conversion</span></span>](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
 [<span data-ttu-id="c5bbc-151">匯出的類型轉換</span><span class="sxs-lookup"><span data-stu-id="c5bbc-151">Exported Type Conversion</span></span>](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
 [<span data-ttu-id="c5bbc-152">如何：將字串轉換為數值</span><span class="sxs-lookup"><span data-stu-id="c5bbc-152">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
