---
title: "可為 Null 的類型 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 可為 null 的類型"
  - "可為 null 的類型 [C#]"
  - "類型 [C#], 可為 null 的"
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 44
---
# 可為 Null 的類型 (C# 程式設計手冊)
可為 Null 的型別是 <xref:System.Nullable%601?displayProperty=fullName> 結構的執行個體。  可為 Null 的型別能夠代表其基礎實值型別的正確值範圍，加上其他 `null` 值。  例如，`Nullable<Int32>` \(念法是 "Nullable of Int32"\)，可以指派為從 \-2147483648 到 2147483647 的任何值，或是可以指派為 `null` 值。  `Nullable<bool>` 可以指派為 [true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 或 [null](../../../csharp/language-reference/keywords/null.md) 的值。  在處理資料庫以及包含並未指派值之項目的其他資料型別時，將 `null` 指派給數字和布林型別的功能就特別有用。  例如，資料庫中的布林欄位能夠儲存值 `true` 或 `false`，或者也可能未定義。  
  
 [!code-cs[csProgGuideTypes#3](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
 此範例將顯示輸出；  
  
 `num = Null`  
  
 `Nullable object must have a value.`  
  
 如需更多範例，請參閱 [用可為 Null 的類型](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## 可為 Null 的型別概觀  
 可為 Null 的型別有下列特性：  
  
-   可為 Null 的型別代表能夠指派 `null` 值的實值型別變數。  您無法根據參考型別建立可為 Null 的型別   \(參考型別已支援 `null` 值\)  
  
-   語法 `T?` 是 <xref:System.Nullable%601> 的簡略表示法，其中 `T` 是實值型別。  兩種格式可以互相變更  
  
-   就像針對一般實值型別一樣，將值指派至可為 Null 的型別，例如 `int? x = 10;` 或 `double? d = 4.108`。  可為 Null 的型別亦可獲派 `null`: `int? x = null.` 值  
  
-   使用 <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> 方法傳回指派的值；若值為 `null`，則傳回基礎型別的預設值，例如  `int j = x.GetValueOrDefault();`  
  
-   使用 <xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 唯讀屬性測試 null 並擷取值，如下列範例中所示：`if(x.HasValue) j = x.Value;`  
  
    -   如果該變數包含值，則 `HasValue` 屬性傳回 `true`，如果是 `null` 則傳回 `false`。  
  
    -   如果有指派值，`Value` 屬性便會傳回值。  否則，會擲回 <xref:System.InvalidOperationException?displayProperty=fullName>。  
  
    -   `HasValue` 的預設值為 `false`。  `Value` 屬性沒有預設值。  
  
    -   您也可以將 `==` 和 `!=` 運算子使用於可為 Null 的型別，如下列範例所示：`if (x != null) y = x;`  
  
-   當目前值為 `null` 的可為 Null 型別指派至不可為 Null 的型別時，請使用 `??` 運算子指派將套用的預設值，例如 `int? x = null; int y = x ?? -1;`  
  
-   不允許巢狀式可為 Null 的型別。  不會編譯下列程式碼行：`Nullable<Nullable<int>> n;`  
  
## 相關章節  
 如需詳細資訊，請參閱下列主題：  
  
-   [用可為 Null 的類型](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Box 處理可為 Null 的類型](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [?? 運算子](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.Nullable>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [哪些完全「被列舉的」方法?](http://go.microsoft.com/fwlink/?LinkId=112382)