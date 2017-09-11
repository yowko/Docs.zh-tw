---
title: "物件和集合初始設定式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: 27
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 66045a6902e64db394a1f5812658e25a11692027
ms.openlocfilehash: a4d0e8f348afdf1793804a4062be45d2fb4e7e2b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/21/2017

---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="7b906-102">物件和集合初始設定式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="7b906-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="7b906-103">物件初始設定式可讓您在建立期間將值指派給物件的任何可存取欄位或屬性，而不用叫用後面接著幾行指派陳述式的建構函式。</span><span class="sxs-lookup"><span data-stu-id="7b906-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="7b906-104">物件初始設定式語法可讓您為建構函式指定引數或省略引數 (以及括號語法)。</span><span class="sxs-lookup"><span data-stu-id="7b906-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="7b906-105">下列範例將示範如何使用有具名類型 `Cat` 的物件初始設定式，以及如何叫用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="7b906-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="7b906-106">請注意 `Cat` 類別中自動實作屬性的用法。</span><span class="sxs-lookup"><span data-stu-id="7b906-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="7b906-107">如需詳細資訊，請參閱[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="7b906-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="7b906-108">[!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7b906-108">[!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]</span></span>  
  
 <span data-ttu-id="7b906-109">[!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7b906-109">[!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)]</span></span>  
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="7b906-110">具有匿名類型的物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="7b906-110">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="7b906-111">雖然物件初始設定式可以用於任何內容，但是在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢運算式中特別有用。</span><span class="sxs-lookup"><span data-stu-id="7b906-111">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] query expressions.</span></span> <span data-ttu-id="7b906-112">查詢運算式經常使用[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)，此型別只能使用物件初始設定式初始化，如下列宣告所示。</span><span class="sxs-lookup"><span data-stu-id="7b906-112">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="7b906-113">匿名型別可讓 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] 查詢運算式中的 `select` 子句將原始序列的物件轉換為其值和圖形可能與原始物件不同的物件。</span><span class="sxs-lookup"><span data-stu-id="7b906-113">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="7b906-114">如果您只要儲存序列中每個物件的部分資訊，這就會很實用。</span><span class="sxs-lookup"><span data-stu-id="7b906-114">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="7b906-115">在下列範例中，假設產品物件 (`p`) 包含許多欄位和方法，而您只想要建立包含產品名稱和單價的物件序列。</span><span class="sxs-lookup"><span data-stu-id="7b906-115">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 <span data-ttu-id="7b906-116">[!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="7b906-116">[!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]</span></span>  
  
 <span data-ttu-id="7b906-117">執行此查詢時，`productInfos` 變數將會包含可以在 `foreach` 陳述式中存取的物件序列，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7b906-117">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="7b906-118">新的匿名類型中的每個物件都有兩個公用屬性，這兩個屬性會接收與原始物件中的屬性或欄位相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b906-118">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="7b906-119">您也可以在建立匿名類型時重新命名欄位，下列範例會將 `UnitPrice` 欄位重新命名為 `Price`。</span><span class="sxs-lookup"><span data-stu-id="7b906-119">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="7b906-120">具有可為 null 類型的物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="7b906-120">Object initializers with nullable types</span></span>  
 <span data-ttu-id="7b906-121">使用具有可為 null 類型的物件初始設定式是編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="7b906-121">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="7b906-122">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="7b906-122">Collection initializers</span></span>  
 <span data-ttu-id="7b906-123">如果集合類別是實作 <xref:System.Collections.IEnumerable>，且具有 `Add` 與適當簽章以作為執行個體方法或擴充方法，集合初始設定式可讓您在初始化這類集合類別時，指定一或多個項目初始設定式。</span><span class="sxs-lookup"><span data-stu-id="7b906-123">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="7b906-124">項目初始設定式可以是簡單的值、運算式或物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="7b906-124">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="7b906-125">藉由使用集合初始設定式，您就不需要在原始程式碼中指定多個對類別之 `Add` 方法的呼叫，編譯器會加入呼叫。</span><span class="sxs-lookup"><span data-stu-id="7b906-125">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="7b906-126">下列範例將示範兩個簡單的集合初始設定式：</span><span class="sxs-lookup"><span data-stu-id="7b906-126">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="7b906-127">下列集合初始設定式會使用物件初始設定式來初始化先前範例中所定義 `Cat` 類別的物件。</span><span class="sxs-lookup"><span data-stu-id="7b906-127">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="7b906-128">請注意，每個物件初始設定式會以括號括住並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="7b906-128">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 <span data-ttu-id="7b906-129">[!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="7b906-129">[!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]</span></span>  
  
 <span data-ttu-id="7b906-130">如果集合的 `Add` 方法允許，您可以將 [null](../../../csharp/language-reference/keywords/null.md) 指定為集合初始設定式中的項目。</span><span class="sxs-lookup"><span data-stu-id="7b906-130">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 <span data-ttu-id="7b906-131">[!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="7b906-131">[!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]</span></span>  
  
 <span data-ttu-id="7b906-132">如果集合支援索引，您可以指定索引的項目。</span><span class="sxs-lookup"><span data-stu-id="7b906-132">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a><span data-ttu-id="7b906-133">範例</span><span class="sxs-lookup"><span data-stu-id="7b906-133">Example</span></span>  
 <span data-ttu-id="7b906-134">[!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="7b906-134">[!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b906-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b906-135">See Also</span></span>  
 <span data-ttu-id="7b906-136">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b906-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="7b906-137"> [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b906-137"> [LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
<span data-ttu-id="7b906-138"> [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="7b906-138"> [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)</span></span>

