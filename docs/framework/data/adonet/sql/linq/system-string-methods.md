---
title: System.String 方法
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 44d32ed1000ca49d9fc29ffcde4506b44fc975b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155662"
---
# <a name="systemstring-methods"></a>System.String 方法

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.String> 方法。  
  
## <a name="unsupported-systemstring-methods-in-general"></a>一般不支援的 System.String 方法  

 一般不支援的 <xref:System.String> 方法：  
  
- 可感知文化特性的多載 (採用) 的方法 `CultureInfo`  /  `StringComparison`  /  `IFormatProvider` 。  
  
- 取用或產生 `char` 陣列的方法。  
  
## <a name="unsupported-systemstring-static-methods"></a>不支援的 System.String 靜態方法  
  
|不支援的 System.String 靜態方法|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a>不支援的 System.String 非靜態方法  
  
|不支援的 System.String 非靜態方法|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>與 .NET 的差異  
  
- 查詢不會考慮伺服器上可能作用中的 SQL Server 定序 (Collation)，因此預設會提供區分文化特性、但不區分大小寫的比較。 這個行為與 .NET Framework 的預設區分大小寫語意 (Semantics) 不同。  
  
- 當傳回 `LastIndexOf` 0 時，字串是 `NULL` 或找到的位置是0。  
  
- 固定長度字串 (`CHAR`、`NCHAR`) 上的串連或其他作業可能會傳回未預期的結果，原因是這些型別已自動將填補套用至資料庫中。  
  
- 因為許多方法 (如 `Replace`、`ToLower`、`ToUpper` 和字元索引子 (Indexer)) 都沒有 `TEXT` 或 `NTEXT` 資料行和 XML 的有效轉譯，所以如果正常轉譯，則會發生 `SqlExceptions`。 對這些型別而言，這個行為是可接受的行為。 不過，所有字串作業都必須符合 `VARCHAR`、`NVARCHAR`、`VARCHAR(max)` 和 `NVARCHAR(max)` 的 Common Language Runtime (CLR) 語意。  
  
## <a name="see-also"></a>另請參閱

- [資料類型與函式](data-types-and-functions.md)
