---
title: 在 .NET 中比較字串
description: 深入瞭解在 .NET 中比較字串的方法。 瞭解 Compare、CompareOrdinal、CompareTo、StartsWith、EndsWith、Equals、IndexOf & LastIndexOf 方法。
ms.date: 03/30/2017
ms.topic: conceptual
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
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: ca2e89fa8c42807757f4ed004c8f8ddaaeafba3b
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693068"
---
# <a name="compare-strings-in-net"></a>比較 .NET 中的字串

.NET 會提供數種方法來比較字串值。 下表列出並描述數值比較的方法。

|方法名稱|使用|
|-----------------|---------|
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|比較兩個字串的值。 傳回整數值。|
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|比較兩個字串，而不考慮當地文化特性。 傳回整數值。|
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|比較目前字串物件與另一個字串。 傳回整數值。|
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|判斷字串是否以傳遞的字串開頭。 傳回布林值。|
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|判斷字串是否以傳遞的字串結束。 傳回布林值。|
|<xref:System.String.Contains%2A?displayProperty=nameWithType>|判斷字元或字串是否出現在另一個字串內。 傳回布林值。|
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|判斷兩個字串是否相同。 傳回布林值。|
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|從您正在檢查之字串的開頭開始，傳回字元或字串的索引位置。 傳回整數值。|
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|從您正在檢查之字串的結尾開始，傳回字元或字串的索引位置。 傳回整數值。|

## <a name="compare-method"></a>Compare 方法

靜態 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法提供全面的方式來比較兩個字串。 該方法會感知文化特性。 您可以使用這個函式來比較兩個字串或兩個字串的子字串。 此外，會假定多載為考慮或是忽略大小寫和文化特性變異數。 下表顯示這個方法可能會傳回的三個整數值。

|傳回值|條件|
|------------------|---------------|
|負整數|在此排序次序中，第一個字串優先於第二個字串。<br /><br /> -或-<br /><br /> 第一個字串是 `null`。|
|0|第一個字串和第二個字串相等。<br /><br /> -或-<br /><br /> 這兩個字串都是 `null`。|
|正整數<br /><br /> -或-<br /><br /> 1|在此排序次序中，第一個字串在第二個字串的後面。<br /><br /> -或-<br /><br /> 第二個字串是 `null`。|

> [!IMPORTANT]
> <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。 您不應該使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。

 下列範例會使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法，以判斷兩個字串的相對值。

 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]

 此範例會顯示 `-1` 至主控台。

 上述範例根據預設會區分文化特性。 若要執行不區分文化特性的字串比較，使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法的多載，可讓您藉由提供「文化特性」參數來指定要使用的文化特性。 如需示範如何使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法執行不區分文化特性比較的範例，請參閱不 [區分文化特性的字串比較](../globalization-localization/performing-culture-insensitive-string-comparisons.md)。

## <a name="compareordinal-method"></a>CompareOrdinal 方法

<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法會比較兩個字串物件，而不考慮當地文化特性。 這個方法的傳回值與上表中 `Compare` 方法所傳回的值相同。

> [!IMPORTANT]
> <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。 您不應該使用 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。

 下列範例會使用 `CompareOrdinal` 方法來比較兩個字串的值。

 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]

 此範例會顯示 `-32` 至主控台。

## <a name="compareto-method"></a>CompareTo 方法

<xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法會比較目前字串物件封裝到另一個字串或物件中的字串。 這個方法的傳回值與上表中 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法所傳回的值相同。

> [!IMPORTANT]
> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。 您不應該使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。

 下列範例會使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來比較 `string1` 物件和 `string2` 物件。

 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]

 此範例會顯示 `-1` 至主控台。

 根據預設，<xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法的所有多載都會執行區分文化特性和區分大小寫的比較。 此方法不提供可讓您執行不區分文化特性比較的多載。 為了讓程式碼更清楚，建議您改用 `String.Compare` 方法，並指定 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 區分文化特性的作業或不 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 區分文化特性的作業。 如需示範如何使用 `String.Compare` 方法來執行區分文化特性和不區分文化特性比較的範例，請參閱 [執行 Culture-Insensitive 字串比較](../globalization-localization/performing-culture-insensitive-string-comparisons.md)。

## <a name="equals-method"></a>Equals 方法

<xref:System.String.Equals%2A?displayProperty=nameWithType>方法可以輕易地判斷兩個字串是否相同。 這個區分大小寫的方法會傳回 `true` 或 `false` 布林值。 它可從現有的類別下使用，如下一個範例中所示。 下列範例會使用 `Equals` 方法來判斷字串物件是否包含片語 "Hello World"。

 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]

 此範例會顯示 `True` 至主控台。

 這個方法也可用做為靜態方法。 下列範例會使用靜態方法來比較兩個字串物件。

 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]

 此範例會顯示 `True` 至主控台。

## <a name="startswith-and-endswith-methods"></a>StartsWith 和 EndsWith 方法

您可以使用 <xref:System.String.StartsWith%2A?displayProperty=nameWithType> 方法來判斷字串物件開頭是否為包含另一個字串的相同字元。 如果目前字串物件的開頭為傳遞的字串，則這個區分大小寫的方法會傳回 `true`，否則為 `false`。 下列範例會使用這個方法，以判斷字串物件開頭是否為 "Hello"。

 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]

 此範例會顯示 `True` 至主控台。

 <xref:System.String.EndsWith%2A?displayProperty=nameWithType>方法會比較傳遞的字串和目前字串物件結尾的字元。 它也會傳回布林值。 下列範例會使用 `EndsWith` 方法檢查字串結尾。

 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]

 此範例會顯示 `False` 至主控台。

## <a name="indexof-and-lastindexof-methods"></a>IndexOf 和 LastIndexOf 方法

您可以使用 <xref:System.String.IndexOf%2A?displayProperty=nameWithType> 方法來判斷字串中第一次出現特定字元的位置。 這個區分大小寫的方法從字串開頭開始算起，並使用以零為起始的索引傳回傳遞字元的位置。 如果找不到該字元，則會傳回 –1 的值。

下列範例會使用 `IndexOf` 方法在字串中搜尋 '`l`' 的第一次出現位置。

 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]

 此範例會顯示 `2` 至主控台。

 <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>方法與方法類似， `String.IndexOf` 不同之處在于它會傳回字串內特定字元最後一次出現的位置。 它會區分大小寫，並使用以零為起始的索引。

 下列範例會使用 `LastIndexOf` 方法在字串中搜尋 '`l`' 的最後一次出現位置。

 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]

 此範例會顯示 `9` 至主控台。

 搭配方法使用時，這兩種方法都很有用 <xref:System.String.Remove%2A?displayProperty=nameWithType> 。 您可以使用 `IndexOf` 或 `LastIndexOf` 方法來取出字元的位置，然後提供該位置給 `Remove` 方法，以移除字元或以該字元開頭的單字。

## <a name="see-also"></a>另請參閱

- [在 .NET 中使用字串的最佳做法](best-practices-strings.md)
- [基底字元串作業](basic-string-operations.md)
- [執行不區分文化特性的字串作業](../globalization-localization/performing-culture-insensitive-string-operations.md)
- [排序權數資料表](https://www.microsoft.com/download/details.aspx?id=10921) -Windows 上的 .NET FRAMEWORK 和 .net Core 1.0-3.1 使用
- [預設 Unicode 定序元素資料表](https://www.unicode.org/Public/UCA/latest/allkeys.txt) -適用于所有平臺上的 .net 5，以及 Linux 和 macOS 上的 .net Core
