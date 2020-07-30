---
title: 轉型和類型轉換 - C# 程式設計指南
description: 瞭解轉換和類型轉換，例如隱含、明確（轉換）和使用者定義的轉換。
ms.date: 07/06/2020
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 040b5679b1e6666a7f0308e5990781a2ef86c530
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381953"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="e09e8-103">轉型和類型轉換 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="e09e8-103">Casting and type conversions (C# Programming Guide)</span></span>

<span data-ttu-id="e09e8-104">因為 C# 在編譯時期是靜態型別，所以宣告變數之後，除非該型別隱含轉換為變數的型別，否則無法再次宣告或指派另一個型別的值。</span><span class="sxs-lookup"><span data-stu-id="e09e8-104">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or assigned a value of another type unless that type is implicitly convertible to the variable's type.</span></span> <span data-ttu-id="e09e8-105">例如，`string` 無法隱含轉換為 `int`。</span><span class="sxs-lookup"><span data-stu-id="e09e8-105">For example, the `string` cannot be implicitly converted to `int`.</span></span> <span data-ttu-id="e09e8-106">因此，在您宣告 `i` 為 `int` 之後，您便無法將字串 "Hello" 指派給它，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e09e8-106">Therefore, after you declare `i` as an `int`, you cannot assign the string "Hello" to it, as the following code shows:</span></span>

```csharp
int i;

// error CS0029: Cannot implicitly convert type 'string' to 'int'
i = "Hello";
```

<span data-ttu-id="e09e8-107">不過，您有時可能需要將值複製至另一種類型的變數或方法參數。</span><span class="sxs-lookup"><span data-stu-id="e09e8-107">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="e09e8-108">例如，您的整數變數可能需要傳遞給參數類型為 `double` 的方法。</span><span class="sxs-lookup"><span data-stu-id="e09e8-108">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="e09e8-109">或者，您可能需要將類別變數指派給介面類型的變數。</span><span class="sxs-lookup"><span data-stu-id="e09e8-109">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="e09e8-110">這些類型的作業稱為「類型轉換」\*\*。</span><span class="sxs-lookup"><span data-stu-id="e09e8-110">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="e09e8-111">在 C# 中，您可以執行下列類型的轉換：</span><span class="sxs-lookup"><span data-stu-id="e09e8-111">In C#, you can perform the following kinds of conversions:</span></span>

- <span data-ttu-id="e09e8-112">**隱含轉換**：不需要特殊語法，因為轉換一律會成功，而且不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="e09e8-112">**Implicit conversions**: No special syntax is required because the conversion always succeeds and no data will be lost.</span></span> <span data-ttu-id="e09e8-113">範例包括從較小到較大整數型別的轉換，以及從衍生類別到基底類別的轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-113">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>

