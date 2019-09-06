---
title: 函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250912"
---
# <a name="functions-entity-sql"></a>函式 (Entity SQL)
Entity SQL 支援使用者定義函式、標準函式及提供者特有的函式。 使用者定義函式可在概念模型中指定，或是內嵌於查詢之中。 如需詳細資訊，請參閱[使用者定義函數](user-defined-functions-entity-sql.md)。  
  
 標準函式會預先定義在 Entity Framework 中，而且應該受到資料提供者的支援。 如果使用者呼叫的函式未受到提供者的支援，Entity SQL 將會失敗。 因此，通常建議優先使用標準函式勝於存放區特有的函式，後者位於提供者特有的命名空間內。 如需詳細資訊，請參閱[標準](canonical-functions.md)函式。  
  
 Microsoft SQL Client Managed Provider 提供了一組提供者特有的函式。 如需詳細資訊，請參閱[SqlClient for Entity Framework 函數](../sqlclient-for-ef-functions.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用者定義函式](user-defined-functions-entity-sql.md)  
  
 [函式多載解析](function-overload-resolution-entity-sql.md)  
  
 [彙總函式](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
