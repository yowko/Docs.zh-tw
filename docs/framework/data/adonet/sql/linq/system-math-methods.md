---
title: System.Math 方法
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e91c8ea95d21288ad2577f1550333febd448766d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158197"
---
# <a name="systemmath-methods"></a>System.Math 方法

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.Math> 方法。  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>與 .NET 的差異  

 .NET Framework 使用的捨入語意 (Semantics) 與 SQL Server 不同。 <xref:System.Math.Round%2A>.NET Framework 中的方法會執行*銀行家的舍入*，其中以 .5 為結尾的數位會舍入到最接近的偶數數位，而不是下一個較高的數位。 例如，2.5 會捨入為 2，而 3.5 會進位為 4  (當資料異動很大時，此法有助於避免系統性地偏向較高位數的值)。  
  
 在 SQL 中，`ROUND` 函式則會一律往遠離 0 的方向捨入。 因此 2.5 會捨入為 3，這與 .NET Framework 中捨入為 2 相反。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會採用 SQL `ROUND` 語意，不會嘗試實作 Banker's Rounding (四捨六入五成雙)。  
  
## <a name="see-also"></a>另請參閱

- [資料類型與函式](data-types-and-functions.md)
