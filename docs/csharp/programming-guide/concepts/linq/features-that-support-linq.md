---
title: "C# Features That Support LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], features supporting LINQ"
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# C# Features That Support LINQ
下節介紹 C\# 3.0 中引進的新語言建構。  雖然這些新功能或多或少與 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢有關，但是它們不只可以用於 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)]，還可以用於任何您覺得適合的內容中。  
  
## 查詢運算式  
 查詢運算式使用類似於 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。  編譯期間查詢語法會轉換為對 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 提供者 \(Provider\) 實作的標準查詢運算子擴充方法進行的方法呼叫。  應用程式會透過使用 `using` 指示詞指定適當的命名空間 \(Namespace\)，來控制範圍內的標準查詢運算子。  下列查詢運算式會接受字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)。  
  
## 隱含型別變數 \(var\)  
 您可以使用 [var](../../../../csharp/language-reference/keywords/var.md) 修飾詞 \(Modifier\) 指示編譯器 \(Compiler\) 推斷並指派型別 \(如下所示\)，而不是在宣告和初始化變數時明確指定型別：  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 宣告為 `var` 的變數和明確指定型別的變數一樣是強型別的。  `var` 可以用來建立匿名型別，但是也可以用於任何區域變數。  陣列也可以使用隱含型別進行宣告。  
  
 如需詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## 物件和集合初始設定式  
 物件和集合初始設定式可以初始化物件，而不需要明確呼叫物件的建構函式 \(Constructor\)。  初始設定式通常會用在將來源資料規劃為新資料型別的查詢運算式中。  假設有個名為 `Customer` 的類別 \(Class\) 具有公用的 \(Public\) `Name` 和 `Phone` 屬性，則可以如同下列程式碼使用物件初始設定式：  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 如需詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
## 匿名型別  
 匿名型別是由編譯器所建構，只有編譯器才知道型別名稱。  匿名型別提供了暫時將查詢結果中的一組屬性分組，而不需要另外定義具名型別的便利方式。  匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 如需詳細資訊，請參閱[匿名類型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
## 擴充方法  
 擴充方法是一種可以與型別相關聯的靜態 \(Static\) 方法，因此可以像呼叫型別上的執行個體方法 \(Instance Method\) 一樣呼叫它。  這項功能實際上可讓您將新的方法「加入」至現有型別，而不需要實際修改現有型別。  標準查詢運算子是一組擴充方法，可為實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何型別提供 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢功能。  
  
 如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
## Lambda 運算式  
 Lambda 運算式是一種內嵌 \(Inline\) 函式，其使用 \=\> 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換為委派 \(Delegate\) 或運算式樹狀架構。  在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 程式設計中，當您直接對標準查詢運算子進行方法呼叫時就會遇到 Lambda 運算式。  
  
 如需詳細資訊，請參閱：  
  
-   [匿名函式](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Lambda 運算式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)  
  
## 自動實作屬性  
 自動實作的屬性可讓屬性宣告更為簡潔。  當您如同下列範例所示宣告屬性時，編譯器會建立私用的 \(Private\) 匿名支援欄位，讓您只能透過屬性 getter 和 setter 來進行存取。  
  
```  
public string Name {get; set;}  
```  
  
 如需詳細資訊，請參閱[自動實作的屬性](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
## 請參閱  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Visual Basic Features That Support LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)