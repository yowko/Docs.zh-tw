---
title: 如何：比較字串 - C# 手冊
description: 了解如何比較和排序字串值，不論大小寫、不論文化特性特定的順序
ms.date: 03/20/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: 3c841a1152613ec877bb6172dc8d053bf060b33b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484098"
---
# <a name="how-to-compare-strings-in-c"></a>如何：在 C\# 比較字串

比較字串來回答兩個問題的其中一個：「這兩個字串相等嗎？」 或「這些字串在排序時應該以何種順序放置？」

這兩個問題會因為影響字串比較的因素而變複雜：

- 您可以選擇序數或語言比較。
- 您可以選擇大小寫是否重要。
- 您可以選擇文化特性特定的比較。
- 語言比較會相依於文化特性和平台。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

當您比較字串時，您會定義它們之間的順序。 比較用來排序字串的序列。 一旦序列是已知的順序，軟體和人類都能比較容易搜尋。 其他的比較可能會檢查字串是否相同。 這些相同性檢查類似於相等，但可能會忽略部分差異，例如大小寫的差異。

## <a name="default-ordinal-comparisons"></a>預設的序數比較

最常見的作業，<xref:System.String.CompareTo%2A?displayProperty=nameWithType> 和 <xref:System.String.Equals%2A?displayProperty=nameWithType> 或 <xref:System.String.op_Equality%2A?displayProperty=nameWithType> 使用序數比較、區分大小寫的比較，並使用目前文化特性。 下列範例將顯示結果。

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

序數比較在比較字串時不會考慮語言規則。 它們會逐字元地比較字串。 區分大小寫的比較會在其比較中使用大小寫。 有關這些預設比較方法最重要的一點是，因為它們會使用目前的文化特性，所以結果取決於它們執行所在電腦的地區設定和語言設定。 這些比較不適合於比較順序應該跨電腦或位置保持一致的比較情況。

## <a name="case-insensitive-ordinal-comparisons"></a>不區分大小寫的序數比較

<xref:System.String.Equals%2A?displayProperty=nameWithType> 方法可讓您指定 <xref:System.StringComparison> 值 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>，
指定不區分大小寫的比較。 也有靜態 <xref:System.String.Compare%2A> 方法，包含布林值的引數來指定不區分大小寫的比較。 如下列程式碼所示：

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

## <a name="linguistic-comparisons"></a>語言比較

字串也可以使用目前文化特性的語言規則來排序。
這有時候稱為「字組排序次序」。 當您執行語言比較時，部分非英數字元的 Unicode 字元可能會被指派特殊的權重。 例如，連字號 "-" 可能會被指派很小的權重，以便 "co-op" 和 "coop" 在排序次序中會出現在彼此旁邊。 此外，某些 Unicode 字元可能會相當於一連串的英數字元。 下列範例使用該片語 "They dance in the street"。 具有德文的 "ss" 和 'ß'。 在語言方面 (在 Windows 中)，"ss" 等於 "en-US" 和 "de-DE" 文化特性中的德文 Essetz: 'β' 字元。

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

這個範例會示範語言比較相依於作業系統的本質。 互動式視窗的主機是 Linux 主機。 語言和序數比較會產生相同的結果。 如果您在 Windows 主機上執行相同的範例，您會看到下列輸出：

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

在 Windows 上，"cop"、"coop" 和 "co-op" 的排序次序會在您從語言比較變更為序數比較時改變。 兩個德文句子使用不同的比較型別時，比較起來也會不同。

## <a name="comparisons-using-specific-cultures"></a>使用特定文化特性的比較

這個範例會儲存目前文化特性的 <xref:System.Globalization.CultureInfo>。
可以在目前的執行緒物件上設定及擷取原始的文化特性。 比較是使用 <xref:System.StringComparison.CurrentCulture> 值執行，以確保特定文化特性的比較。

使用的文化特性會影響語言比較。 下列範例會顯示使用 "en-US" 文化特性和 "de-DE" 文化特性比較兩個德文句子的結果：

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

