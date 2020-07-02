---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620000"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy 針對字串使用目的地資料行編碼方式

#### <a name="details"></a>詳細資料

將資料插入資料行時，<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> 會使用目的地資料行的編碼方式，而不是 <code>VARCHAR</code> 和 <code>CHAR</code> 類型的預設編碼方式。 這項變更可排除當目的地資料行未使用預設編碼方式時，使用預設編碼方式可能造成的資料損毀。 在某些鮮少發生的情況下，如果變更編碼方式後產生的資料太大而不適用於目的地資料行，現有的應用程式可能會擲回 SqlException 例外狀況。

#### <a name="suggestion"></a>建議

由於編碼方式的差異，預期 <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> 不會再損毀資料。 如果所複製的字串接近目的地資料行的大小限制，可能必須預先編碼資料 (要複製以確認資料可納入目的地資料行) 或攔截 <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