- <span data-ttu-id="e09e8-114">**明確轉換（轉換）**：明確轉換需要[cast 運算式](../../language-reference/operators/type-testing-and-cast.md#cast-expression)。</span><span class="sxs-lookup"><span data-stu-id="e09e8-114">**Explicit conversions (casts)**: Explicit conversions require a [cast expression](../../language-reference/operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="e09e8-115">如果資訊可能會在轉換時遺失，或轉換因其他原因而失敗，則需要轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-115">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span> <span data-ttu-id="e09e8-116">一般範例包括將數字轉換為較少有效位數或較小範圍的類型，以及將基底類別執行個體轉換為衍生類別。</span><span class="sxs-lookup"><span data-stu-id="e09e8-116">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>

- <span data-ttu-id="e09e8-117">**使用者定義的轉換**：使用者定義的轉換是透過特殊方法所執行，而您可以定義特殊方法來啟用沒有基底類別/衍生類別關聯性之自訂類型間的明確和隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-117">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="e09e8-118">如需詳細資訊，請參閱[使用者定義轉換運算子](../../language-reference/operators/user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="e09e8-118">For more information, see [User-defined conversion operators](../../language-reference/operators/user-defined-conversion-operators.md).</span></span>

- <span data-ttu-id="e09e8-119">**使用協助程式類別轉換**：若要轉換不相容類型 (例如，整數和 <xref:System.DateTime?displayProperty=nameWithType> 物件，或十六進位字串和位元組陣列)，您可以使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別、<xref:System.Convert?displayProperty=nameWithType> 類別，以及內建數字類型的 `Parse` 方法 (例如，<xref:System.Int32.Parse%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="e09e8-119">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e09e8-120">如需詳細資訊，請參閱[如何將位元組陣列轉換成](./how-to-convert-a-byte-array-to-an-int.md)整數、[如何將字串轉換成數位](./how-to-convert-a-string-to-a-number.md)，以及[如何在十六進位字串和數位類型之間進行轉換](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e09e8-120">For more information, see [How to convert a byte array to an int](./how-to-convert-a-byte-array-to-an-int.md), [How to convert a string to a number](./how-to-convert-a-string-to-a-number.md), and [How to convert between hexadecimal strings and numeric types](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>

## <a name="implicit-conversions"></a><span data-ttu-id="e09e8-121">隱含的轉換</span><span class="sxs-lookup"><span data-stu-id="e09e8-121">Implicit conversions</span></span>

<span data-ttu-id="e09e8-122">針對內建數字類型，如果要儲存的值可以放入變數中，而不需進行截斷或四捨五入，則可以進行隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-122">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="e09e8-123">針對整數型別，這表示來源型別的範圍是目標型別範圍的適當子集。</span><span class="sxs-lookup"><span data-stu-id="e09e8-123">For integral types, this means the range of the source type is a proper subset of the range for the target type.</span></span> <span data-ttu-id="e09e8-124">例如，型別為 [long](../../language-reference/builtin-types/integral-numeric-types.md) 的變數 (64 位元整數) 可儲存任何 [int](../../language-reference/builtin-types/integral-numeric-types.md) (32 位元整數) 能儲存的值。</span><span class="sxs-lookup"><span data-stu-id="e09e8-124">For example, a variable of type [long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bit integer) can store any value that an [int](../../language-reference/builtin-types/integral-numeric-types.md) (32-bit integer) can store.</span></span> <span data-ttu-id="e09e8-125">在下列範例中，編譯器會將位於右側的 `num` 值隱含轉換為 `long` 型別，再將它指派給 `bigNum`。</span><span class="sxs-lookup"><span data-stu-id="e09e8-125">In the following example, the compiler implicitly converts the value of `num` on the right to a type `long` before assigning it to `bigNum`.</span></span>

[!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]

<span data-ttu-id="e09e8-126">如需所有隱含數值轉換的完整清單，請參閱[內建數值轉換](../../language-reference/builtin-types/numeric-conversions.md)一文的[隱含數值轉換](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="e09e8-126">For a complete list of all implicit numeric conversions, see the [Implicit numeric conversions](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) section of the [Built-in numeric conversions](../../language-reference/builtin-types/numeric-conversions.md) article.</span></span>

<span data-ttu-id="e09e8-127">針對參考型別，一律會執行從某個類別到其任何一個直接或間接基底類別或介面的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-127">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="e09e8-128">因為衍生類別一律會包含基底類別的所有成員，所以不需要特殊語法。</span><span class="sxs-lookup"><span data-stu-id="e09e8-128">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>

```csharp
Derived d = new Derived();

// Always OK.
Base b = d;
```

## <a name="explicit-conversions"></a><span data-ttu-id="e09e8-129">明確轉換</span><span class="sxs-lookup"><span data-stu-id="e09e8-129">Explicit conversions</span></span>

<span data-ttu-id="e09e8-130">不過，如果進行轉換，而有遺失資訊的風險，則編譯器需要您執行稱為「轉換」\*\* 的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-130">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="e09e8-131">轉換是一種方法，可明確通知編譯器您想要進行轉換，而且您知道可能會遺失資料，或轉換可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="e09e8-131">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur, or the cast may fail at runtime.</span></span> <span data-ttu-id="e09e8-132">若要執行轉換，請在要轉換的值或變數前面的括弧中指定要轉換為的類型。</span><span class="sxs-lookup"><span data-stu-id="e09e8-132">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="e09e8-133">下列程式會將[double](../../language-reference/builtin-types/floating-point-numeric-types.md)轉換成[int](../../language-reference/builtin-types/integral-numeric-types.md)。程式不會進行編譯，而不會進行轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-133">The following program casts a [double](../../language-reference/builtin-types/floating-point-numeric-types.md) to an [int](../../language-reference/builtin-types/integral-numeric-types.md). The program will not compile without the cast.</span></span>

[!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]

<span data-ttu-id="e09e8-134">如需支援的明確數值轉換的完整清單，請參閱[內建數值轉換](../../language-reference/builtin-types/numeric-conversions.md)一文的[明確數值轉換](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions)一節。</span><span class="sxs-lookup"><span data-stu-id="e09e8-134">For a complete list of supported explicit numeric conversions, see the [Explicit numeric conversions](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) section of the [Built-in numeric conversions](../../language-reference/builtin-types/numeric-conversions.md) article.</span></span>

<span data-ttu-id="e09e8-135">針對參考型別，如果您需要將基底類型轉換為衍生類型，則需要明確轉換︰</span><span class="sxs-lookup"><span data-stu-id="e09e8-135">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>

```csharp
// Create a new derived type.
Giraffe g = new Giraffe();

// Implicit conversion to base type is safe.
Animal a = g;

// Explicit conversion is required to cast back
// to derived type. Note: This will compile but will
// throw an exception at run time if the right-side
// object is not in fact a Giraffe.
Giraffe g2 = (Giraffe)a;
```

<span data-ttu-id="e09e8-136">參考型別之間的轉型作業不會變更基礎物件的執行階段類型；它只會變更將用作該物件之參考值的類型。</span><span class="sxs-lookup"><span data-stu-id="e09e8-136">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="e09e8-137">如需詳細資訊，請參閱[多型](../classes-and-structs/polymorphism.md)。</span><span class="sxs-lookup"><span data-stu-id="e09e8-137">For more information, see [Polymorphism](../classes-and-structs/polymorphism.md).</span></span>

## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="e09e8-138">執行階段的類型轉換例外狀況</span><span class="sxs-lookup"><span data-stu-id="e09e8-138">Type conversion exceptions at run time</span></span>

<span data-ttu-id="e09e8-139">在某些參考型別轉換中，編譯器無法判斷轉換是否有效。</span><span class="sxs-lookup"><span data-stu-id="e09e8-139">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="e09e8-140">正確編譯的轉型作業可能會在執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="e09e8-140">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="e09e8-141">如下列範例所示，在執行階段失敗的型別轉型將導致擲回 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="e09e8-141">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>

[!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]

<span data-ttu-id="e09e8-142">`Test`方法具有 `Animal` 參數，因此將引數明確轉換 `a` 為會造成 `Reptile` 危險的假設。</span><span class="sxs-lookup"><span data-stu-id="e09e8-142">The `Test` method has an `Animal` parameter, thus explicitly casting the argument `a` to a `Reptile` makes a dangerous assumption.</span></span> <span data-ttu-id="e09e8-143">不進行假設，而是檢查類型是比較安全的作法。</span><span class="sxs-lookup"><span data-stu-id="e09e8-143">It is safer to not make assumptions, but rather check the type.</span></span> <span data-ttu-id="e09e8-144">C# 提供 [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) 運算子，可讓您先測試相容性，再實際執行轉換。</span><span class="sxs-lookup"><span data-stu-id="e09e8-144">C# provides the [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) operator to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="e09e8-145">如需詳細資訊，請參閱[如何使用模式比對來安全地轉換和 as 和 is 運算子](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="e09e8-145">For more information, see [How to safely cast using pattern matching and the as and is operators](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e09e8-146">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e09e8-146">C# language specification</span></span>

<span data-ttu-id="e09e8-147">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[轉換](~/_csharplang/spec/conversions.md)一節。</span><span class="sxs-lookup"><span data-stu-id="e09e8-147">For more information, see the [Conversions](~/_csharplang/spec/conversions.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e09e8-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e09e8-148">See also</span></span>

- [<span data-ttu-id="e09e8-149">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e09e8-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e09e8-150">類型</span><span class="sxs-lookup"><span data-stu-id="e09e8-150">Types</span></span>](./index.md)
- [<span data-ttu-id="e09e8-151">轉換運算式</span><span class="sxs-lookup"><span data-stu-id="e09e8-151">Cast expression</span></span>](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [<span data-ttu-id="e09e8-152">使用者定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="e09e8-152">User-defined conversion operators</span></span>](../../language-reference/operators/user-defined-conversion-operators.md)
- <span data-ttu-id="e09e8-153">[產生的類型轉換](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e09e8-153">[Generalized Type Conversion](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span></span>
- [<span data-ttu-id="e09e8-154">如何將字串轉換為數值</span><span class="sxs-lookup"><span data-stu-id="e09e8-154">How to convert a string to a number</span></span>](./how-to-convert-a-string-to-a-number.md)
