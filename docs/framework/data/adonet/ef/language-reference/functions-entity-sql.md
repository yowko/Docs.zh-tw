---
title: 函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: 6c8a44a4e347ffabd665847f02bfafe267a14103
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760293"
---
# <a name="functions-entity-sql"></a>函式 (Entity SQL)
Entity SQL 支援使用者定義函式、標準函式及提供者特有的函式。 使用者定義函式可在概念模型中指定，或是內嵌於查詢之中。 如需詳細資訊，請參閱[使用者定義函數](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)。  
  
 標準函式會預先定義在 Entity Framework 中，而且應該受到資料提供者的支援。 如果使用者呼叫的函式未受到提供者的支援，Entity SQL 將會失敗。 因此，通常建議優先使用標準函式勝於存放區特有的函式，後者位於提供者特有的命名空間內。 如需詳細資訊，請參閱[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。  
  
 Microsoft SQL Client Managed Provider 提供了一組提供者特有的函式。 如需詳細資訊，請參閱[適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用者定義函式](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [函式多載解析](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [彙總函式](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
