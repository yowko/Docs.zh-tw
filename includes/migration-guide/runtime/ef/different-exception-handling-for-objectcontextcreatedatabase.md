---
ms.openlocfilehash: 33ad1c044001e0a8d09708cc7a1f06e05cb307de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235132"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>ObjectContext.CreateDatabase 和 DbProviderServices.CreateDatabase 方法處理例外狀況的方式不同

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.5 開始，如果資料庫建立失敗，<code>CreateDatabase</code> 方法會嘗試卸除空白資料庫。 如果該作業成功，則會傳播原始 <xref:System.Data.SqlClient.SqlException?displayProperty=name> (而不是在 .NET Framework 4.0 中一律擲回的 <xref:System.InvalidOperationException?displayProperty=name>)|
|建議|如果在執行 <xref:System.Data.Objects.ObjectContext.CreateDatabase> 或 <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> 時攔截 <xref:System.InvalidOperationException?displayProperty=name>，現在也應該要攔截 SQLException。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
