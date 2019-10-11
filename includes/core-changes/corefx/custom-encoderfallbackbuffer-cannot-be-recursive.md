---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237313"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>自訂 EncoderFallbackBuffer 實例無法遞迴切換

自訂 <xref:System.Text.EncoderFallbackBuffer> 實例無法以遞迴方式回復。 @No__t-0 的執行必須產生可轉換成目的地編碼的字元序列。 否則，就會發生例外狀況。

#### <a name="change-description"></a>變更描述

在字元對位元組轉碼作業期間，執行時間會偵測格式不正確或 nonconvertible 的 UTF-16 序列，並將這些字元提供給 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法。 @No__t-0 方法會決定哪些字元應取代為原始的 nonconvertible 資料，而這些字元會藉由在迴圈中呼叫 <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 而耗盡。

然後執行時間會嘗試將這些替代字元轉碼到目標編碼。 如果這項作業成功，執行時間會從原始輸入字串中停止的位置繼續轉碼。

在 .NET Core Preview 7 和更早版本中，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的自訂執行可能會傳回無法轉換成目的地編碼的字元序列。 如果替代字元無法轉碼到目標編碼，執行時間就會再次使用替代字元叫用 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法一次，並預期 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 方法傳回新的替代序列。 此程式會繼續進行，直到執行時間最終看到格式正確、可轉換的替代，或直到達到最大遞迴計數為止。

從 .NET Core 3.0 開始，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 的自訂執行必須傳回可轉換成目的地編碼的字元序列。 如果替代字元無法轉碼到目標編碼，則會擲回 @no__t 0。 執行時間不會再對 <xref:System.Text.EncoderFallbackBuffer> 實例進行遞迴呼叫。

只有在符合下列三個條件時，才會套用此行為：

- 執行時間會偵測格式不正確的 UTF-16 序列或 UTF-16 序列，而無法轉換成目標編碼。
- 已指定自訂 <xref:System.Text.EncoderFallback>。
- 自訂 <xref:System.Text.EncoderFallback> 會嘗試取代新格式不正確或 nonconvertible 的 UTF-16 序列。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的開發人員都不需要採取任何動作。

如果應用程式使用自訂的 <xref:System.Text.EncoderFallback> 和 @no__t 1 類別，請確定 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 會將正確格式的 UTF-16 資料填入回溯緩衝區，而當第一次叫用 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> 方法時，會直接轉換成目標編碼運行.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
