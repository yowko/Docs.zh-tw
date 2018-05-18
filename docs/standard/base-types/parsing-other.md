---
title: 在 .NET 中剖析其他字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7becf993db866e24381fe9013c82d74dd91ee9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="parsing-other-strings-in-net"></a>在 .NET 中剖析其他字串
除了數值和 <xref:System.DateTime> 字串，您也可以將表示 <xref:System.Char>、<xref:System.Boolean> 和 <xref:System.Enum> 類型的字串剖析為資料類型。  
  
## <a name="char"></a>Char  
 與 **Char** 資料類型相關聯的靜態 parse 方法，可用於將包含單一字元的字串轉換成其 Unicode 值。 下列程式碼範例會將字串剖析成 Unicode 字元。  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 **Boolean** 資料類型包含的 **Parse** 方法，可用來將代表 Boolean 值的字串轉換成實際的 **Boolean** 類型。 這個方法不區分大小寫，而且可以成功剖析包含 "True" 或 "False" 的字串。 與 **Boolean** 類型相關聯的 **Parse** 方法也可剖析由空白字元所包圍的字串。 如果傳遞任何其他字串，則會擲回 <xref:System.FormatException>。  
  
 下列程式碼範例會使用 **Parse** 方法來將字串轉換為 Boolean 值。  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>列舉  
 您可以使用靜態的 **Parse** 方法初始化字串值的列舉類型。 此方法接受您剖析的列舉類型、要剖析的字串，以及指出剖析是否區分大小寫的選擇性 Boolean 旗標。 您要剖析的字串可以包含數個以逗號分隔的值，前後可有一或多個空格 (也稱為空白字元)。 當字串包含多個值時，傳回物件的值就是結合了位元 OR 運算的所有指定值的值。  
  
 下列範例會使用 **Parse** 方法來將字串表示轉換為列舉值。 <xref:System.DayOfWeek> 列舉會從字串初始化為 **Thursday**。  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>請參閱  
 [Parsing Strings](../../../docs/standard/base-types/parsing-strings.md)  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)
