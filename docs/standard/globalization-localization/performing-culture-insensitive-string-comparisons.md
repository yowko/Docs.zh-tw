---
title: 執行不區分文化特性的字串比較
ms.date: 08/22/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b68d079413168b042412a67e8732e8afed66ffa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915883"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>執行不區分文化特性的字串比較
根據預設，<xref:System.String.Compare%2A?displayProperty=nameWithType> 方法會執行區分文化特性和區分大小寫的比較。 這個方法也包含幾個多載，這些多載會提供 `culture` 參數 (讓您指定要使用的文化特性) 及 `comparisonType` 參數 (讓您指定要使用的比較規則)。 呼叫這些方法 (而不是預設多載) 會消除有關特定方法呼叫中使用之規則的任何模稜兩可情況，而且可以釐清特定比較是否區分文化特性。  
  
> [!NOTE]
> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法的兩個多載都會執行區分文化特性和區分大小寫的比較，您不能使用這個方法來執行不區分文化特性的比較。 為了讓程式碼更清楚，我們建議您改用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法。  
  
 若要進行區分文化特性作業，請指定 <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> 或 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 列舉值當做 `comparisonType` 參數。 如果您想要使用目前文化特性以外的指定文化特性來執行區分文化特性的比較，請指定代表該文化特性的 <xref:System.Globalization.CultureInfo> 物件當做 `culture` 參數。  
  
 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法支援的不區分文化特性的字串比較為語言式 (根據不因國別而異的文化特性排序慣例) 或是非語言式 (根據字串中字元的序數值)。 大多數不區分文化特性的字串比較都是非語言式。 若要進行這些比較，請指定 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 列舉值當做 `comparisonType` 參數。 例如，如果安全性決策 (例如使用者名稱或密碼比較) 是依據字串比較的結果，此作業應該不區分文化特性而且為非語言式，以確保結果不受特定文化特性或語言的慣例所影響  
  
 如果您想要以一致的方式處理多個文化特性中語言相關的字串，請使用不區分文化特性的語言字串比較。 例如，如果應用程式顯示的字詞會使用清單方塊中的多個字元集，您可能會想要以相同的順序顯示字詞，不論目前的文化特性為何。 如果是不區分文化特性的語言比較，.NET Framework 會定義以英文語言慣例為基礎的不因國別而異的文化特性。 若要執行不區分文化特性的語言作業，請指定 <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> 或 <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> 當做 `comparisonType` 參數。  
  
 下列範例執行兩個不區分文化特性的非語言式字串比較。 第一個比較區分大小寫，第二個比較則不區分。  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

您可以下載[排序權數資料表](https://www.microsoft.com/download/details.aspx?id=10921)，該文字檔集合包含在 Windows 作業系統排序及比較作業中使用的字元權數資訊，以及下載[預設 Unicode 定序元素資料表](https://www.unicode.org/Public/UCA/latest/allkeys.txt) (適用於 Linux 和 macOS 的排序權數資料表)。

## <a name="see-also"></a>另請參閱

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)
