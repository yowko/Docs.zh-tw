---
title: 標準 TimeSpan 格式字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, standard time interval
- format strings
- standard time interval format strings
- standard format strings, time intervals
- format specifiers, time intervals
- time intervals [.NET Framework], formatting
- time [.NET Framework], formatting
- formatting [.NET Framework], time
- standard TimeSpan format strings
- formatting [.NET Framework], time intervals
ms.assetid: 9f6c95eb-63ae-4dcc-9c32-f81985c75794
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52da538ba9cf348062905b66a87d13db82a214a0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085258"
---
# <a name="standard-timespan-format-strings"></a>標準 TimeSpan 格式字串
<a name="Top"></a> 標準 <xref:System.TimeSpan> 格式字串會使用單一格式規範，來定義從格式化作業所產生之 <xref:System.TimeSpan> 值的文字表示。 任何包含一個以上字元 (包含空格) 的格式字串，都會解譯為自訂 <xref:System.TimeSpan> 格式字串。 如需詳細資訊，請參閱[自訂 TimeSpan 格式字串](../../../docs/standard/base-types/custom-timespan-format-strings.md)。  
  
 <xref:System.TimeSpan> 值的字串表示，藉由呼叫 <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> 方法的多載而產生，同時也可藉由支援複合格式化的方法所產生，例如 <xref:System.String.Format%2A?displayProperty=nameWithType>。 如需詳細資訊，請參閱[格式化類型](../../../docs/standard/base-types/formatting-types.md)和[複合格式設定](../../../docs/standard/base-types/composite-formatting.md)。 下列範例說明格式化作業中的標準格式字串用法。  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 <xref:System.TimeSpan> 和 <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> 方法也會使用標準 <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> 格式字串，以定義剖析作業之輸入字串的必要格式 (剖析會將值的字串表示轉換成該值)。下列範例說明剖析作業中標準格式字串的用法。  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a>下表列出標準時間間隔格式規範。  
  
