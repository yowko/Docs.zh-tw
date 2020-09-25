---
title: 運算子優先順序 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: f8aa0f213a24d6431d8910af849571a67fbd9f57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175638"
---
# <a name="operator-precedence-entity-sql"></a>運算子優先順序 (Entity SQL)

當 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢有多個運算子時，運算子優先順序會決定作業的執行順序。 執行的順序對於查詢結果有很大的影響。  
  
 下表顯示運算子的優先順序層級。 先評估層級較高的運算子，再評估層級較低的運算子。  
  
|層級|作業類型|運算子|  
|-----------|--------------------|--------------|  
|1|主要|`. , [] ()`|  
|2|一元|`! not`|  
|3|乘法|`* / %`|  
|4|加法|`+ -`|  
|5|排序|`< > <= >=`|  
|6|等式|`= != <>`|  
|7|條件式 AND|`and &&`|  
|8|條件式 OR|`or &#124;&#124;`|  
  
 當運算式中的兩個運算子有相同的運算子優先順序層級時，會依據它們在查詢中的位置，由左至右來評估它們。 例如，`x+y-z` 會判斷值為 `(x+y)-z`。  
  
 您可以使用括號來覆寫查詢中已定義的運算子優先順序。 括號內的所有內容都會先評估得出單一結果，之後，括號外的任何運算子便可以使用這個結果。 例如，將 `x+y*z` 乘以 `y` ， `z` 然後加 `x` 上，但是會 `(x+y)*z` 將結果相加， `x` 然後將 `y` 結果乘以 `z` 。  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 概觀](entity-sql-overview.md)
