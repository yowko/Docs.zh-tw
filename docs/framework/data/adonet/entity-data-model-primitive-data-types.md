---
title: "實體資料模型：基本資料型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f25c94582ade23b645942a13829a5aa559e3e4f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-primitive-data-types"></a>實體資料模型：基本資料型別
實體資料模型 (EDM) 支援一組用來定義的抽象基本資料類型 （例如字串、 布林值、 Int32 等） 的[屬性](../../../../docs/framework/data/adonet/property.md)概念模型中。 這些基本資料型別是實際基本資料型別的 Proxy，無論在 SQL Server 資料庫或 Common Language Runtime (CLR) 等儲存或裝載環境中皆可支援。 EDM 不會定義基本資料型別作業或慣例的語意，這些語意是由儲存或裝載環境定義的。 一般來說，EDM 中的基本資料型別對應於儲存或裝載環境中相對應的基本資料型別。 如需如何 Entity Framework 將 EDM 中的基本類型對應到 SQL Server 資料類型資訊，請參閱[適用於 Entity Framework 的 SqlClient](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)。  
  
> [!NOTE]
>  EDM 不支援基本資料型別集合。  
  
 如需 EDM 中結構化的資料類型的資訊，請參閱[實體類型](../../../../docs/framework/data/adonet/entity-type.md)和[複雜型別](../../../../docs/framework/data/adonet/complex-type.md)。  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>實體資料模型中支援的基本資料型別  
 下表列出 EDM 所支援的基本資料型別。 這個表格也列出[facet](../../../../docs/framework/data/adonet/facet.md) ，可以套用到每個基本資料類型。  
  
|基本資料型別|描述|適用的 Facet|  
|-------------------------|-----------------|-----------------------|  
|二元|包含二進位資料。|MaxLength、FixedLength、Nullable、Default|  
|Boolean|包含值 `true` 或`false`。|Nullable、Default|  
|Byte|包含不帶正負號的 8 位元整數值。|Precision、Nullable、Default|  
|DateTime|表示日期和時間。|Precision、Nullable、Default|  
|DateTimeOffset|包含與 GMT 的日期和時間時差 (以分鐘為單位)。|Precision、Nullable、Default|  
|Decimal|包含固定有效位數和小數位數的數值。|Precision、Nullable、Default|  
|Double|包含具有 15 位數精確度的浮點數。|Precision、Nullable、Default|  
|浮動|包含具有 7 位數精確度的浮點數。|Precision、Nullable、Default|  
|Guid|包含 16 位元組的唯一識別碼。|Precision、Nullable、Default|  
|Int16|包含帶正負號的 16 位元整數值。|Precision、Nullable、Default|  
|Int32|包含帶正負號的 32 位元整數值。|Precision、Nullable、Default|  
|Int64|包含帶正負號的 64 位元整數值。|Precision、Nullable、Default|  
|SByte|包含帶正負號的 8 位元整數值。|Precision、Nullable、Default|  
|String|包含字元資料。|Unicode、FixedLength、MaxLength、Collation、Precision、Nullable、Default|  
|時間|包含一天的時間。|Precision、Nullable、Default|  
  
## <a name="see-also"></a>請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
