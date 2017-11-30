---
title: ".NET 中剖析其他字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a>.NET 中剖析其他字串
除了數字和<xref:System.DateTime>字串，您可以剖析字串，表示類型<xref:System.Char>， <xref:System.Boolean>，和<xref:System.Enum>為資料類型。  
  
## <a name="char"></a>Char  
 與 **Char** 資料類型相關聯的靜態 parse 方法，可用於將包含單一字元的字串轉換成其 Unicode 值。 下列程式碼範例會將字串剖析成 Unicode 字元。  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 **布林**資料型別包含**剖析**方法可讓您將表示成實際的布林值的字串轉換**布林**型別。 這個方法不區分大小寫，而且可以成功剖析包含 "True" 或 "False" 的字串。 **剖析**方法相關聯**布林**類型也可以剖析會包圍泛空白字元的字串。 如果傳遞任何其他字串，<xref:System.FormatException>就會擲回。  
  
 下列程式碼範例使用**剖析**方法，將字串轉換成布林值。  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>列舉  
 您可以使用靜態的 **Parse** 方法初始化字串值的列舉類型。 這個方法會接受您剖析的列舉類型、 要剖析的字串和選擇性的布林旗標，以指出會區分大小寫剖析。 您要剖析的字串可以包含數個以逗號分隔的值，前後可有一或多個空格 (也稱為空白字元)。 當字串包含多個值時，傳回物件的值就是結合了位元 OR 運算的所有指定值的值。  
  
 下列範例會使用**剖析**方法，將字串表示轉換成列舉值。 <xref:System.DayOfWeek>列舉型別會初始化為**星期四**從字串。  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [剖析字串](../../../docs/standard/base-types/parsing-strings.md)  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 [在.NET 中的型別轉換](../../../docs/standard/base-types/type-conversion.md)
