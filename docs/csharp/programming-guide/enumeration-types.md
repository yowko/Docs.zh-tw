---
title: "列舉類型 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
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
ms.openlocfilehash: 677de7c6e0c0f72b600ce8ee5a8bad265725f6d3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="d22da-102">列舉類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d22da-102">Enumeration Types (C# Programming Guide)</span></span>
<span data-ttu-id="d22da-103">列舉類型 (也稱為列舉 (enumeration) 或列舉 (enum)) 提供有效率的方式，來定義一組可指派給變數的具名整數常數。</span><span class="sxs-lookup"><span data-stu-id="d22da-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="d22da-104">例如，假設您必須定義一個變數，其值代表星期幾。</span><span class="sxs-lookup"><span data-stu-id="d22da-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="d22da-105">該變數只會儲存七個有意義的值。</span><span class="sxs-lookup"><span data-stu-id="d22da-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="d22da-106">若要定義這些值，您可以使用以 [enum](../../csharp/language-reference/keywords/enum.md) 關鍵字宣告的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="d22da-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>  
  
 <span data-ttu-id="d22da-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span></span>  
  
 <span data-ttu-id="d22da-108">根據預設，每個項目在列舉中的基礎類型是 [int](../../csharp/language-reference/keywords/int.md)。</span><span class="sxs-lookup"><span data-stu-id="d22da-108">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="d22da-109">您可以使用冒號指定其他的整數數值類型，如上例所示。</span><span class="sxs-lookup"><span data-stu-id="d22da-109">You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="d22da-110">如需可能類型的完整清單，請參閱 [enum (C# 參考)](../../csharp/language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="d22da-110">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="d22da-111">您可以透過轉換為基礎類型來驗證基礎數字值，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="d22da-111">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>  
  
```csharp  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 <span data-ttu-id="d22da-112">使用列舉而不使用數值類型的優點如下︰</span><span class="sxs-lookup"><span data-stu-id="d22da-112">The following are advantages of using an enum instead of a numeric type:</span></span>  
  
-   <span data-ttu-id="d22da-113">清楚指定用戶端程式碼的哪些值對變數有效。</span><span class="sxs-lookup"><span data-stu-id="d22da-113">You clearly specify for client code which values are valid for the variable.</span></span>  
  
-   <span data-ttu-id="d22da-114">在 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 中，IntelliSense 會列出已定義的值。</span><span class="sxs-lookup"><span data-stu-id="d22da-114">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense lists the defined values.</span></span>  
  
 <span data-ttu-id="d22da-115">當您不為列舉程式清單中的項目指定值時，值會自動遞增 1。</span><span class="sxs-lookup"><span data-stu-id="d22da-115">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="d22da-116">在上例中，`Days.Sunday` 的值為 0，`Days.Monday` 的值為 1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d22da-116">In the previous example, `Days.Sunday` has a value of 0, `Days.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="d22da-117">當您建立新的 `Days` 物件時，如未明確指定其值，則它會有預設值 `Days.Sunday` (0)。</span><span class="sxs-lookup"><span data-stu-id="d22da-117">When you create a new `Days` object, it will have a default value of `Days.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="d22da-118">當您建立列舉時，請選取最符合邏輯的預設值，並指定其值為零。</span><span class="sxs-lookup"><span data-stu-id="d22da-118">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="d22da-119">這會造成所有的列舉都是預設值，如果它們在建立時未明確指派值。</span><span class="sxs-lookup"><span data-stu-id="d22da-119">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>  
  
 <span data-ttu-id="d22da-120">如果 `meetingDay` 變數的類型是 `Days`，則 (不需要明確轉換) 您只能將 `Days` 所定義的其中一個值指派給它。</span><span class="sxs-lookup"><span data-stu-id="d22da-120">If the variable `meetingDay` is of type `Days`, then (without an explicit cast) you can only assign it one of the values defined by `Days`.</span></span> <span data-ttu-id="d22da-121">如果會議日期變更，您可以指派新值，從 `Days` 變成 `meetingDay`：</span><span class="sxs-lookup"><span data-stu-id="d22da-121">And if the meeting day changes, you can assign a new value from `Days` to `meetingDay`:</span></span>  
  
 <span data-ttu-id="d22da-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d22da-123">您可以將任何任意整數值指派給 `meetingDay`。</span><span class="sxs-lookup"><span data-stu-id="d22da-123">It is possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="d22da-124">例如，這行程式碼不會產生錯誤︰`meetingDay = (Days) 42`。</span><span class="sxs-lookup"><span data-stu-id="d22da-124">For example, this line of code does not produce an error: `meetingDay = (Days) 42`.</span></span> <span data-ttu-id="d22da-125">不過，您不應該這麼做，因為隱含預期列舉變數只保留列舉定義的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="d22da-125">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="d22da-126">將任意值指派給列舉類型的變數會導致高風險錯誤。</span><span class="sxs-lookup"><span data-stu-id="d22da-126">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>  
  
 <span data-ttu-id="d22da-127">您可以指派任何值給列舉類型的列舉程式清單中的項目，也可以使用計算的值︰</span><span class="sxs-lookup"><span data-stu-id="d22da-127">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>  
  
 <span data-ttu-id="d22da-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span></span>  
  
## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="d22da-129">作為位元旗標的列舉類型</span><span class="sxs-lookup"><span data-stu-id="d22da-129">Enumeration Types as Bit Flags</span></span>  
 <span data-ttu-id="d22da-130">您可以使用列舉類型來定義位元旗標，讓列舉類型的執行個體儲存在列舉程式清單中所定義的任何值組。</span><span class="sxs-lookup"><span data-stu-id="d22da-130">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="d22da-131">(當然，某些組合在您的程式碼中可能無意義或不被允許。)</span><span class="sxs-lookup"><span data-stu-id="d22da-131">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>  
  
 <span data-ttu-id="d22da-132">您可透過套用 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性和適當定義值來建立位元旗標列舉，以對它們執行 `AND`、`OR`、`NOT` 和 `XOR` 位元運算。</span><span class="sxs-lookup"><span data-stu-id="d22da-132">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=fullName> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="d22da-133">在位元旗標列舉中包含值為零的具名常數，表示「未設定任何旗標」。</span><span class="sxs-lookup"><span data-stu-id="d22da-133">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="d22da-134">如果不表示「未設定任何旗標」，請勿指定旗標值為零。</span><span class="sxs-lookup"><span data-stu-id="d22da-134">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>  
  
 <span data-ttu-id="d22da-135">在下例中，定義了另一個版本的 `Days` 列舉，名為 `Days2`。</span><span class="sxs-lookup"><span data-stu-id="d22da-135">In the following example, another version of the `Days` enum, which is named `Days2`, is defined.</span></span> <span data-ttu-id="d22da-136">`Days2` 具有 `Flags` 屬性，且每個值已指派下一個大於 2 的乘冪。</span><span class="sxs-lookup"><span data-stu-id="d22da-136">`Days2` has the `Flags` attribute and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="d22da-137">這可讓您建立其值為 `Days2.Tuesday` 和 `Days2.Thursday` 的 `Days2` 變數。</span><span class="sxs-lookup"><span data-stu-id="d22da-137">This enables you to create a `Days2` variable whose value is `Days2.Tuesday` and `Days2.Thursday`.</span></span>  
  
 <span data-ttu-id="d22da-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span></span>  
  
 <span data-ttu-id="d22da-139">若要對列舉設定旗標，請使用位元 `OR` 運算子，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="d22da-139">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>  
  
 <span data-ttu-id="d22da-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span></span>  
  
 <span data-ttu-id="d22da-141">若要判斷是否已設定特定的旗標，請使用位元 `AND` 作業，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="d22da-141">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>  
  
 <span data-ttu-id="d22da-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span></span>  
  
 <span data-ttu-id="d22da-143">如需在定義含有 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性之列舉類型時需考量事項的詳細資訊，請參閱 <xref:System.Enum?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="d22da-143">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=fullName> attribute, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="d22da-144">使用 System.Enum 方法來探索和操作列舉值</span><span class="sxs-lookup"><span data-stu-id="d22da-144">Using the System.Enum Methods to Discover and Manipulate Enum Values</span></span>  
 <span data-ttu-id="d22da-145">所有列舉都是 <xref:System.Enum?displayProperty=fullName> 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d22da-145">All enums are instances of the <xref:System.Enum?displayProperty=fullName> type.</span></span> <span data-ttu-id="d22da-146">您不能從 <xref:System.Enum?displayProperty=fullName> 衍生新的類別，但可以使用其方法來探索相關資訊以及操作列舉執行個體中的值。</span><span class="sxs-lookup"><span data-stu-id="d22da-146">You cannot derive new classes from <xref:System.Enum?displayProperty=fullName>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>  
  
 <span data-ttu-id="d22da-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="d22da-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span></span>  
  
 <span data-ttu-id="d22da-148">如需詳細資訊，請參閱<xref:System.Enum?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="d22da-148">For more information, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="d22da-149">您也可以使用擴充方法，為列舉建立新的方法。</span><span class="sxs-lookup"><span data-stu-id="d22da-149">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="d22da-150">如需詳細資訊，請參閱[如何：建立列舉的新方法 ](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="d22da-150">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="d22da-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d22da-151">See Also</span></span>  
 <span data-ttu-id="d22da-152"><xref:System.Enum?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d22da-152"><xref:System.Enum?displayProperty=fullName></span></span>   
 <span data-ttu-id="d22da-153">[C# 程式設計手冊](../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d22da-153">[C# Programming Guide](../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d22da-154">enum</span><span class="sxs-lookup"><span data-stu-id="d22da-154">enum</span></span>](../../csharp/language-reference/keywords/enum.md)

