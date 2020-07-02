---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621951"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>格線含星號資料列空間配置演算法的改進

#### <a name="details"></a>詳細資料

已修正 <xref:System.Windows.Controls.Grid> (於 .NET Framework 4.7 推出) 中[配置大小至 ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) 的演算法錯誤 (Bug)。  在某些情況下，例如含 <code>Height=&quot;Auto&quot;</code> 與空白資料列的格線，資料列會排列在錯誤的位置，可能會全部擠在格線外。

#### <a name="suggestion"></a>建議

若要讓應用程式受益於這些變更，您必須在 .NET Framework 4.8 或更新版本上執行應用程式。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.8|
|類型|執行階段|
