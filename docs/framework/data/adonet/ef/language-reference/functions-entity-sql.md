---
title: "函式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9008360a4af0a669a223a2e56ee5152b23c6ebe4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="functions-entity-sql"></a>函式 (Entity SQL)
Entity SQL 支援使用者定義函式、標準函式及提供者特有的函式。 使用者定義函式可在概念模型中指定，或是內嵌於查詢之中。 如需詳細資訊，請參閱[使用者定義函數](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)。  
  
 標準函式會預先定義在 Entity Framework 中，而且應該受到資料提供者的支援。 如果使用者呼叫的函式未受到提供者的支援，Entity SQL 將會失敗。 因此，通常建議優先使用標準函式勝於存放區特有的函式，後者位於提供者特有的命名空間內。 如需詳細資訊，請參閱[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。  
  
 Microsoft SQL Client Managed Provider 提供了一組提供者特有的函式。 如需詳細資訊，請參閱[適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用者定義函式](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [函式多載解析](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [彙總函式](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
