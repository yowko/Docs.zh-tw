---
title: "在 .NET Framework 中剖析其他字串 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Char 資料類型，剖析字串"
  - "列舉 [.NET Framework]，剖析字串"
  - "基底類型，剖析字串"
  - "剖析字串，其他字串"
  - "布林資料類型，剖析字串"
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 在 .NET Framework 中剖析其他字串
除了數值和 <xref:System.DateTime> 字串以外，您也可以將代表 <xref:System.Char>、<xref:System.Boolean> 和 <xref:System.Enum> 型別的字串剖析成資料型別。  
  
## Char  
 和 **Char** 資料型別關聯的靜態剖析方法可用來將包含單一字元的字串轉換成 Unicode 值。  下列程式碼範例會將字串剖析成 Unicode 字元。  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## Boolean  
 **Boolean** 資料型別包含 **Parse** 方法，您可用此方法將代表布林值 \(Boolean\) 的字串轉換成實際的 **Boolean** 型別。  這個方法不會區分大小寫，而且可以成功剖析包含 True 或 False 的字串。 與 **Boolean** 型別關聯的 **Parse** 方法也可以剖析前後有空白區 \(White Space\) 的字串。  如果傳遞的是其他任何字串，便會擲回 <xref:System.FormatException>。  
  
 下列程式碼範例使用 **Parse** 方法，將字串轉換成布林值。  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## 列舉  
 您可以使用靜態 **Parse** 方法，將列舉型別初始化成字串值。  這個方法可接受正在剖析的列舉型別、要剖析的字串，以及指出剖析是否區分大小寫的選擇性 \(Optional\) 布林值旗標。  您正在剖析的字串可包含幾個以逗號分隔的值，而且它的前面或後面可以有一個或多個空格 \(也稱為泛空白字元\)。  當字串包含多個值時，傳回物件的值就是以位元運算 OR 組合所有指定值之後產生的值。  
  
 下列程式碼範例使用 **Parse** 方法，將字串代表轉換成列舉值。  <xref:System.DayOfWeek> 列舉型別會初始化成字串中的 **Thursday**。  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## 請參閱  
 [剖析字串](../../../docs/standard/base-types/parsing-strings.md)   
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)   
 [.NET Framework 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)