---
title: "Box 處理可為 Null 的類型 (C# 程式設計手冊) | Microsoft Docs"
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
  - "boxing [C#], 可為 null 的類型"
  - "可為 null 的類型 [C#], boxing 和 unboxing"
  - "unboxing [C#], 可為 null 的類型"
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Box 處理可為 Null 的類型 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

只有當以可為 Null 的型別 \(Nullable Type\) 為基礎的物件不是 Null 時，該物件才會是 boxed。  如果 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則會將物件參考指派為 `null`，而不會做 boxing 處理。  例如：  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 如果物件為非 null \(若 <xref:System.Nullable%601.HasValue%2A> 是 `true`\)，便會進行 boxing 處理，但只有可為 Null 的物件所依據的基礎型別會是 boxed。  對不可為 Null 的數值型別執行 box 處理就會 box 數值型別本身，而非包裝實值型別的 <xref:System.Nullable%601?displayProperty=fullName>。  例如：  
  
```  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 這兩個 boxed 物件與透過對不可為 Null 型別執行 box 處理而建立的物件相同。  而且就像不可為 null 的 boxed 型別一樣，可以 unboxed 成可為 null 的型別，如下列範例所示：  
  
```  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## 備註  
 在執行 box 的動作時，可為 Null 型別的行為提供了兩個優點：  
  
1.  可以測試可為 Null 的物件及其 boxed 對應物件是否為 null：  
  
    ```  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Boxed 可為 Null 型別完全支援基礎型別的功能：  
  
    ```  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [可為 Null 的類型](../../../visual-basic/reference/command-line-compiler/index.md)   
 [如何：識別可為 Null 的類型](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)