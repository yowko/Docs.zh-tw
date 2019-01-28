---
title: 物件和集合初始設定式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 44ae8acd1278d8a6163ac1c5bc6e0a0e030c02fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676961"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>物件和集合初始設定式 (C# 程式設計手冊)

C# 可讓您具現化物件或集合，並以單一陳述式執行成員指派。

## <a name="object-initializers"></a>物件初始設定式

物件初始設定式可讓您在建立期間將值指派給物件的任何可存取欄位或屬性，而不用叫用後面接著幾行指派陳述式的建構函式。 物件初始設定式語法可讓您為建構函式指定引數或省略引數 (以及括號語法)。  下列範例將示範如何使用有具名類型 `Cat` 的物件初始設定式，以及如何叫用預設建構函式。 請注意 `Cat` 類別中自動實作屬性的用法。 如需詳細資訊，請參閱[自動實作的屬性](auto-implemented-properties.md)。  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
物件初始設定式語法可讓您建立執行個體，然後將新建立的物件及其指派的屬性指派給指派作業中的變數。

從 C# 6 開始，物件初始設定式除了指派欄位和屬性，還可以設定索引子。 請考慮此基本 `Matrix` 類別：

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

您可以使用下列程式碼來初始化單位矩陣：

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

任何包含可存取 setter 的可存取索引子都可作為物件初始設定式中的其中一個運算式，不論引數的數目或類型為何。 指派左側是由索引引數組成，運算式右側是其值。  例如，如果 `IndexersExample` 具有適當的索引子，下列內容全部有效：

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Baz = Math.PI,
    ['C',4] = "Middle C"
}
```

若要編譯上述程式碼，`IndexersExample` 類型必須具有下列成員：

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a>具有匿名類型的物件初始設定式

雖然物件初始設定式可以用於任何內容，但是在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中特別有用。 查詢運算式經常使用[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)，此型別只能使用物件初始設定式初始化，如下列宣告所示。  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

匿名型別可讓 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式中的 `select` 子句將原始序列的物件轉換為其值和圖形可能與原始物件不同的物件。 如果您只要儲存序列中每個物件的部分資訊，這就會很實用。 在下列範例中，假設產品物件 (`p`) 包含許多欄位和方法，而您只想要建立包含產品名稱和單價的物件序列。  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

執行此查詢時，`productInfos` 變數將會包含可以在 `foreach` 陳述式中存取的物件序列，如下列範例所示：  

```csharp
foreach(var p in productInfos){...}  
```

新的匿名型別中的每個物件都有兩個公用屬性，這兩個屬性會接收與原始物件中的屬性或欄位相同的名稱。 您也可以在建立匿名類型時重新命名欄位，下列範例會將 `UnitPrice` 欄位重新命名為 `Price`。  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>集合初始設定式

如果集合類別是實作 <xref:System.Collections.IEnumerable>，且具有 `Add` 與適當簽章以作為執行個體方法或擴充方法，集合初始設定式可讓您在初始化這類集合類別時，指定一或多個項目初始設定式。 項目初始設定式可以是簡單的值、運算式或物件初始設定式。 藉由使用集合初始設定式，您就不需要指定多個呼叫，編譯器會自動新增呼叫。  
  
下列範例將示範兩個簡單的集合初始設定式：  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

下列集合初始設定式會使用物件初始設定式來初始化先前範例中所定義 `Cat` 類別的物件。 請注意，每個物件初始設定式會以括號括住並以逗號分隔。  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
如果集合的 `Add` 方法允許，您可以將 [null](../../language-reference/keywords/null.md) 指定為集合初始設定式中的項目。  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 如果集合支援讀取/寫入索引，您可以指定索引的項目。
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

上述範例會產生呼叫 <xref:System.Collections.Generic.Dictionary%602.Item(%600)> 以設定值的程式碼。 從 C# 6 開始，您可以使用下列語法來初始化字典及其他關聯容器。 請注意，它會使用具有多個值的物件，而不是使用括弧和指派的索引子語法：

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

初始設定式範例會呼叫 <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> 來將三個項目新增至字典。 由於編譯器所產生的方法呼叫，這兩種初始化關聯集合的方式會有稍微不同的行為。 這兩種方式都可以搭配 `Dictionary` 類別運作。 其他類型視其公用 API 而定，可能只支援其中一種。

## <a name="examples"></a>範例

下列範例結合了物件和集合初始設定式的概念。

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

下列範例顯示實作 <xref:System.Collections.IEnumerable> 並包含具有多個參數之 `Add` 方法的物件，它使用集合初始設定式來處理對應至 `Add` 方法簽章之清單中每個項目的多個元素。

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add` 方法可以使用 `params` 關鍵字來接受各種數目的引數，如下列範例所示。 此範例也示範索引子的自訂實作，以使用索引來初始化集合。

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [LINQ 查詢運算式](../linq-query-expressions/index.md)
- [匿名類型](anonymous-types.md)
