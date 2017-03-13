---
title: "sizeof (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "sizeof_CSharpKeyword"
  - "sizeof"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sizeof 關鍵字 [C#]"
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# sizeof (C# 參考)
用於取得 Unmanaged 型別的位元組大小。  Unmanaged 型別包含下表列出的內建型別以及下列項目：  
  
-   列舉型別  
  
-   指標型別  
  
-   使用者定義的結構，不包含任何欄位或者為參考型別的屬性。  
  
 下列範例顯示如何擷取 `int` 的大小。  
  
```c#  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## 備註  
 從 C\# 2.0 版開始，將 `sizeof` 套用至內建型別 \(Primitive Type\) 時，不再需要使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 模式。  
  
 `sizeof` 運算子無法多載。  `sizeof` 運算子所傳回的值是 `int` 型別。  下表列出替代 `sizeof` 運算式 \(使用特定的內建型別做為運算元\) 的常數值：  
  
|運算式|常數值|  
|---------|---------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 \(Unicode\)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 至於所有其他型別，包括結構 \(Struct\)，`sizeof` 運算子只能用於 unsafe 程式碼區塊。  雖然您可以使用 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> 方法，但是這個方法傳回的值不一定等於 `sizeof` 傳回的值。  <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> 會傳回型別經過封送處理後的大小，而 `sizeof` 則傳回經過 Common Language Runtime 配置的大小，包括任何填補。  
  
## 範例  
 [!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [enum](../../../csharp/language-reference/keywords/enum.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)