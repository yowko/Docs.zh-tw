---
title: "在.NET 中使用 StringBuilder 類別"
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
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a6c8f6dee9f2a1da6ed4a8219c1b4832464d9aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a>在.NET 中使用 StringBuilder 類別
<xref:System.String>物件是不可變。 每次您使用其中一種方法在<xref:System.String?displayProperty=nameWithType>類別，您建立新的字串物件在記憶體中，這需要為這個新物件的新配置的空間。 建立新的在您要重複修改字串的情況下，關聯的額外負荷<xref:System.String>物件可能會很費時。 <xref:System.Text.StringBuilder?displayProperty=nameWithType>當您想要修改字串，而不需要建立新的物件時，可以使用類別。 例如，使用<xref:System.Text.StringBuilder>串連在一起在迴圈中的許多字串時，類別可以提升效能。  
  
## <a name="importing-the-systemtext-namespace"></a>匯入 System.Text 命名空間  
 <xref:System.Text.StringBuilder>類別位於<xref:System.Text>命名空間。  若要避免提供程式碼中的完整限定的類型名稱，您可以匯入<xref:System.Text>命名空間：  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>具現化 StringBuilder 物件  
 您可以建立的新執行個體<xref:System.Text.StringBuilder>類別的其中一個多載建構函式方法，初始化變數，如下列範例所示。  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>設定容量和長度  
 雖然<xref:System.Text.StringBuilder>是動態的物件可讓您擴展它封裝時，字串中的字元數，您可以指定它能容納的字元的數目上限的值。 這個值會呼叫物件的容量，而且不應該與字串長度混淆，目前<xref:System.Text.StringBuilder>保存。 例如，您可以建立的新執行個體<xref:System.Text.StringBuilder>類別與字串"Hello"，其長度為 5，而且您可能會指定物件是否具有最大容量為 25。 當您修改<xref:System.Text.StringBuilder>，它不會重新配置大小本身直到到達此容量。 發生這種情況時，會自動配置新的空間，而且容量加倍。 您可以指定的容量<xref:System.Text.StringBuilder>類別使用其中一種多載建構函式。 下列範例會指定 `MyStringBuilder` 物件可以擴展到最多 25 個空格。  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 此外，您可以使用讀取/寫入<xref:System.Text.StringBuilder.Capacity%2A>屬性來設定物件的最大長度。 下列範例會使用 **Capacity** 屬性來定義物件長度上限。  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A>方法可以用來檢查目前的容量**StringBuilder**。 如果容量大於傳遞的值，不會進行任何變更。不過，如果容量小於傳遞的值，會變更目前的容量以符合傳遞的值。  
  
 <xref:System.Text.StringBuilder.Length%2A>屬性也可以檢視或設定。 如果您將 **Length** 屬性的值設成大於 **Capacity** 屬性的值，則 **Capacity** 屬性會自動變更為與 **Length** 屬性相同的值。 若將 **Length** 屬性的值設成小於目前 **StringBuilder** 內字串長度的值，則會縮短該字串。  
  
## <a name="modifying-the-stringbuilder-string"></a>修改 StringBuilder 字串  
 下表列出您可用來修改 **StringBuilder** 內容的方法。  
  
|方法名稱|用法|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|將資訊附加至目前 **StringBuilder** 的結尾。|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|將字串中傳遞的格式規範取代為格式化的文字。|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|將字串或物件插入目前 **StringBuilder** 的指定索引。|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|從目前 **StringBuilder** 移除指定的字元數。|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|取代指定索引處的指定字元。|  
  
### <a name="append"></a>附加  
 **附加**方法可以用來加入代表由目前的字串結尾的文字或物件的字串表示**StringBuilder**。 下列範例會將 **StringBuilder** 初始化為 "Hello World"，然後附加一些文字到物件的結尾。 會視需要自動配置空格。  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>方法將文字加入結尾<xref:System.Text.StringBuilder>物件。 它支援複合格式功能 (如需詳細資訊，請參閱[複合格式化](../../../docs/standard/base-types/composite-formatting.md)) 藉由呼叫<xref:System.IFormattable>實作或多個要格式化的物件。 因此，它接受數值、日期和時間，以及列舉值的標準格式字串，數值及日期和時間的自訂格式字串，以及為自訂類型定義的格式字串。 (如需格式設定的資訊，請參閱[格式化類型](../../../docs/standard/base-types/formatting-types.md)。)您可以使用這個方法，自訂變數的格式，並將那些值來附加<xref:System.Text.StringBuilder>。 下列範例會使用<xref:System.Text.StringBuilder.AppendFormat%2A>方法，將整數值格式化為貨幣值的結尾<xref:System.Text.StringBuilder>物件。  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 <xref:System.Text.StringBuilder.Insert%2A>方法會將字串或物件中目前指定的位置加入<xref:System.Text.StringBuilder>物件。 下列範例會使用這個方法的第六個位置中插入一個字<xref:System.Text.StringBuilder>物件。  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>移除  
 您可以使用**移除**方法來移除指定的字元數，從目前<xref:System.Text.StringBuilder>物件，指定以零為起始的索引處開始。 下列範例會使用**移除**方法來縮短<xref:System.Text.StringBuilder>物件。  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>取代  
 **取代**方法可以用來取代內的字元<xref:System.Text.StringBuilder>物件與另一個指定的字元。 下列範例會使用**取代**方法來搜尋<xref:System.Text.StringBuilder>物件的所有執行個體的驚嘆號字元 （！），並取代為問號字元 （？）。  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>將 StringBuilder 物件轉換為字串  
 您必須將轉換<xref:System.Text.StringBuilder>物件<xref:System.String>物件之前，您可以傳遞所代表的字串<xref:System.Text.StringBuilder>方法，該方法的物件<xref:System.String>參數或將它顯示在使用者介面。 您執行這項轉換，藉由呼叫<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>方法。 下列範例會呼叫數<xref:System.Text.StringBuilder>方法，然後呼叫<xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType>顯示字串的方法。  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)
