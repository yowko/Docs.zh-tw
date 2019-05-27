---
title: 在 .NET 中建立新字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50750b23af9e9cfca79b0f7db9d272e8e24971ab
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591409"
---
# <a name="creating-new-strings-in-net"></a>在 .NET 中建立新字串
.NET Framework 允許使用簡單指派來建立字串，且還可以多載類別建構函式，支援使用多個不同參數來建立字串。 .NET Framework 也在 <xref:System.String?displayProperty=nameWithType> 類別中提供數個方法，藉由合併數個字串、字串陣列或物件來建立新的字串物件。  
  
## <a name="creating-strings-using-assignment"></a>使用指派建立字串  
 建立新 <xref:System.String> 物件的最簡單方式，就是將字串常值指派給 <xref:System.String> 物件。  
  
## <a name="creating-strings-using-a-class-constructor"></a>使用類別建構函式建立字串  
 您可以使用 <xref:System.String> 類別建構函式的多載，從字元陣列建立字串。 您也可以讓某個特定字元重複指定的次數，藉此建立新字串。  
  
## <a name="methods-that-return-strings"></a>傳回字串的方法  
 下表列出數個可傳回新字串物件的有用方法。  
  
|方法名稱|使用|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|從一組輸入物件建立格式化的字串。|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|從兩個或多個字串建立字串。|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|藉由組合字串陣列來建立新字串。|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|藉由將字串插入現有字串的指定索引中來建立新字串。|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|將字串中的指定字元複製到字元陣列中的指定位置。|  
  
### <a name="format"></a>格式  
 您可以使用 **String.Format** 方法，來建立格式化的字串和串連代表多個物件的字串。 這個方法會自動將任何傳遞的物件轉換為字串。 例如，如果您的應用程式必須向使用者顯示 **Int32** 值和 **DateTime** 值，您可以使用 **Format** 方法，輕鬆地建構代表這些值的字串。 如需搭配此方法使用之格式慣例的資訊，請參閱[複合格式](../../../docs/standard/base-types/composite-formatting.md)一節。  
  
 下列範例會使用 **Format** 方法來建立使用整數變數的字串。  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 在此範例中，<xref:System.DateTime.Now%2A?displayProperty=nameWithType> 會以和目前執行緒相關聯之文化特性所指定的方式來顯示目前的日期和時間。  
  
### <a name="concat"></a>Concat  
 使用 **String.Concat** 方法，可輕鬆地從兩個或多個現有物件建立新的字串物件。 它提供與語言無關的方式來串連字串。 這個方法接受任何衍生自 **System.Object** 的類別。 下列範例會從現有的兩個字串物件和一個分隔字元建立字串。  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 **String.Join** 方法會從字串陣列和分隔符號字串建立新的字串。 如果您想要將多個字串串連在一起，建立以逗號分隔的清單，這個方法會很有用。  
  
 下列範例會使用空格來繫結字串陣列。  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 **String.Insert** 方法會將字串插入另一個字串中的指定位置，藉以建立新的字串。 這個方法會使用以零起始的索引。 下列範例會將字串插入 `MyString` 的第五個索引位置，並使用這個值來建立新的字串。  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** 方法會將部分字串複製到字元陣列中。 您可以同時指定字串的開頭索引和要複製的字元數。 這個方法會使用來源索引、字元陣列、目的索引和要複製的字元數。 所有索引都是以零起始。  
  
 下列範例會使用 **CopyTo** 方法，將 "Hello" 這個字的所有字元從字串物件複製到字元陣列的第一個索引位置。  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)
- [複合格式](../../../docs/standard/base-types/composite-formatting.md)
