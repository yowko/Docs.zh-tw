---
title: "物件和集合初始設定式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "集合初始設定式 [C#]"
  - "物件初始設定式 [C#]"
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# 物件和集合初始設定式 (C# 程式設計手冊)
物件初始設定式可讓您在建立期間將值指派給物件的任何可存取欄位或屬性，而不用叫用後面接著幾行指派陳述式的建構函式。  物件初始設定式語法可讓您為建構函式指定引數或省略引數 \(以及括號語法\)。  下列範例將示範如何使用有具名類型 `Cat` 的物件初始設定式，以及如何叫用預設建構函式。  請注意 `Cat` 類別中自動實作屬性的用法。  如需詳細資訊，請參閱[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
 [!code-cs[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#39)]  
  
 [!code-cs[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#45)]  
  
## 具有匿名類型的物件初始設定式  
 雖然物件初始設定式可以用於任何內容，但是在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢運算式中特別有用。  查詢運算式經常使用[匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)，此類型只能使用物件初始設定式初始化，如下列宣告所示。  
  
```  
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 匿名類型可讓 `select` 查詢運算式中的 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 子句將原始序列的物件轉換為其值和圖形可能與原始物件不同的物件。  如果您只要儲存序列中每個物件的部分資訊，這就會很實用。  在下列範例中，假設產品物件 \(`p`\) 包含許多欄位和方法，而您只想要建立包含產品名稱和單價的物件序列。  
  
 [!code-cs[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#40)]  
  
 執行此查詢時，`productInfos` 變數將會包含可以在 `foreach` 陳述式中存取的物件序列，如下列範例所示：  
  
```  
foreach(var p in productInfos){...}  
```  
  
 新的匿名類型中的每個物件都有兩個公用屬性，這兩個屬性會接收與原始物件中的屬性或欄位相同的名稱。  您也可以在建立匿名類型時重新命名欄位，下列範例會將 `UnitPrice` 欄位重新命名為 `Price`。  
  
```  
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## 具有可為 null 類型的物件初始設定式  
 使用具有可為 null 類型的物件初始設定式是編譯時期錯誤。  
  
## 集合初始設定式  
 集合初始設定式可讓您在初始化實作 <xref:System.Collections.IEnumerable> 的集合類別或具有 `Add` 擴充方法的類別時，指定一個或多個項目初始設定式。  項目初始設定式可以是簡單的值、運算式或物件初始設定式。  藉由使用集合初始設定式，您就不需要在原始程式碼中指定多個對類別之 `Add` 方法的呼叫，編譯器會加入呼叫。  
  
 下列範例將示範兩個簡單的集合初始設定式：  
  
```  
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 下列集合初始設定式會使用物件初始設定式來初始化先前範例中所定義 `Cat` 類別的物件。  請注意，每個物件初始設定式會以括號括住並以逗號分隔。  
  
 [!code-cs[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#41)]  
  
 如果集合的 [null](../../../csharp/language-reference/keywords/null.md) 方法允許，您可以將 `Add` 指定為集合初始設定式中的項目。  
  
 [!code-cs[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#42)]  
  
 如果集合支援索引，您可以指定索引的項目。  
  
```  
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
  
```  
  
## 範例  
 [!code-cs[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#46)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)