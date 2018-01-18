---
title: "數學標準函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33c8b500002b46d720533f681807889955de5982
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="math-canonical-functions"></a>數學標準函式
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 包括一些數學標準函式。  
  
 下表所示為數學 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 標準函式。  
  
|函式|描述|  
|--------------|-----------------|  
|`Abs(` `value` `)`|傳回 `value` 的絕對值。<br /><br /> **引數**<br /><br /> `Int16`， `Int32`， `Int64`， `Byte`， `Single`， `Double`，和`Decimal`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|傳回大於或等於 `value` 的最小整數。<br /><br /> **引數**<br /><br /> A `Single`， `Double`，和`Decimal`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|傳回小於或等於 `value` 的最大整數。<br /><br /> **引數**<br /><br /> A `Single`， `Double`，和`Decimal`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|傳回指定的 `value` 結果至指定的 `exponent`。<br /><br /> **引數**<br /><br /> `value`: `Int32, Int64, Double`，或`Decimal`。<br /><br /> `exponent`: `Int64``, Double`，或`Decimal`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|傳回 `value` 的整數部分，四捨五入成最接近的整數。<br /><br /> **引數**<br /><br /> A `Single`， `Double`，和`Decimal`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|傳回 `value`，四捨五入至最接近的指定 `digits`。<br /><br /> **引數**<br /><br /> `value`：`Double` 或 `Decimal`。<br /><br /> `digits`：`Int16` 或 `Int32`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|傳回 `value`，截斷至最接近的指定 `digits`。<br /><br /> **引數**<br /><br /> `value`：`Double` 或 `Decimal`。<br /><br /> `digits`：`Int16` 或 `Int32`。<br /><br /> **傳回值**<br /><br /> `value` 的類型。<br /><br /> **範例**<br /><br /> `Truncate(748.58,1)`|  
  
 如果提供 `null` 輸入，這些函式會傳回 `null`。  
  
 Microsoft SQL Client Managed Provider 中提供了對等的功能。 如需詳細資訊，請參閱[適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="see-also"></a>請參閱  
 [標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
