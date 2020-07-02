---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621955"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a>已修正當 ListBox 包含重複實值型別時的停止回應問題

#### <a name="details"></a>詳細資料

已修正下列問題：當虛擬化 <xref:System.Windows.Controls.ItemsControl> 的項目集合包含重複實值型別物件時，其在捲動期間會停止回應。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.8|
|類型|執行階段|
