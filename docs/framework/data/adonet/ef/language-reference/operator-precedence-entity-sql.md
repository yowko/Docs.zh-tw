---
title: "運算子優先順序 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 537c9ae7c92c6abcbe597970f2b0ec29e399bc62
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="operator-precedence-entity-sql"></a>運算子優先順序 (Entity SQL)
當[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢有多個運算子，運算子優先順序會決定作業的執行的順序。 執行的順序對於查詢結果有很大的影響。  
  
 下表顯示運算子的優先順序層級。 先評估層級較高的運算子，再評估層級較低的運算子。  
  
|層級|運算類型|運算子|  
|-----------|--------------------|--------------|  
|1|主要|`. , [] ()`|  
|2|一元|`! not`|  
|3|乘法類 (Multiplicative)|`* / %`|  
|4|加法類 (Additive)|`+ -`|  
|5|排序|`< > <= >=`|  
|6|相等|`= != <>`|  
|7|條件式 AND|`and &&`|  
|8|條件式 OR|`or &#124;&#124;`|  
  
 當運算式中的兩個運算子有相同的運算子優先順序層級時，會依據它們在查詢中的位置，由左至右來評估它們。 例如，`x+y-z` 會判斷值為 `(x+y)-z`。  
  
 您可以使用括號來覆寫查詢中已定義的運算子優先順序。 括號內的所有內容都會先評估得出單一結果，之後，括號外的任何運算子便可以使用這個結果。 比方說，`x+y*z`乘以`y`由`z`，然後新增`x`，但`(x+y)*z`新增`x`至`y`然後相乘的結果和`z`。  
  
## <a name="see-also"></a>請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
