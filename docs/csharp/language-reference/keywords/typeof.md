---
title: "typeof (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "typeof"
  - "typeof_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "typeof 關鍵字 [C#]"
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# typeof (C# 參考)
用來取得型別的 `System.Type` 物件。  `typeof` 運算式的格式如下：  
  
```  
System.Type type = typeof(int);  
```  
  
## 備註  
 若要取得運算式的執行階段型別，請使用如下列範例所示的 .NET Framework 方法 <xref:System.Object.GetType%2A>：  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` 運算子無法多載。  
  
 `typeof` 運算子也可在開放泛型型別上使用。  具有一個以上型別參數的型別，在規格中必須有適當數目的逗號。  下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。  假設方法為 MethodInfo 型別的執行個體：  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## 範例  
 [!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#12)]  
  
## 範例  
 這個範例會使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數字計算結果的型別。  這取決於產生的數字其儲存需求。  
  
 [!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#13)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.Type?displayProperty=fullName>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)