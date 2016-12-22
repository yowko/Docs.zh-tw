---
title: "如何：使用複合索引鍵執行聯結 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "複合索引鍵 [C# 中的 LINQ]"
  - "聯結 [C#]"
  - "聯結 [C#], 複合索引鍵"
  - "查詢 [C# 中的 LINQ], 聯結"
  - "查詢運算式 [C# 中的 LINQ], 聯結"
ms.assetid: 3e015b3f-9cca-4b0c-aa97-dca0d36ea592
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：使用複合索引鍵執行聯結 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個範例會示範如何執行聯結 \(Join\) 作業，您會在該作業中使用一個以上的索引鍵來定義符合項目。  使用複合索引鍵便可完成這項定義。  您會將複合索引鍵建立成匿名型別，或是包含要比較之值的具名型別。  如果查詢變數傳遞時將跨越方法界限，請使用會覆寫該索引鍵之 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 的具名型別。  在每個索引鍵中，這些屬性的名稱及其出現的順序都必須相同。  
  
## 範例  
 下列範例會示範如何使用複合索引鍵來聯結來自三個資料表的資料：  
  
```  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,         d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 複合索引鍵上的型別推斷，會根據索引鍵中的屬性名稱及其出現的順序來進行。  如果來源序列中的屬性沒有相同名稱，您就必須在索引鍵中指派新的名稱。  例如，如果 `Orders` 資料表和 `OrderDetails` 資料表分別對其資料行使用不同的名稱，您就可以在匿名型別中指派相同的名稱以建立複合索引鍵：  
  
```  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 複合索引鍵也可以用於 `group` 子句。  
  
## 編譯程式碼  
  
-   若要編譯並執行這段程式碼，請依照下列步驟執行：  
  
-   開啟 [如何：連接到 Northwind 資料庫](../Topic/How%20to:%20Connect%20to%20the%20Northwind%20Database.md)，並依照指示來設定專案及建立資料庫連接。  如需詳細資訊，請參閱 [如何：安裝範例資料庫](../Topic/How%20to:%20Install%20Sample%20Databases.md)。  
  
-   在 samples.cs 中，建立會採用 Northwind 輸入參數 \(名稱為 db\) 之新的空方法 \(相似於該檔案中的其他方法\)。  將這個範例中的程式碼貼到該方法主體中。  
  
-   將 program.cs 修改成從 `Main` 呼叫該新方法。  
  
-   按 F5 編譯並執行查詢。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)   
 [group 子句](../../../csharp/language-reference/keywords/group-clause.md)