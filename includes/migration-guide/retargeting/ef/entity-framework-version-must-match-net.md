---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774318"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework 版本必須符合 .NET Framework 版本

|   |   |
|---|---|
|詳細資料|Entity Framework 版本應該符合 .NET Framework 版本。 建議針對 .NET Framework 4.5 使用 Entity Framework 5。 .NET Framework 4.5 專案中，已知 EF 4.x 有一些 <xref:System.ComponentModel.DataAnnotations> 相關問題。 在 .NET 4.5 中，這些已移至不同的組件，因此決定要使用哪些註解時會有問題。|
|建議|針對 .NET Framework 4.5 升級至 Entity Framework 5|
|範圍|主要|
|版本|4.5|
|類型|正在重定目標|
