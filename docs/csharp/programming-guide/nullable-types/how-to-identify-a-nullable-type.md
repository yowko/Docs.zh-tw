---
title: "如何：識別可為 Null 的類型 (C# 程式設計手冊) | Microsoft Docs"
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
  - "可為 null 的類型 [C#], 識別"
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：識別可為 Null 的類型 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以使用 C\# 的 [typeof](../../../csharp/language-reference/keywords/typeof.md) 運算子來建立表示可為 Null 的型別 \(Nullable Type\) 之 <xref:System.Type> 物件。  
  
```  
System.Type type = typeof(int?);  
```  
  
 您也可以使用 <xref:System.Reflection> 命名空間的類別和方法來產生表示可為 Null 的型別之 <xref:System.Type> 物件。  不過，如果您嘗試在執行階段使用 <xref:System.Object.GetType%2A> 方法或 `is` 運算子，從可為 Null 的變數取得型別資訊，則結果會是表示基礎型別的 <xref:System.Type> 物件，而不是可為 Null 的型別本身。  
  
 當可為 Null 的型別隱含轉換為 <xref:System.Object> 時，在該型別上呼叫 `GetType` 會產生 boxing 作業。  因此，<xref:System.Object.GetType%2A> 一定會傳回表示基礎型別的 <xref:System.Type> 物件，而不是可為 Null 的型別。  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C\# 的 [is](../../../csharp/language-reference/keywords/is.md) 運算子也可以在可為 Null 的基礎型別上運作。  因此，您無法使用 `is` 來判斷某個變數是否是可為 Null 的型別。  下列範例示範 `is` 運算子如何將可為 Null 的 \<int\> 變數視為 int。  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## 範例  
 使用下列程式碼可判斷 <xref:System.Type> 物件是否表示可為 Null 的型別。  請記得，如果 `Type` 物件是從 <xref:System.Object.GetType%2A> 呼叫所傳回，這段程式碼一定會傳回 false，如本主題先前所述。  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## 請參閱  
 [可為 Null 的類型](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Box 處理可為 Null 的類型](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)