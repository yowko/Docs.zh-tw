---
title: "屬性 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.properties"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 屬性"
  - "屬性 [C#]"
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 屬性 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

屬性是提供彈性機制以讀取、寫入或計算私人欄位值的成員。  使用屬性時可將其視為公用資料成員，但實際上屬性是名為*存取子*的特殊方法。  如此可讓資料更容易存取，同時有助於提升方法的安全性和彈性。  
  
 在本範例中，`TimePeriod` 類別會儲存一個時段。  此類別在內部會儲存以秒為單位的時間，但名為 `Hours` 的屬性可讓用戶端指定以小時為單位的時間。  `Hours` 屬性的存取子會執行小時與秒之間的轉換。  
  
## 範例  
 [!code-cs[csProgGuideProperties#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/properties_1.cs)]  
  
## 運算式主體定義  
 使用直接隨運算式的結果立即傳回的屬性，是很常見的作法。  有個語法捷徑可以使用 `=>` 定義這些屬性：  
  
```c#  
public string Name => First + " " + Last;   
```  
  
 屬性必須是唯讀，且您不會使用 `get` 存取子關鍵字。  
  
## 屬性概觀  
  
-   屬性可讓類別公開取得和設定值的公用方式，同時隱藏實作或驗證程式碼。  
  
-   [get](../../../csharp/language-reference/keywords/get.md) 屬性存取子可用來傳回屬性值，而 [set](../../../csharp/language-reference/keywords/set.md) 存取子則用來指派新值。  這些存取子可以有不同的存取層級。  如需詳細資訊，請參閱[限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
-   [值](../../../csharp/language-reference/keywords/value.md)關鍵字可用來定義由 `set` 索引子指派的值。  
  
-   不會實作 `set` 存取子的屬性是唯讀的。  
  
-   對於不需要自訂存取子程式碼的簡單屬性，請考量使用自動實作屬性的選項。  如需詳細資訊，請參閱[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
## 相關章節  
  
-   [使用屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [介面屬性](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [屬性與索引子之間的比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [使用屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [索引子](../../../visual-basic/reference/command-line-compiler/index.md)