---
title: 在 .NET 中比較字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET Framework], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c925b734c6d89bfa7240a7946c5bae4d8062a47a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577813"
---
# <a name="comparing-strings-in-net"></a>在 .NET 中比較字串
.NET 會提供數種方法來比較字串值。 下表列出並描述數值比較的方法。  
  
|方法名稱|使用|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|比較兩個字串的值。 傳回整數值。|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|比較兩個字串，而不考慮當地文化特性。 傳回整數值。|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|比較目前字串物件與另一個字串。 傳回整數值。|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|判斷字串是否以傳遞的字串開頭。 傳回布林值。|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|判斷字串是否以傳遞的字串結束。 傳回布林值。|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|判斷兩個字串是否相同。 傳回布林值。|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|從您正在檢查之字串的開頭開始，傳回字元或字串的索引位置。 傳回整數值。|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|從您正在檢查之字串的結尾開始，傳回字元或字串的索引位置。 傳回整數值。|  
  
## <a name="compare"></a>比較  
 靜態 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法提供全面的方式來比較兩個字串。 該方法會感知文化特性。 您可以使用這個函式來比較兩個字串或兩個字串的子字串。 此外，會假定多載為考慮或是忽略大小寫和文化特性變異數。 下表顯示這個方法可能會傳回的三個整數值。  
  
|傳回值|條件|  
|------------------|---------------|  
|負整數|在此排序次序中，第一個字串優先於第二個字串。<br /><br /> -或-<br /><br /> 第一個字串是 `null`。|  
|0|第一個字串和第二個字串相等。<br /><br /> -或-<br /><br /> 這兩個字串都是 `null`。|  
|正整數<br /><br /> -或-<br /><br /> 1|在此排序次序中，第一個字串在第二個字串的後面。<br /><br /> -或-<br /><br /> 第二個字串是 `null`。|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。 您不應該使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。  
  
 下列範例會使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法，以判斷兩個字串的相對值。  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 此範例會顯示 `-1` 至主控台。  
  
 上述範例根據預設會區分文化特性。 若要執行不區分文化特性的字串比較，使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法的多載，可讓您藉由提供「文化特性」參數來指定要使用的文化特性。 如需示範如何使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法以執行不區分文化特性比較的範例，請參閱[執行不區分文化特性的字串比較](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)。  
  
## <a name="compareordinal"></a>CompareOrdinal  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法會比較兩個字串物件，而不考慮當地文化特性。 這個方法的傳回值與上表中 **比較** 方法所傳回的值相同。  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。 您不應該使用 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。  
  
 下列範例會使用 **CompareOrdinal** 方法，以判斷兩個字串的值。  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 此範例會顯示 `-32` 至主控台。  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法會比較目前字串物件封裝到另一個字串或物件中的字串。 這個方法的傳回值與上表中 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法所傳回的值相同。  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。 您不應該使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。  
  
 下列範例會使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來比較 `string1` 物件和 `string2` 物件。  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 此範例會顯示 `-1` 至主控台。  
  
 根據預設，<xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法的所有多載都會執行區分文化特性和區分大小寫的比較。 此方法不提供可讓您執行不區分文化特性比較的多載。 為了讓程式碼更清楚，建議您改用 **String.Compare** 方法，對於區分文化特性的作業指定 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>，或對於不區分文化特性的作業指定 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。 如需範例示範如何使用 **String.Compare** 方法以執行區分文化特性和不區分文化特性的比較，請參閱 [執行不區分文化特性的字串比較](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)。  
  
## <a name="equals"></a>等於  
 **String.Equals** 方法可以輕易地判斷兩個字串是否相同。 這個區分大小寫的方法會傳回 **true** 或 **false** 布林值。 它可從現有的類別下使用，如下一個範例中所示。 下列範例會使用 **等於** 方法來判斷字串物件是否包含片語 "Hello World"。  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 此範例會顯示 `True` 至主控台。  
  
 這個方法也可用做為靜態方法。 下列範例會使用靜態方法來比較兩個字串物件。  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 此範例會顯示 `True` 至主控台。  
  
## <a name="startswith-and-endswith"></a>StartsWith 和 EndsWith  
 您可以使用 **String.StartsWith** 方法來判斷字串物件開頭是否為包含另一個字串的相同字元。 如果目前字串物件的開頭為傳遞的字串，則這個區分大小寫的方法會傳回 **true** ，否則為 **false** 。 下列範例會使用這個方法，以判斷字串物件開頭是否為 "Hello"。  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 此範例會顯示 `True` 至主控台。  
  
 **String.EndsWith** 方法會比較傳遞的字串和目前字串物件結尾上存在的字元。 它也會傳回布林值。 下列範例會使用 **EndsWith** 方法檢查字串結尾。  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 此範例會顯示 `False` 至主控台。  
  
## <a name="indexof-and-lastindexof"></a>IndexOf 和 LastIndexOf  
 您可以使用 **String.IndexOf** 方法，以判斷字串中第一次出現特定字元的位置。 這個區分大小寫的方法從字串開頭開始算起，並使用以零為起始的索引傳回傳遞字元的位置。 如果找不到該字元，則會傳回 –1 的值。  
  
 下列範例會使用 **IndexOf** 方法在字串中搜尋 '`l`' 字元的第一次出現。  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 此範例會顯示 `2` 至主控台。  
  
 **String.LastIndexOf** 方法類似 **String.IndexOf** 方法，只是它會傳回字串內特定字元最後一次出現的位置。 它會區分大小寫，並使用以零為起始的索引。  
  
 下列範例會使用 **LastIndexOf** 方法在字串中搜尋 '`l`' 字元的最後一次出現。  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 此範例會顯示 `9` 至主控台。  
  
 當搭配 **String.Remove** 方法使用時，這兩種方法都很實用。 您可以使用 **IndexOf** 或 **LastIndexOf** 方法來擷取字元的位置，然後提供該位置給 **移除** 方法，以移除字元或以該字元開頭的單字。  
  
## <a name="see-also"></a>請參閱  
 [基本字串作業](../../../docs/standard/base-types/basic-string-operations.md)  
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
