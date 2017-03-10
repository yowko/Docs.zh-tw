---
title: "如何：將位元組陣列轉換成整數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "位元組陣列 [C#], 轉換為 int"
  - "轉換 [C#], 位元組陣列轉換為 int"
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 如何：將位元組陣列轉換成整數 (C# 程式設計手冊)
這個範例會示範如何使用 <xref:System.BitConverter> 類別，將位元組陣列轉換為 [int](../../../csharp/language-reference/keywords/int.md)，並轉換回位元組陣列。  例如，您讀取了網路上的位元組之後，您可能需要將位元組轉換為內建資料型別。  除了範例中的 [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> 方法以外，下表會列出 <xref:System.BitConverter> 類別中的方法，這些方法會將位元組 \(從位元組陣列\) 轉換為內建型別。  
  
|傳回的型別|方法|  
|-----------|--------|  
|`bool`|[ToBoolean\(Byte\<xref:System.BitConverter.ToBoolean%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`char`|[ToChar\(Byte\<xref:System.BitConverter.ToChar%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`double`|[ToDouble\(Byte\<xref:System.BitConverter.ToDouble%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`short`|[ToInt16\(Byte\<xref:System.BitConverter.ToInt16%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`int`|[ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`long`|[ToInt64\(Byte\<xref:System.BitConverter.ToInt64%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`float`|[ToSingle\(Byte\<xref:System.BitConverter.ToSingle%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`ushort`|[ToUInt16\(Byte\<xref:System.BitConverter.ToUInt16%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`uint`|[ToUInt32\(Byte\<xref:System.BitConverter.ToUInt32%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`ulong`|[ToUInt64\(Byte\<xref:System.BitConverter.ToUInt64%28System.Byte%5B%5D%2CSystem.Int32%29>|  
  
## 範例  
 這個範例會初始化位元組陣列，若電腦架構是位元組由小到大 \(也就是說，先儲存較不重要的位元組\) 時將陣列反向，然後呼叫 [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> 方法，將陣列中的四個位元組轉換為 `int`。  [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> 的第二個引數會指定位元組陣列的起始索引。  
  
> [!NOTE]
>  輸出可能會因電腦架構的位元組順序而有所不同。  
  
 [!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-byte-ar_1.cs)]  
  
## 範例  
 在這個範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換為位元組陣列。  
  
> [!NOTE]
>  輸出可能會因電腦架構的位元組順序而有所不同。  
  
 [!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-byte-ar_2.cs)]  
  
## 請參閱  
 <xref:System.BitConverter>   
 <xref:System.BitConverter.IsLittleEndian>   
 [類型](../../../csharp/programming-guide/types/index.md)