---
title: "函式多載解析 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3a303ca917a9f6cfee42d11456a1f80b52ffd2ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="function-overload-resolution-entity-sql"></a>函式多載解析 (Entity SQL)
本主題描述如何解析 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 函式。  
  
 可以定義一個以上的同名函式，只要這些函式具有唯一的簽章即可。  
  
 在這種情況下，必須套用下列準則，以判斷哪一個函式是由給定的運算式參考。 這些準則會依序套用。 只套用到單一函式的第一個準則就是被解析的函式。  
  
1.  **參數編號**。 此函式具有運算式中指定的相同參數數目。  
  
2.  **型別完全相符**。 此函式的每一個引數型別都完全符合參數型別，或是為 null 常值。  
  
3.  **符合子型別**。 此函式的每一個引數型別都完全符合或是為參數型別的子型別，或者引數為 null 常值。 萬一有幾個函式只有所需的子型別轉換數目不同，則具有最少子型別轉換數目的函式就是被解析的函式。  
  
4.  **比對的子型別或型別提升**。 此函式的每一個引數型別都完全符合或是為參數型別的子型別，或者可以提升為參數型別，或是引數為 null 常值。 同樣地，萬一有幾個函式只有子型別轉換和提升數目不同，則具有最少子型別轉換和提升數目的函式就是被解析的函式。  
  
 如果沒有一個準則導致單一函式被選取，表示函式引動過程運算式模稜兩可。  
  
 即使可以使用這些規則擷取單一函式，引數仍然可能不符合參數。 在此情況下會引發錯誤。  
  
 針對使用者定義函式，即使存在更符合使用者定義函式且含簽章的模型定義函式，內嵌查詢函式的定義仍擁有較高的優先順序。  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