文化特性敏感的比較通常用來比較和排序使用者輸入的字串與使用者輸入的其他字串。 這些字串的字元和排序慣例可能會視使用者電腦的地區設定而變。 即使包含完全相同字元的字串，也可能因目前執行緒的文化特性而改變排序。 此外，在 Windows 電腦上本機嘗試此範例程式碼，會產生下列結果：

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

語言比較相依於目前的文化特性以及 OS。 當您使用字串比較時必須考量此點。

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>陣列中的語言排序和字串搜尋

下列範例顯示如何使用相依於目前文化特性的語言比較，在陣列中排序和搜尋字串。 請使用接受 <xref:System.StringComparer?displayProperty=nameWithType> 參數的靜態 <xref:System.Array> 方法。

此範例顯示如何使用目前文化特性來排序字串陣列：

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

陣列排序之後，您可以使用二進位搜尋來搜尋項目。 二進位搜尋會從集合的中間開始，判斷集合的哪一半會包含搜尋的字串。 每次後續的比較都會將集合的剩餘部分再對分。  陣列是使用 <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType> 排序。 區域函式 `ShowWhere` 會顯示找到字串處的相關資訊。 如果找不到字串，則傳回的值會指出如果找到的話它會是在哪裡。

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>集合中的序數排序和搜尋

下列程式碼會使用 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 集合類別來儲存字串。 字串是使用 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 方法排序。 這個方法需要可比較和排序兩個字串的委派。 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法提供該比較函式。 執行範例，並觀察順序。 此排序作業會使用序數區分大小寫排序。 您可以使用靜態 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法來指定不同的比較規則。

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

排序之後，便可以使用二進位搜尋來搜尋字串清單。 下列範例會示範如何使用相同的比較函式搜尋已排序的清單。 區域函式 `ShowWhere` 顯示搜尋的文字在哪裡或是會在哪裡：

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

請務必使用相同型別的比較來排序和搜尋。 使用不同的比較型別來排序和搜尋，會產生非預期的結果。

項目或索引鍵的類型為 `string` 時，<xref:System.Collections.Hashtable?displayProperty=nameWithType>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 這類集合類別具有接受 <xref:System.StringComparer?displayProperty=nameWithType> 參數的建構函式。 通常應該盡可能使用這些建構函式，並指定 <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>。

## <a name="reference-equality-and-string-interning"></a>參考相等與字串暫留

沒有任何範例使用 <xref:System.Object.ReferenceEquals%2A>。 這個方法會判斷兩個字串是否相同的物件。 這可能會導致不一致的字串比較結果。 下列範例示範 C# 的「字串暫留」功能。 當程式宣告兩個或多個相同的字串變數時，編譯器會將它們全部儲存在相同的位置。 藉由呼叫 <xref:System.Object.ReferenceEquals%2A> 方法，您會看到兩個字串實際上參考記憶體中的相同物件。 請使用 <xref:System.String.Copy%2A?displayProperty=nameWithType> 方法以避免暫留。 複製完成後，兩個字串會有不同的儲存位置，即使它們有相同的值。 執行下列範例以顯示字串 `a` 和 `b` 已「暫留」，也就是說它們共用相同的存放裝置。 字串 `a` 和 `c` 則否。

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> 當您測試字串是否相等時，您應該使用明確指定打算執行比較型別的方法。 您的程式碼會更容易維護及閱讀。 請使用 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Array?displayProperty=nameWithType> 類別的方法多載，接受 <xref:System.StringComparison> 列舉參數。 您指定要執行的比較型別。 測試是否相等時，請避免使用 `==` 和 `!=` 運算子。 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 執行個體方法一律會執行區分大小寫的序數比較。 它們主要適用於依字母順序排序字串。

## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
- <xref:System.StringComparer?displayProperty=nameWithType>  
- [字串](../programming-guide/strings/index.md)  
- [比較字串](../../standard/base-types/comparing.md)  
- [全球化和當地語系化應用程式](/visualstudio/ide/globalizing-and-localizing-applications)
