---
title: 物件和集合初始設定式 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: def33041c4202c80aad9f08d1ff8d9dbbc477061
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892414"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="3778f-102">物件和集合初始設定式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3778f-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="3778f-103">物件初始設定式可讓您在建立期間將值指派給物件的任何可存取欄位或屬性，而不用叫用後面接著幾行指派陳述式的建構函式。</span><span class="sxs-lookup"><span data-stu-id="3778f-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="3778f-104">物件初始設定式語法可讓您為建構函式指定引數或省略引數 (以及括號語法)。</span><span class="sxs-lookup"><span data-stu-id="3778f-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="3778f-105">下列範例將示範如何使用有具名類型 `Cat` 的物件初始設定式，以及如何叫用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="3778f-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="3778f-106">請注意 `Cat` 類別中自動實作屬性的用法。</span><span class="sxs-lookup"><span data-stu-id="3778f-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="3778f-107">如需詳細資訊，請參閱[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3778f-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="3778f-108">物件初始設定式語法可讓您建立執行個體，然後將新建立的物件及其指派的屬性指派給指派作業中的變數。</span><span class="sxs-lookup"><span data-stu-id="3778f-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="3778f-109">具有匿名類型的物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="3778f-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="3778f-110">雖然物件初始設定式可以用於任何內容，但是在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中特別有用。</span><span class="sxs-lookup"><span data-stu-id="3778f-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="3778f-111">查詢運算式經常使用[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)，此型別只能使用物件初始設定式初始化，如下列宣告所示。</span><span class="sxs-lookup"><span data-stu-id="3778f-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="3778f-112">匿名型別可讓 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中的 `select` 子句將原始序列的物件轉換為其值和圖形可能與原始物件不同的物件。</span><span class="sxs-lookup"><span data-stu-id="3778f-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="3778f-113">如果您只要儲存序列中每個物件的部分資訊，這就會很實用。</span><span class="sxs-lookup"><span data-stu-id="3778f-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="3778f-114">在下列範例中，假設產品物件 (`p`) 包含許多欄位和方法，而您只想要建立包含產品名稱和單價的物件序列。</span><span class="sxs-lookup"><span data-stu-id="3778f-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="3778f-115">執行此查詢時，`productInfos` 變數將會包含可以在 `foreach` 陳述式中存取的物件序列，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3778f-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="3778f-116">新的匿名類型中的每個物件都有兩個公用屬性，這兩個屬性會接收與原始物件中的屬性或欄位相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="3778f-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="3778f-117">您也可以在建立匿名類型時重新命名欄位，下列範例會將 `UnitPrice` 欄位重新命名為 `Price`。</span><span class="sxs-lookup"><span data-stu-id="3778f-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a><span data-ttu-id="3778f-118">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="3778f-118">Collection initializers</span></span>  
 <span data-ttu-id="3778f-119">如果集合類別是實作 <xref:System.Collections.IEnumerable>，且具有 `Add` 與適當簽章以作為執行個體方法或擴充方法，集合初始設定式可讓您在初始化這類集合類別時，指定一或多個項目初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3778f-119">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="3778f-120">項目初始設定式可以是簡單的值、運算式或物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3778f-120">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="3778f-121">藉由使用集合初始設定式，您就不需要在原始程式碼中指定多個對類別之 `Add` 方法的呼叫，編譯器會加入呼叫。</span><span class="sxs-lookup"><span data-stu-id="3778f-121">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="3778f-122">下列範例將示範兩個簡單的集合初始設定式：</span><span class="sxs-lookup"><span data-stu-id="3778f-122">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="3778f-123">下列集合初始設定式會使用物件初始設定式來初始化先前範例中所定義 `Cat` 類別的物件。</span><span class="sxs-lookup"><span data-stu-id="3778f-123">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="3778f-124">請注意，每個物件初始設定式會以括號括住並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="3778f-124">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="3778f-125">如果集合的 `Add` 方法允許，您可以將 [null](../../../csharp/language-reference/keywords/null.md) 指定為集合初始設定式中的項目。</span><span class="sxs-lookup"><span data-stu-id="3778f-125">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="3778f-126">如果集合支援索引，您可以指定索引的項目。</span><span class="sxs-lookup"><span data-stu-id="3778f-126">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="3778f-127">範例</span><span class="sxs-lookup"><span data-stu-id="3778f-127">Examples</span></span>

 <span data-ttu-id="3778f-128">下列範例結合了物件和集合初始設定式的概念。</span><span class="sxs-lookup"><span data-stu-id="3778f-128">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="3778f-129">如下列範例所示，實作 <xref:System.Collections.IEnumerable> 的物件包含了具有多個參數的 `Add` 方法，讓集合初始設定式可以處理對應 `Add` 方法簽章的清單中每個項目的多個元素。</span><span class="sxs-lookup"><span data-stu-id="3778f-129">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="3778f-130">如下列範例所示，`Add` 方法可以使用 `params` 關鍵字來接受各種數目的引數。</span><span class="sxs-lookup"><span data-stu-id="3778f-130">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="3778f-131">此範例示範索引子的自訂實作，以及使用索引來初始化集合。</span><span class="sxs-lookup"><span data-stu-id="3778f-131">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="3778f-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="3778f-132">See Also</span></span>

- [<span data-ttu-id="3778f-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3778f-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3778f-134">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="3778f-134">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="3778f-135">匿名類型</span><span class="sxs-lookup"><span data-stu-id="3778f-135">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
