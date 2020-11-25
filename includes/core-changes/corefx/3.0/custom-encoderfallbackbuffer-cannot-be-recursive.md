---
ms.openlocfilehash: 54ef49755dc0b9d1b821ae7999ab218626d455e1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032018"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>自訂 >encoderfallbackbuffer 實例無法遞迴地切換

自訂 <xref:System.Text.EncoderFallbackBuffer> 實例無法遞迴地切換。 的執行 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 必須產生可轉換為目的地編碼的字元序列。 否則，就會發生例外狀況。

#### <a name="change-description"></a>變更描述

在字元對位元組轉碼作業期間，執行時間會偵測格式不正確或 nonconvertible 的 UTF-16 序列，並提供這些字元給 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法。 `Fallback`方法會判斷哪些字元應該取代為原始 nonconvertible 資料，而這些字元會藉由 <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 在迴圈中呼叫來清空。

然後執行時間會嘗試將這些替代字元轉碼至目標編碼。 如果這項作業成功，則執行時間會繼續從原始輸入字串的左邊處開始轉碼。

先前的自訂執行 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 可以傳回無法轉換成目的地編碼的字元序列。 如果替代的字元無法轉碼至目標編碼，則執行時間會 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 再次使用替代字元叫用方法一次，預期方法會傳回 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 新的替代序列。 此程式會繼續進行，直到執行時間最終看到格式正確、可轉換的替代，或達到最大遞迴計數為止。

從 .NET Core 3.0 開始，的自訂實 <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> 作為必須傳回可轉換成目的地編碼的字元序列。 如果替代的字元無法轉碼至目標編碼， <xref:System.ArgumentException> 則會擲回。 執行時間不會再對實例進行遞迴呼叫 <xref:System.Text.EncoderFallbackBuffer> 。

只有在符合下列三個條件時，才會套用此行為：

- 執行時間偵測到格式不正確的 UTF-16 序列或 UTF-16 序列，無法轉換成目標編碼。
- 已指定自訂 <xref:System.Text.EncoderFallback> 。
- 自訂 <xref:System.Text.EncoderFallback> 會嘗試取代新格式不正確或 nonconvertible 的 utf-16 序列。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的開發人員都不需要採取任何動作。

如果應用程式使用自訂 <xref:System.Text.EncoderFallback> 和 <xref:System.Text.EncoderFallbackBuffer> 類別，請確定在 <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> 執行時間第一次叫用方法時，使用格式正確的 utf-16 資料來擴展回溯緩衝區的執行，以直接轉換成目標編碼。

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
