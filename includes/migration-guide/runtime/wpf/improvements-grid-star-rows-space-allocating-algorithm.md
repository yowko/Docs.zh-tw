---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802632"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>格線含星號資料列空間配置演算法的改進

|   |   |
|---|---|
|詳細資料|已修正 <xref:System.Windows.Controls.Grid> (於 .NET Framework 4.7 推出) 中[配置大小至 ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) 的演算法 Bug。  在某些情況下，例如含 <code>Height=&quot;Auto&quot;</code> 與空白資料列的格線，資料列會排列在錯誤的位置，可能會全部擠在格線外。|
|建議|若要讓應用程式受益於這些變更，您必須在 .NET Framework 4.8 或更新版本上執行應用程式。|
|範圍|主要|
|版本|4.8|
|類型|執行階段|

