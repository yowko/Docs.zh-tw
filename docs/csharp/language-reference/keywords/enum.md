---
title: enum 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 57043963640f3c384b1e1a9aa7aeb65114689e9f
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569527"
---
# <a name="enum-c-reference"></a><span data-ttu-id="a8593-102">enum (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a8593-102">enum (C# Reference)</span></span>

<span data-ttu-id="a8593-103">`enum` 關鍵字用來宣告列舉，是包含一組稱為列舉程式清單之具名常數的不同類型。</span><span class="sxs-lookup"><span data-stu-id="a8593-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="a8593-104">通常最好在命名空間內直接定義列舉，使得命名空間中的所有類別可以同樣便利地存取列舉。</span><span class="sxs-lookup"><span data-stu-id="a8593-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="a8593-105">不過，列舉也可以巢狀於類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="a8593-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="a8593-106">根據預設，第一個列舉程式的值是 0，而每個後續列舉程式的值會遞增 1。</span><span class="sxs-lookup"><span data-stu-id="a8593-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="a8593-107">例如，在下列的列舉中， `Sat` 是 `0`， `Sun` 是 `1`， `Mon` 是 `2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a8593-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="a8593-108">列舉程式可使用初始設定式覆寫預設值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a8593-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="a8593-109">在這個列舉中，項目的順序會強制從 `1` 開始，而不是 `0`。</span><span class="sxs-lookup"><span data-stu-id="a8593-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="a8593-110">不過，建議加入值為 0 的常數。</span><span class="sxs-lookup"><span data-stu-id="a8593-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="a8593-111">如需詳細資訊，請參閱[列舉類型](../../programming-guide/enumeration-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a8593-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="a8593-112">每個列舉型別都具有基礎型別，它可以是任何[整數數字型別](../builtin-types/integral-numeric-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a8593-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="a8593-113">[Char](char.md) 型別不能是列舉的基礎型別。</span><span class="sxs-lookup"><span data-stu-id="a8593-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="a8593-114">預設基礎列舉項目類型是 [int](../builtin-types/integral-numeric-types.md)。若要宣告另一個整數類型的列舉，例如 [byte](../builtin-types/integral-numeric-types.md)，請在識別項後使用冒號，後面接著類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a8593-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="a8593-115">型別為列舉的變數可以指派為底層類型範圍中的任何值；該值不限於具名常數。</span><span class="sxs-lookup"><span data-stu-id="a8593-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="a8593-116">`enum E` 的預設值是 `(E)0`運算式所產生的值。</span><span class="sxs-lookup"><span data-stu-id="a8593-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="a8593-117">列舉程式名稱中不能包含空白字元。</span><span class="sxs-lookup"><span data-stu-id="a8593-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="a8593-118">基礎類型指定為每個列舉程式配置的儲存體數量。</span><span class="sxs-lookup"><span data-stu-id="a8593-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="a8593-119">不過，從 `enum` 類型轉換為整數類型需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="a8593-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="a8593-120">例如，下列陳述式會指派列舉程式 `Sun` 為 [int](../builtin-types/integral-numeric-types.md) 類型的變數，方法是使用轉換從 `enum` 轉換成 `int`。</span><span class="sxs-lookup"><span data-stu-id="a8593-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="a8593-121">當您將 <xref:System.FlagsAttribute?displayProperty=nameWithType> 套用至包含可與位元 `OR` 作業結合之項目的列舉時，這個屬性會影響 `enum` 與某些工具一起使用時的行為。</span><span class="sxs-lookup"><span data-stu-id="a8593-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="a8593-122">當您使用如 <xref:System.Console> 類別方法和運算式評估工具等工具時，您可以注意到這些變更。</span><span class="sxs-lookup"><span data-stu-id="a8593-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="a8593-123">(請參閱第三個範例。)</span><span class="sxs-lookup"><span data-stu-id="a8593-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="a8593-124">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="a8593-124">Robust programming</span></span>

<span data-ttu-id="a8593-125">如同任何常數，對列舉之個別值的所有參考都會在編譯時期轉換成數值常值。</span><span class="sxs-lookup"><span data-stu-id="a8593-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="a8593-126">這有可能產生潛在的版本控制問題，如[常數](../../programming-guide/classes-and-structs/constants.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="a8593-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="a8593-127">將額外的值指派給新版本的列舉，或變更新版本中列舉成員的值時，可能會造成相依原始碼的問題。</span><span class="sxs-lookup"><span data-stu-id="a8593-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="a8593-128">列舉值通常用於 [switch](switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a8593-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="a8593-129">如果已將其他項目加入 `enum` 類型中，可能會意外選取 switch 陳述式的預設區段。</span><span class="sxs-lookup"><span data-stu-id="a8593-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="a8593-130">如果其他開發人員使用您的程式碼，您應該提供詳細指引，說明當新項目加入任何 `enum` 類型中時，其程式碼應該要如何回應。</span><span class="sxs-lookup"><span data-stu-id="a8593-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="a8593-131">範例</span><span class="sxs-lookup"><span data-stu-id="a8593-131">Example</span></span>

<span data-ttu-id="a8593-132">在下列範例中，宣告了 `Day`列舉。</span><span class="sxs-lookup"><span data-stu-id="a8593-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="a8593-133">兩個列舉程式已明確轉換成整數，並指派給整數變數。</span><span class="sxs-lookup"><span data-stu-id="a8593-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="a8593-134">範例</span><span class="sxs-lookup"><span data-stu-id="a8593-134">Example</span></span>

<span data-ttu-id="a8593-135">在下列範例中，基底類型選項會用來宣告 `enum` ，其成員類型是 `long`。</span><span class="sxs-lookup"><span data-stu-id="a8593-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="a8593-136">請注意，即使列舉的基礎類型是 `long`，列舉成員仍必須使用轉換來明確地轉換成 `long` 類型。</span><span class="sxs-lookup"><span data-stu-id="a8593-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="a8593-137">範例</span><span class="sxs-lookup"><span data-stu-id="a8593-137">Example</span></span>

<span data-ttu-id="a8593-138">下列程式碼範例說明如何在 <xref:System.FlagsAttribute?displayProperty=nameWithType> 宣告上使用 `enum` 屬性與其效果。</span><span class="sxs-lookup"><span data-stu-id="a8593-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="a8593-139">註解</span><span class="sxs-lookup"><span data-stu-id="a8593-139">Comments</span></span>

<span data-ttu-id="a8593-140">如果您移除 `Flags`，此範例就會顯示下列值︰</span><span class="sxs-lookup"><span data-stu-id="a8593-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="a8593-141">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a8593-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a8593-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8593-142">See also</span></span>

- [<span data-ttu-id="a8593-143">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a8593-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a8593-144">列舉型別</span><span class="sxs-lookup"><span data-stu-id="a8593-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="a8593-145">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a8593-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a8593-146">整數型別</span><span class="sxs-lookup"><span data-stu-id="a8593-146">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="a8593-147">內建型別表</span><span class="sxs-lookup"><span data-stu-id="a8593-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="a8593-148">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="a8593-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="a8593-149">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="a8593-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="a8593-150">列舉命名慣例</span><span class="sxs-lookup"><span data-stu-id="a8593-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
