---
title: 命名空間 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: bef2fa96ce090a600155d68ecc3daea55b675840
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185519"
---
# <a name="namespaces-entity-sql"></a>命名空間 (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 導入了命名空間，以避免發生名稱衝突，例如類型名稱、 實體集、 函式，等全域識別碼。 中的命名空間支援[!INCLUDE[esql](../../../../../../includes/esql-md.md)]中的命名空間支援類似[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)]。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供兩種形式的 USING 子句： 限定的命名空間 （其中的命名空間提供較短的別名） 和不合格的命名空間，如下列範例所示：  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>名稱解析規則  
 如果無法解析識別項，在區域範圍，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試在全域範圍 （命名空間） 中找到的名稱。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 第一次嘗試比對識別項 （前置詞） 與其中一個限定的命名空間。 如果沒有相符項目，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試解析指定的命名空間中的識別項的其餘部分。 如果兩者不相符，則會擲回例外狀況。  
  
 接下來，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]嘗試搜尋所有非限定的命名空間 （初構中指定） 的識別項。 如果可以在剛好一個命名空間內找到此識別項，就會傳回該位置。 如果有一個以上的命名空間符合該識別項，則會擲回例外狀況。 如果沒有命名空間，可以針對該識別碼，找出[!INCLUDE[esql](../../../../../../includes/esql-md.md)]傳遞到下一個向外範圍的名稱 (<xref:System.Data.Common.DbCommand>或<xref:System.Data.Common.DbConnection>物件)，如下列範例所示：  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>與 .NET Framework 的差異  
 在 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 中，您可以使用部分限定的命名空間。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 不允許此動作。  
  
## <a name="adonet-usage"></a>ADO.NET 使用方式  
 查詢是透過 ADO.NET <xref:System.Data.Common.DbCommand> 物件來表示。 <xref:System.Data.Common.DbCommand> 物件可建立在<xref:System.Data.Common.DbConnection>物件。 此外，命名空間也可以指定成 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbConnection> 物件的一部分。 如果[!INCLUDE[esql](../../../../../../includes/esql-md.md)]無法解析識別項，在查詢本身的外部命名空間會探查 （根據類似的規則）。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
