---
ms.openlocfilehash: 00c32c10f77995284264e795d386f699082dcb84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721449"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>自訂 EncoderFallbackBuffer 實例無法遞迴切換

自訂 <xref:System.Text.EncoderFallbackBuffer> 實例無法以遞迴方式回復。 的執行 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 必須產生可轉換成目的地編碼的字元序列。 否則，就會發生例外狀況。

#### <a name="change-description"></a>變更描述

在字元對位元組轉碼作業期間，執行時間會偵測格式不正確或 nonconvertible 的 UTF-16 序列，並將這些字元提供給 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法。 `Fallback`方法會決定哪些字元應該取代為原始的 nonconvertible 資料，而這些字元會藉由 <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 在迴圈中呼叫而耗盡。

然後執行時間會嘗試將這些替代字元轉碼到目標編碼。 如果這項作業成功，執行時間會從原始輸入字串中停止的位置繼續轉碼。

在 .NET Core Preview 7 和更早版本中，的自訂執行 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 可能會傳回無法轉換成目的地編碼的字元序列。 如果替代字元無法轉碼到目標編碼，執行時間就會 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 使用替代字元再次叫用方法一次，而此方法必須傳回 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 新的替代序列。 此程式會繼續進行，直到執行時間最終看到格式正確、可轉換的替代，或直到達到最大遞迴計數為止。

從 .NET Core 3.0 開始，自訂的執行 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 必須傳回可轉換成目的地編碼的字元序列。 如果替代字元無法轉碼到目標編碼，則會擲回 <xref:System.ArgumentException> 。 執行時間不會再對實例進行遞迴呼叫 <xref:System.Text.EncoderFallbackBuffer> 。

只有在符合下列三個條件時，才會套用此行為：

- 執行時間會偵測格式不正確的 UTF-16 序列或 UTF-16 序列，而無法轉換成目標編碼。
- 已指定自訂 <xref:System.Text.EncoderFallback> 。
- 自訂 <xref:System.Text.EncoderFallback> 會嘗試取代新格式不正確或 nonconvertible 的 utf-16 序列。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的開發人員都不需要採取任何動作。

如果應用程式使用自訂的 <xref:System.Text.EncoderFallback> 和 <xref:System.Text.EncoderFallbackBuffer> 類別，請確定在 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> 執行時間第一次叫用方法時，以正確格式的 utf-16 資料擴展回溯緩衝區的執行，以直接轉換成目標編碼。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
