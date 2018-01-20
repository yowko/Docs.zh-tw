---
title: "分頁 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dfbd282eed19fdfa81a1dda5d06d41a80386feaa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="paging-entity-sql"></a>分頁 (Entity SQL)
可以透過執行實際分頁[略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)和[限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)中的子子句[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句。 若要以決定性的方式執行實體分頁，您應該要使用 SKIP 和 LIMIT。 如果您只想要限制非決定性的方式在結果中的資料列數目，您應該使用[頂端](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)。 TOP 和 SKIP/LIMIT 互斥。  
  
## <a name="top-overview"></a>TOP 概觀  
 SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。 TOP 子項子句指定只會從查詢結果傳回第一組資料列。 如需詳細資訊，請參閱[頂端](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)。  
  
## <a name="skip-and-limit-overview"></a>SKIP 和 LIMIT 概觀  
 SKIP 和 LIMIT 是 ORDER BY 子句的一部分。 如果 ORDER BY 子句中有 SKIP 運算式子項子句存在，將會根據排序的指定來排序結果，而且結果集將包含緊接在 SKIP 運算式之後的下一個資料列開始的資料列。 例如，SKIP 5 將會略過前五個資料列，並且傳回從第六個資料列以後的資料列。 如果 ORDER BY 子句中有 LIMIT 運算式次子句，此查詢將會依據排序規格排序，而且所產生的資料列數目將會受到 LIMIT 運算式的限制。 舉例來說，LIMIT 5 會將結果集限制為五個執行個體或資料列。 SKIP 和 LIMIT 不必一起使用，您可以搭配 ORDER BY 子句來單獨使用 SKIP 或 LIMIT。 如需詳細資訊，請參閱下列主題：  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [如何： 逐頁檢視查詢結果](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
