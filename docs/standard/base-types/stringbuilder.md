---
title: 在 .NET 中使用 StringBuilder 類別
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 099e2de40458e42c9df34e74dee8d9fc7c425dea
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44197310"
---
# <a name="using-the-stringbuilder-class-in-net"></a>在 .NET 中使用 StringBuilder 類別
<xref:System.String> 物件不可變。 每次您使用 <xref:System.String?displayProperty=nameWithType> 類別的其中一個方法時，就會在記憶體中建立新的字串物件，這需要為該新物件配置新的空間。 在您需要重複修改字串的情況下，與建立新 <xref:System.String> 物件相關聯的額外負荷可能成本高昂。 當您想要修改字串，而不建立新物件時，可以使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別。 例如，在迴圈中將許多字串串連在一起時，可以使用 <xref:System.Text.StringBuilder> 類別來提升效能。  
  
## <a name="importing-the-systemtext-namespace"></a>匯入 System.Text 命名空間  
 <xref:System.Text.StringBuilder> 類別位於 <xref:System.Text> 命名空間。  為了避免在程式碼中提供完整的類型名稱，您可以匯入 <xref:System.Text> 命名空間：  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>具現化 StringBuilder 物件  
 您可以使用其中一個多載建構函式方法來將變數初始化，以建立 <xref:System.Text.StringBuilder> 類別的新執行個體，如下列範例所示。  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>設定容量和長度  
 雖然 <xref:System.Text.StringBuilder> 是一個動態物件，可讓您擴充其封裝之字串中的字元數，但您可以指定它能容納的字元數上限值。 這個值稱為物件的容量，不應該與目前 <xref:System.Text.StringBuilder> 保存的字串長度混淆。 例如，您可以用字串 "Hello" 建立 <xref:System.Text.StringBuilder> 類別的新執行個體，其長度為 5，而您可能會將物件的最大容量指定為 25。 當您修改 <xref:System.Text.StringBuilder> 時，在到達容量上限之前，它不會重新配置自己的大小。 發生這種情況時，會自動配置新的空間，而且容量加倍。 您可以使用其中一個多載建構函式來指定 <xref:System.Text.StringBuilder> 類別的容量。 下列範例會指定 `myStringBuilder` 物件可以擴展到最多 25 個空格。  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 此外，您可以使用讀/寫 <xref:System.Text.StringBuilder.Capacity%2A> 屬性來設定物件的長度上限。 下列範例會使用 **Capacity** 屬性來定義物件長度上限。  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> 方法可用來檢查目前 **StringBuilder** 的容量。 如果容量大於傳遞的值，不會進行任何變更。不過，如果容量小於傳遞的值，會變更目前的容量以符合傳遞的值。  
  
 也可以檢視或設定 <xref:System.Text.StringBuilder.Length%2A> 屬性。 如果您將 **Length** 屬性的值設成大於 **Capacity** 屬性的值，則 **Capacity** 屬性會自動變更為與 **Length** 屬性相同的值。 若將 **Length** 屬性的值設成小於目前 **StringBuilder** 內字串長度的值，則會縮短該字串。  
  
## <a name="modifying-the-stringbuilder-string"></a>修改 StringBuilder 字串  
 下表列出您可用來修改 **StringBuilder** 內容的方法。  
  
|方法名稱|使用|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|將資訊附加至目前 **StringBuilder** 的結尾。|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|將字串中傳遞的格式規範取代為格式化的文字。|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|將字串或物件插入目前 **StringBuilder** 的指定索引。|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|從目前 **StringBuilder** 移除指定的字元數。|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|取代指定索引處的指定字元。|  
  
### <a name="append"></a>附加  
 **Append** 方法可以用來將物件的文字或字串表示加入至目前 **StringBuilder** 所代表的字串結尾。 下列範例會將 **StringBuilder** 初始化為 "Hello World"，然後附加一些文字到物件的結尾。 會視需要自動配置空格。  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> 方法會將文字加入至 <xref:System.Text.StringBuilder> 物件的結尾。 它藉由呼叫要格式化之一或多個物件的 <xref:System.IFormattable> 實作，來支援複合格式功能 (如需詳細資訊，請參閱[複合格式](../../../docs/standard/base-types/composite-formatting.md))。 因此，它接受數值、日期和時間，以及列舉值的標準格式字串，數值及日期和時間的自訂格式字串，以及為自訂類型定義的格式字串。 (如需格式設定的資訊，請參閱[格式化類型](../../../docs/standard/base-types/formatting-types.md)。)您可以使用這個方法來自訂變數格式，並將那些值附加到 <xref:System.Text.StringBuilder>。 下列範例使用 <xref:System.Text.StringBuilder.AppendFormat%2A> 方法，將格式化為貨幣值的整數值放到 <xref:System.Text.StringBuilder> 物件的結尾。  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 <xref:System.Text.StringBuilder.Insert%2A> 方法會將字串或物件加入至目前 <xref:System.Text.StringBuilder> 物件中的指定位置。 下列範例會使用這個方法，在 <xref:System.Text.StringBuilder> 物件的第六個位置插入一個字組。  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>移除  
 您可以使用 **Remove** 方法，從目前 <xref:System.Text.StringBuilder> 物件移除指定的字元數 (從指定之以零為基礎的索引開始)。 下列範例會使用 **Remove** 方法來縮短 <xref:System.Text.StringBuilder> 物件。  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>取代  
 **Replace** 方法可以用來將 <xref:System.Text.StringBuilder> 物件內的字元取代為另一個指定的字元。 下列範例會使用 **Replace** 方法，來搜尋 <xref:System.Text.StringBuilder> 物件中所有的驚嘆號字元 (!) 執行個體，並取代為問號字元 (?)。  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>將 StringBuilder 物件轉換為字串  
 您必須先將 <xref:System.Text.StringBuilder> 物件轉換成 <xref:System.String> 物件，才能將 <xref:System.Text.StringBuilder> 物件所代表的字串傳遞給具有 <xref:System.String> 參數的方法，或在使用者介面中加以顯示。 您可以呼叫 <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法來執行這項轉換。 下列範例會呼叫一些 <xref:System.Text.StringBuilder> 方法，然後呼叫 <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> 方法來顯示字串。  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
- [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)  
- [格式化類型](../../../docs/standard/base-types/formatting-types.md)
