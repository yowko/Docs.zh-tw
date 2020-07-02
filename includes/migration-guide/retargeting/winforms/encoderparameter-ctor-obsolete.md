---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617146"
---
### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor 已淘汰

#### <a name="details"></a>詳細資料

<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 建構函式現在已淘汰，如果使用，就會產生建置警告。

#### <a name="suggestion"></a>建議

雖然 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 建構函式會繼續運作，但應改用下列建構函式，以避免使用 .NET Framework 4.5 工具重新編譯程式碼時出現已淘汰的建置警告：<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