|格式規範|名稱|描述|範例|  
|----------------------|----------|-----------------|--------------|  
|"c"|常數 (非變異) 格式|這個規範不區分文化特性。 它採用 `[-][d’.’]hh’:’mm’:’ss[‘.’fffffff]` 格式<br /><br /> \ ("t" 與 "T" 格式字串會產生相同的結果)。<br /><br /> 詳細資訊：[常數 ("c") 格式規範](#Constant)。|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|一般短格式|這個規範只會輸出需要的內容。 它會區分文化特性，並採用 `[-][d’:’]h’:’mm’:’ss[.FFFFFFF]` 格式。<br /><br /> 詳細資訊：[一般短 ("g") 格式規範](#GeneralShort)。|`New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50,5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:500.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:500.599 (fr-FR)|  
|"G"|一般長格式|這個規範一律會輸出天數和七個小數。 它會區分文化特性，並採用 `[-]d’:’hh’:’mm’:’ss.fffffff` 格式。<br /><br /> 詳細資訊：[一般長 ("G") 格式規範](#GeneralLong)。|`New TimeSpan(18, 30, 0)` -> 0:18:30:00.0000000 (en-US)<br /><br /> `New TimeSpan(18, 30, 0)` -> 0:18:30:00,0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>常數 ("c") 格式規範  
 "c" 格式規範會以下列形式傳回 <xref:System.TimeSpan> 值的字串表示：  
  
 [-][*d*.]*hh*:*mm*:*ss*[.*fffffff*]  
  
 在方括號 ([ 和 ]) 中的項目是選擇性的項目。 句號 (.) 和冒號 (:) 是常值的符號。 下表說明其餘項目。  
  
|元素|描述|  
|-------------|-----------------|  
|*-*|選擇性的負號，表示負的時間間隔。|  
|*d*|選擇性的天數，沒有前置的零。|  
|*hh*|小時數，範圍從 "00" 到 "23"。|  
|*mm*|分鐘數，範圍從 "00" 到 "59"。|  
|*ss*|秒數，範圍從 "0" 到 "59"。|  
|*fffffff*|秒的選擇性小數部分。  其值的範圍可從 "0000001" (一個刻度或一秒的千萬分之一) 到 "9999999" (一秒的千萬分之 9,999,999，也就是一秒減一個刻度)。|  
  
 與 "g" 和 "G" 格式規範不同，"c" 的格式規範不區分文化特性。 它會產生 <xref:System.TimeSpan> 值的字串表示，而該值是非變異值，且對於 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 之前的所有舊版 .NET Framework 皆通用。 "c" 是預設的 <xref:System.TimeSpan> 格式字串；<xref:System.TimeSpan.ToString?displayProperty=nameWithType> 方法使用 "c" 格式字串來將時間間隔值格式化。  
  
> [!NOTE]
>  <xref:System.TimeSpan> 也支援 "t" 和 "T" 標準格式字串，它們的行為與 "c" 標準格式字串相同。  
  
 下列範例會呈現兩個 <xref:System.TimeSpan> 物件，用以執行算術運算，並顯示結果。 在每個案例中，都使用複合格式化，以 "c" 格式規範顯示 <xref:System.TimeSpan> 值。  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [回到表格](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>一般短 ("g") 格式規範  
 "g" <xref:System.TimeSpan> 格式規範會以壓縮形式傳回 <xref:System.TimeSpan> 值的字串表示，而且只包括必要的項目。 其形式如下：  
  
 [-][*d*:]*h*:*mm*:*ss*[.*FFFFFFF*]  
  
 在方括號 ([ 和 ]) 中的項目是選擇性的項目。 冒號 (:) 是常值符號。 下表說明其餘項目。  
  
|元素|描述|  
|-------------|-----------------|  
|*-*|選擇性的負號，表示負的時間間隔。|  
|*d*|選擇性的天數，沒有前置的零。|  
|*h*|小時數，範圍從 "0" 到 "23"，且沒有前置的零。|  
|*mm*|分鐘數，範圍從 "00" 到 "59"。|  
|*ss*|秒數，範圍從 "00" 到 "59"。|  
|*.*|小數的秒數分隔符號。 它相當於指定之文化特性的 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> 屬性，且不會覆寫使用者。|  
|*FFFFFFF*|小數的秒數。 盡可能顯示最少的數字。|  
  
 如同 "G" 格式規範，"g" 格式規範已經過當地語系化。 它的小數秒數分隔符號取決於目前的文化特性或指定之文化特性的 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> 屬性。  
  
 下列範例會呈現兩個 <xref:System.TimeSpan> 物件，用以執行算術運算，並顯示結果。 在每個案例中，都會使用複合格式化，以 "g" 格式規範顯示 <xref:System.TimeSpan> 值。 此外，它會使用目前的系統文化特性 (在此案例中是英文-美國或 en-US) 和法文-法國 (fr-FR) 文化特性的格式化慣例，來格式化 <xref:System.TimeSpan> 值。  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [回到表格](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>一般長 ("G") 格式規範  
 "G" <xref:System.TimeSpan> 格式規範會以長形式傳回 <xref:System.TimeSpan> 值的字串表示，而此形式一律會同時包含日數和小數秒數。 從 "G" 標準格式規範產生的字串具有下列形式：  
  
 [-]*d*:*hh*:*mm*:*ss*.*fffffff*  
  
 在方括號 ([ 和 ]) 中的項目是選擇性的項目。 冒號 (:) 是常值符號。 下表說明其餘項目。  
  
|元素|描述|  
|-------------|-----------------|  
|*-*|選擇性的負號，表示負的時間間隔。|  
|*d*|天數，沒有前置的零。|  
|*hh*|小時數，範圍從 "00" 到 "23"。|  
|*mm*|分鐘數，範圍從 "00" 到 "59"。|  
|*ss*|秒數，範圍從 "00" 到 "59"。|  
|*.*|小數的秒數分隔符號。 它相當於指定之文化特性的 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> 屬性，且不會覆寫使用者。|  
|*fffffff*|小數的秒數。|  
  
 和 "G" 格式規範一樣，"g" 格式規範已經過當地語系化。 它的小數秒數分隔符號取決於目前的文化特性或指定之文化特性的 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> 屬性。  
  
 下列範例會呈現兩個 <xref:System.TimeSpan> 物件，用以執行算術運算，並顯示結果。 在每個案例中，都會使用複合格式化，以 "G" 格式規範顯示 <xref:System.TimeSpan> 值。 此外，它會使用目前的系統文化特性 (在此案例中是英文-美國或 en-US) 和法文-法國 (fr-FR) 文化特性的格式化慣例，來格式化 <xref:System.TimeSpan> 值。  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [回到表格](#Top)  
  
## <a name="see-also"></a>另請參閱

- [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
- [自訂 TimeSpan 格式字串](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
- [剖析字串](../../../docs/standard/base-types/parsing-strings.md)
