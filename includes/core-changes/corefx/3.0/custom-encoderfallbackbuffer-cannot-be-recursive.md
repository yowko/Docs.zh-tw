---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568214"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>自訂編碼器回退緩衝區實例不能遞迴

自訂<xref:System.Text.EncoderFallbackBuffer>實例不能遞迴。 的<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>實現必須產生可轉換為目標編碼的字元序列。 否則，將發生異常。

#### <a name="change-description"></a>變更描述

在字元到位元組轉碼操作期間，運行時檢測格式錯誤或不可轉換的 UTF-16 序列，並將這些字元提供<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>給該方法。 該方法`Fallback`確定哪些字元應替換為原始不可轉換資料，並且這些字元通過在迴圈中調用<xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType>而耗盡。

然後，運行時嘗試將這些替換字元轉碼到目標編碼。 如果此操作成功，運行時將繼續從原始輸入字串中保留的位置轉碼。

在 .NET 核心預覽 7 和早期版本中，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>的自訂實現可以返回不可轉換為目標編碼的字元序列。 如果替換的字元無法轉碼到目標編碼，運行時將再次使用替換字元調用<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>該方法，希望<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>該方法返回新的替換序列。 此過程將一直持續到運行時最終看到格式良好的可轉換替換，或直到達到最大遞迴計數。

從 .NET Core 3.0 開始，<xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>必須返回可轉換為目標編碼的字元序列的自訂實現。 如果替換的字元無法轉碼到目標編碼，則引發 。 <xref:System.ArgumentException> 運行時將不再對<xref:System.Text.EncoderFallbackBuffer>實例進行遞迴呼叫。

此行為僅在滿足以下所有三個條件時才適用：

- 運行時檢測格式錯誤的 UTF-16 序列或無法轉換為目標編碼的 UTF-16 序列。
- 已指定<xref:System.Text.EncoderFallback>自訂項。
- 自訂<xref:System.Text.EncoderFallback>嘗試替換新的格式錯誤或不可轉換的 UTF-16 序列。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大多數開發人員不需要採取任何操作。

如果應用程式使用<xref:System.Text.EncoderFallback>自訂和<xref:System.Text.EncoderFallbackBuffer>類，請確保使用格式良好的 UTF-16 資料<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>填充回退緩衝區，這些資料在運行時首次調用<xref:System.Text.EncoderFallbackBuffer.Fallback%2A>該方法時直接轉換為目標編碼。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
