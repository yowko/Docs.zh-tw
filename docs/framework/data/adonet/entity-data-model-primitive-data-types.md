---
title: 實體資料模型：基本資料類型
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: dd688a06a47f4c44c27ddee2120b9de6980672fc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795168"
---
# <a name="entity-data-model-primitive-data-types"></a>實體資料模型：基本資料類型
實體資料模型（EDM）支援一組抽象的基本資料類型（例如字串、布林值、Int32 等等），可用來定義概念模型中的[屬性](property.md)。 這些基本資料型別是實際基本資料型別的 Proxy，無論在 SQL Server 資料庫或 Common Language Runtime (CLR) 等儲存或裝載環境中皆可支援。 EDM 不會定義基本資料型別作業或慣例的語意，這些語意是由儲存或裝載環境定義的。 一般來說，EDM 中的基本資料型別對應於儲存或裝載環境中相對應的基本資料型別。 如需 Entity Framework 如何將 EDM 中的基本型別對應至 SQL Server 資料類型的詳細資訊，請參閱[Entity FrameworkTypes 的 SqlClient](./ef/sqlclient-for-ef-types.md)。  
  
> [!NOTE]
> EDM 不支援基本資料型別集合。  
  
 如需 EDM 中結構化資料類型的詳細資訊，請參閱[實體類型](entity-type.md)和[複雜類型](complex-type.md)。  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>實體資料模型中支援的基本資料型別  
 下表列出 EDM 所支援的基本資料型別。 資料表也會列出可以套用至每個基本資料類型的[facet](facet.md) 。  
  
|基本資料型別|說明|適用的 Facet|  
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
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
