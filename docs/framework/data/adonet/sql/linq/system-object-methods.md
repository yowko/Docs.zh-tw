---
title: System.Object 方法
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 3a52f081f1c0c6e6c5218550009c736d0ed60514
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917657"
---
# <a name="systemobject-methods"></a>System.Object 方法
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援下列<xref:System.Object>方法。  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.Object> 方法。  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|二進位型別 (例如 <xref:System.Object.ToString?displayProperty=nameWithType>、`BINARY`、`VARBINARY` 和 `IMAGE`) 的 `TIMESTAMP`。||  
  
## <a name="differences-from-net"></a>與 .NET 的差異  
 輸出<xref:System.Object.ToString?displayProperty=nameWithType>雙精度浮點數會使用 SQL `CONVERT`(NVARCHAR(30)， @x，2) 在 SQL 上。 在此情況下，SQL 一律會使用 16 位數和科學記號表示法 (例如，"0.000000000000000e+000" 代表 0)。 因此，<xref:System.Object.ToString?displayProperty=nameWithType> 轉換不會產生與 .NET Framework 中 <xref:System.Convert.ToString%2A?displayProperty=nameWithType> 相同的字串。  
  
## <a name="see-also"></a>另請參閱

- [資料類型和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
