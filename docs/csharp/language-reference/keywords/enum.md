---
title: "enum (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 36
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cf12724ec9e450a2bc237db614f235d7f03a4a7e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="enum-c-reference"></a><span data-ttu-id="2d60c-102">enum (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2d60c-102">enum (C# Reference)</span></span>
<span data-ttu-id="2d60c-103">`enum` 關鍵字用來宣告列舉，是包含一組稱為列舉程式清單之具名常數的不同類型。</span><span class="sxs-lookup"><span data-stu-id="2d60c-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="2d60c-104">通常最好在命名空間內直接定義列舉，使得命名空間中的所有類別可以同樣便利地存取列舉。</span><span class="sxs-lookup"><span data-stu-id="2d60c-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="2d60c-105">不過，列舉也可以巢狀於類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="2d60c-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="2d60c-106">根據預設，第一個列舉程式的值是 0，而每個後續列舉程式的值會遞增 1。</span><span class="sxs-lookup"><span data-stu-id="2d60c-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="2d60c-107">例如，在下列的列舉中， `Sat` 是 `0`， `Sun` 是 `1`， `Mon` 是 `2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="2d60c-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="2d60c-108">列舉程式可使用初始設定式覆寫預設值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2d60c-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="2d60c-109">在這個列舉中，項目的順序會強制從 `1` 開始，而不是 `0`。</span><span class="sxs-lookup"><span data-stu-id="2d60c-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="2d60c-110">不過，建議加入值為 0 的常數。</span><span class="sxs-lookup"><span data-stu-id="2d60c-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="2d60c-111">如需詳細資訊，請參閱[列舉類型](../../../csharp/programming-guide/enumeration-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2d60c-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="2d60c-112">每個列舉類型都具有基礎類型，可以是任何整數類型，但 [char](../../../csharp/language-reference/keywords/char.md) 除外。</span><span class="sxs-lookup"><span data-stu-id="2d60c-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="2d60c-113">預設基礎列舉項目類型是 [int](../../../csharp/language-reference/keywords/int.md)。</span><span class="sxs-lookup"><span data-stu-id="2d60c-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="2d60c-114">若要宣告另一個整數類型的列舉，例如 [byte](../../../csharp/language-reference/keywords/byte.md)，請在識別項後使用冒號，後面接著類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2d60c-114">To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="2d60c-115">列舉已核准的類型是 `byte`、 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、 [short](../../../csharp/language-reference/keywords/short.md)、 [ushort](../../../csharp/language-reference/keywords/ushort.md)、 [int](../../../csharp/language-reference/keywords/int.md)、 [uint](../../../csharp/language-reference/keywords/uint.md)、 [long](../../../csharp/language-reference/keywords/long.md)或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。</span><span class="sxs-lookup"><span data-stu-id="2d60c-115">The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="2d60c-116">類型為 `Days` 的變數可以指派為基礎的類型範圍中的任何值；該值不限於具名常數。</span><span class="sxs-lookup"><span data-stu-id="2d60c-116">A variable of type `Days` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="2d60c-117">`enum E` 的預設值是 `(E)0`運算式所產生的值。</span><span class="sxs-lookup"><span data-stu-id="2d60c-117">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d60c-118">列舉程式名稱中不能包含空白字元。</span><span class="sxs-lookup"><span data-stu-id="2d60c-118">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="2d60c-119">基礎類型指定為每個列舉程式配置的儲存體數量。</span><span class="sxs-lookup"><span data-stu-id="2d60c-119">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="2d60c-120">不過，從 `enum` 類型轉換為整數類型需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="2d60c-120">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="2d60c-121">例如，下列陳述式會指派列舉程式 `Sun` 為 [int](../../../csharp/language-reference/keywords/int.md) 類型的變數，方法是使用轉換從 `enum` 轉換成 `int`。</span><span class="sxs-lookup"><span data-stu-id="2d60c-121">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Days.Sun;  
```  
  
 <span data-ttu-id="2d60c-122">當您將 <xref:System.FlagsAttribute?displayProperty=fullName> 套用至包含可與位元 `OR` 作業結合之項目的列舉時，這個屬性會影響 `enum` 與某些工具一起使用時的行為。</span><span class="sxs-lookup"><span data-stu-id="2d60c-122">When you apply <xref:System.FlagsAttribute?displayProperty=fullName> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="2d60c-123">當您使用如 <xref:System.Console> 類別方法和運算式評估工具等工具時，您可以注意到這些變更。</span><span class="sxs-lookup"><span data-stu-id="2d60c-123">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="2d60c-124">(請參閱第三個範例。)</span><span class="sxs-lookup"><span data-stu-id="2d60c-124">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2d60c-125">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2d60c-125">Robust Programming</span></span>  
 <span data-ttu-id="2d60c-126">如同任何常數，對列舉之個別值的所有參考都會在編譯時期轉換成數值常值。</span><span class="sxs-lookup"><span data-stu-id="2d60c-126">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="2d60c-127">這有可能產生潛在的版本控制問題，如[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="2d60c-127">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="2d60c-128">將額外的值指派給新版本的列舉，或變更新版本中列舉成員的值時，可能會造成相依原始碼的問題。</span><span class="sxs-lookup"><span data-stu-id="2d60c-128">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="2d60c-129">列舉值通常用於 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2d60c-129">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="2d60c-130">如果已將其他項目加入 `enum` 類型中，可能會意外選取 switch 陳述式的預設區段。</span><span class="sxs-lookup"><span data-stu-id="2d60c-130">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="2d60c-131">如果其他開發人員使用您的程式碼，您應該提供詳細指引，說明當新項目加入任何 `enum` 類型中時，其程式碼應該要如何回應。</span><span class="sxs-lookup"><span data-stu-id="2d60c-131">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d60c-132">範例</span><span class="sxs-lookup"><span data-stu-id="2d60c-132">Example</span></span>  
 <span data-ttu-id="2d60c-133">在下列範例中，宣告了 `Days`列舉。</span><span class="sxs-lookup"><span data-stu-id="2d60c-133">In the following example, an enumeration, `Days`, is declared.</span></span> <span data-ttu-id="2d60c-134">兩個列舉程式已明確轉換成整數，並指派給整數變數。</span><span class="sxs-lookup"><span data-stu-id="2d60c-134">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 <span data-ttu-id="2d60c-135">[!code-cs[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2d60c-135">[!code-cs[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d60c-136">範例</span><span class="sxs-lookup"><span data-stu-id="2d60c-136">Example</span></span>  
 <span data-ttu-id="2d60c-137">在下列範例中，基底類型選項會用來宣告 `enum` ，其成員類型是 `long`。</span><span class="sxs-lookup"><span data-stu-id="2d60c-137">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="2d60c-138">請注意，即使列舉的基礎類型是 `long`，列舉成員仍必須使用轉換來明確地轉換成 `long` 類型。</span><span class="sxs-lookup"><span data-stu-id="2d60c-138">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 <span data-ttu-id="2d60c-139">[!code-cs[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2d60c-139">[!code-cs[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d60c-140">範例</span><span class="sxs-lookup"><span data-stu-id="2d60c-140">Example</span></span>  
 <span data-ttu-id="2d60c-141">下列程式碼範例說明如何在 <xref:System.FlagsAttribute?displayProperty=fullName> 宣告上使用 `enum` 屬性與其效果。</span><span class="sxs-lookup"><span data-stu-id="2d60c-141">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=fullName> attribute on an `enum` declaration.</span></span>  
  
 <span data-ttu-id="2d60c-142">[!code-cs[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2d60c-142">[!code-cs[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="2d60c-143">註解</span><span class="sxs-lookup"><span data-stu-id="2d60c-143">Comments</span></span>  
 <span data-ttu-id="2d60c-144">如果您移除 `Flags`，此範例就會顯示下列值︰</span><span class="sxs-lookup"><span data-stu-id="2d60c-144">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="2d60c-145">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2d60c-145">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d60c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d60c-146">See Also</span></span>  
 <span data-ttu-id="2d60c-147">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2d60c-147">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2d60c-148">[列舉類型](../../../csharp/programming-guide/enumeration-types.md) </span><span class="sxs-lookup"><span data-stu-id="2d60c-148">[Enumeration Types](../../../csharp/programming-guide/enumeration-types.md) </span></span>  
 <span data-ttu-id="2d60c-149">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="2d60c-149">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="2d60c-150">[整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="2d60c-150">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="2d60c-151">[內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="2d60c-151">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="2d60c-152">[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="2d60c-152">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="2d60c-153">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="2d60c-153">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

