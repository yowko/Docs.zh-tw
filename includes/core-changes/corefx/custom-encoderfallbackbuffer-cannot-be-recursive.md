---
ms.openlocfilehash: 4075eadf7cfb39c913b7657d43335bae5497deff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217049"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>自訂 EncoderFallbackBuffer 實例無法遞迴切換

自<xref:System.Text.EncoderFallbackBuffer>定義實例無法以遞迴方式回復。 的執行<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>必須產生可轉換成目的地編碼的字元序列。 否則，就會發生例外狀況。

#### <a name="details"></a>詳細資料

在字元對位元組轉碼作業期間，執行時間會偵測格式不正確或 nonconvertible 的<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> utf-16 序列，並將這些字元提供給方法。 方法會決定哪些字元應該取代為原始的 nonconvertible 資料，而這些字元會藉由在迴圈<xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType>中呼叫而耗盡。 `Fallback`

然後執行時間會嘗試將這些替代字元轉碼到目標編碼。 如果這項作業成功，執行時間會從原始輸入字串中停止的位置繼續轉碼。

在 .net Core Preview 7 和更早版本中，的<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>自訂執行可能會傳回無法轉換成目的地編碼的字元序列。 如果替代字元無法轉碼到目標編碼，運行<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>時間就會使用替代字元再次叫用方法一次，而此<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>方法必須傳回新的替代序列。 此程式會繼續進行，直到執行時間最終看到格式正確、可轉換的替代，或直到達到最大遞迴計數為止。

從 .net Core 3.0 開始，自訂的<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>執行必須傳回可轉換成目的地編碼的字元序列。 如果替代字元無法轉碼到目標編碼， <xref:System.ArgumentException>則會擲回。 執行時間不會再對<xref:System.Text.EncoderFallbackBuffer>實例進行遞迴呼叫。

只有在符合下列三個條件時，才會套用此行為：

- 執行時間會偵測格式不正確的 UTF-16 序列或 UTF-16 序列，而無法轉換成目標編碼。
- 已指定<xref:System.Text.EncoderFallback>自訂。
- 自訂<xref:System.Text.EncoderFallback>會嘗試取代新格式不正確或 nonconvertible 的 utf-16 序列。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的開發人員都不需要採取任何動作。

如果應用程式使用自訂<xref:System.Text.EncoderFallback>的<xref:System.Text.EncoderFallbackBuffer>和類別<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ，請確定以正確格式的 utf-16 資料填入回溯緩衝區，此<xref:System.Text.EncoderFallbackBuffer.Fallback%2A>方法會在方法執行時直接轉換成目標編碼是由執行時間第一次叫用。

#### <a name="category"></a>分類

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
