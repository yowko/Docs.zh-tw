---
title: "enum (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36d33387dda68270e0490eaa6c792f95d058651e
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="enum-c-reference"></a><span data-ttu-id="d4c64-102">enum (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d4c64-102">enum (C# Reference)</span></span>
<span data-ttu-id="d4c64-103">`enum` 關鍵字用來宣告列舉，是包含一組稱為列舉程式清單之具名常數的不同類型。</span><span class="sxs-lookup"><span data-stu-id="d4c64-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="d4c64-104">通常最好在命名空間內直接定義列舉，使得命名空間中的所有類別可以同樣便利地存取列舉。</span><span class="sxs-lookup"><span data-stu-id="d4c64-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="d4c64-105">不過，列舉也可以巢狀於類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="d4c64-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="d4c64-106">根據預設，第一個列舉程式的值是 0，而每個後續列舉程式的值會遞增 1。</span><span class="sxs-lookup"><span data-stu-id="d4c64-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="d4c64-107">例如，在下列的列舉中， `Sat` 是 `0`， `Sun` 是 `1`， `Mon` 是 `2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d4c64-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="d4c64-108">列舉程式可使用初始設定式覆寫預設值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d4c64-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="d4c64-109">在這個列舉中，項目的順序會強制從 `1` 開始，而不是 `0`。</span><span class="sxs-lookup"><span data-stu-id="d4c64-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="d4c64-110">不過，建議加入值為 0 的常數。</span><span class="sxs-lookup"><span data-stu-id="d4c64-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="d4c64-111">如需詳細資訊，請參閱[列舉類型](../../../csharp/programming-guide/enumeration-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c64-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="d4c64-112">每個列舉類型都具有基礎類型，可以是任何整數類型，但 [char](../../../csharp/language-reference/keywords/char.md) 除外。</span><span class="sxs-lookup"><span data-stu-id="d4c64-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="d4c64-113">預設基礎列舉項目類型是 [int](../../../csharp/language-reference/keywords/int.md)。若要宣告另一個整數類型的列舉，例如 [byte](../../../csharp/language-reference/keywords/byte.md)，請在識別項後使用冒號，後面接著類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d4c64-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md). To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="d4c64-114">列舉的核准類型有 [byte](../../../csharp/language-reference/keywords/byte.md)、[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c64-114">The approved types for an enum are [byte](../../../csharp/language-reference/keywords/byte.md), [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="d4c64-115">類型為 `Day` 的變數可以指派為基礎的類型範圍中的任何值；該值不限於具名常數。</span><span class="sxs-lookup"><span data-stu-id="d4c64-115">A variable of type `Day` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="d4c64-116">`enum E` 的預設值是 `(E)0`運算式所產生的值。</span><span class="sxs-lookup"><span data-stu-id="d4c64-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4c64-117">列舉程式名稱中不能包含空白字元。</span><span class="sxs-lookup"><span data-stu-id="d4c64-117">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="d4c64-118">基礎類型指定為每個列舉程式配置的儲存體數量。</span><span class="sxs-lookup"><span data-stu-id="d4c64-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="d4c64-119">不過，從 `enum` 類型轉換為整數類型需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="d4c64-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="d4c64-120">例如，下列陳述式會指派列舉程式 `Sun` 為 [int](../../../csharp/language-reference/keywords/int.md) 類型的變數，方法是使用轉換從 `enum` 轉換成 `int`。</span><span class="sxs-lookup"><span data-stu-id="d4c64-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Day.Sun;  
```  
  
 <span data-ttu-id="d4c64-121">當您將 <xref:System.FlagsAttribute?displayProperty=nameWithType> 套用至包含可與位元 `OR` 作業結合之項目的列舉時，這個屬性會影響 `enum` 與某些工具一起使用時的行為。</span><span class="sxs-lookup"><span data-stu-id="d4c64-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="d4c64-122">當您使用如 <xref:System.Console> 類別方法和運算式評估工具等工具時，您可以注意到這些變更。</span><span class="sxs-lookup"><span data-stu-id="d4c64-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="d4c64-123">(請參閱第三個範例。)</span><span class="sxs-lookup"><span data-stu-id="d4c64-123">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d4c64-124">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d4c64-124">Robust Programming</span></span>  
 <span data-ttu-id="d4c64-125">如同任何常數，對列舉之個別值的所有參考都會在編譯時期轉換成數值常值。</span><span class="sxs-lookup"><span data-stu-id="d4c64-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="d4c64-126">這有可能產生潛在的版本控制問題，如[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="d4c64-126">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="d4c64-127">將額外的值指派給新版本的列舉，或變更新版本中列舉成員的值時，可能會造成相依原始碼的問題。</span><span class="sxs-lookup"><span data-stu-id="d4c64-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="d4c64-128">列舉值通常用於 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c64-128">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="d4c64-129">如果已將其他項目加入 `enum` 類型中，可能會意外選取 switch 陳述式的預設區段。</span><span class="sxs-lookup"><span data-stu-id="d4c64-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="d4c64-130">如果其他開發人員使用您的程式碼，您應該提供詳細指引，說明當新項目加入任何 `enum` 類型中時，其程式碼應該要如何回應。</span><span class="sxs-lookup"><span data-stu-id="d4c64-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c64-131">範例</span><span class="sxs-lookup"><span data-stu-id="d4c64-131">Example</span></span>  
 <span data-ttu-id="d4c64-132">在下列範例中，宣告了 `Day`列舉。</span><span class="sxs-lookup"><span data-stu-id="d4c64-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="d4c64-133">兩個列舉程式已明確轉換成整數，並指派給整數變數。</span><span class="sxs-lookup"><span data-stu-id="d4c64-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d4c64-134">範例</span><span class="sxs-lookup"><span data-stu-id="d4c64-134">Example</span></span>  
 <span data-ttu-id="d4c64-135">在下列範例中，基底類型選項會用來宣告 `enum` ，其成員類型是 `long`。</span><span class="sxs-lookup"><span data-stu-id="d4c64-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="d4c64-136">請注意，即使列舉的基礎類型是 `long`，列舉成員仍必須使用轉換來明確地轉換成 `long` 類型。</span><span class="sxs-lookup"><span data-stu-id="d4c64-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="d4c64-137">範例</span><span class="sxs-lookup"><span data-stu-id="d4c64-137">Example</span></span>  
 <span data-ttu-id="d4c64-138">下列程式碼範例說明如何在 <xref:System.FlagsAttribute?displayProperty=nameWithType> 宣告上使用 `enum` 屬性與其效果。</span><span class="sxs-lookup"><span data-stu-id="d4c64-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a><span data-ttu-id="d4c64-139">註解</span><span class="sxs-lookup"><span data-stu-id="d4c64-139">Comments</span></span>  
 <span data-ttu-id="d4c64-140">如果您移除 `Flags`，此範例就會顯示下列值︰</span><span class="sxs-lookup"><span data-stu-id="d4c64-140">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="d4c64-141">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d4c64-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4c64-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4c64-142">See Also</span></span>  
 [<span data-ttu-id="d4c64-143">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d4c64-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d4c64-144">列舉型別</span><span class="sxs-lookup"><span data-stu-id="d4c64-144">Enumeration Types</span></span>](../../../csharp/programming-guide/enumeration-types.md)  
 [<span data-ttu-id="d4c64-145">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4c64-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d4c64-146">整數型別表</span><span class="sxs-lookup"><span data-stu-id="d4c64-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="d4c64-147">內建型別表</span><span class="sxs-lookup"><span data-stu-id="d4c64-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="d4c64-148">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="d4c64-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d4c64-149">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="d4c64-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="d4c64-150">列舉命名慣例</span><span class="sxs-lookup"><span data-stu-id="d4c64-150">Enum Naming Conventions</span></span>](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)
