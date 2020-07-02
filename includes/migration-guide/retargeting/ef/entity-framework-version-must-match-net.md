---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617138"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework 版本必須符合 .NET Framework 版本

#### <a name="details"></a>詳細資料

Entity Framework （EF）版本應該與 .NET Framework 版本相符。 建議針對 .NET Framework 4.5 使用 Entity Framework 5。 .NET Framework 4.5 專案中，已知 EF 4.x 有一些 <xref:System.ComponentModel.DataAnnotations> 相關問題。 在 .NET Framework 4.5 中，這些已移至不同的元件，因此在決定要使用的注釋時，會發生問題。

#### <a name="suggestion"></a>建議

針對 .NET Framework 4.5 升級至 Entity Framework 5

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |
