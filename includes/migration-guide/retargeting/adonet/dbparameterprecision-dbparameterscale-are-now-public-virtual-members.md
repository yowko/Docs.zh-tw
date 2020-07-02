---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616037"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision 和 DbParameter.Scale 現在是公用虛擬成員

#### <a name="details"></a>詳細資料

<xref:System.Data.Common.DbParameter.Precision> 和 <xref:System.Data.Common.DbParameter.Scale> 會當做公用虛擬屬性來實作。 這些屬性取代對應的明確介面實作 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>。

#### <a name="suggestion"></a>建議

重建 ADO.NET 資料庫提供者時，這些差異會要求將 'override' 關鍵字套用至 Precision 和 Scale 屬性。 只有在重建元件時才需要這樣做；現有的二進位檔將繼續運作。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
