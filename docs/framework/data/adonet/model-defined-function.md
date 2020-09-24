---
title: 模型定義函式
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 04d27387c30d5fe09d31c1b2cc94741f21ffe8e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150774"
---
# <a name="model-defined-function"></a>模型定義函式

*模型定義函數*是概念模型中定義的函式。 模型定義函式的主體是以 [Entity SQL](./ef/language-reference/entity-sql-language.md)表示，可讓函式與資料來源中支援的規則或語言分開表示。  
  
 模型定義函式的定義包含下列資訊：  
  
- 函式名稱。 (必要)  
  
- 傳回值的型別。 (選用)  
  
    > [!NOTE]
    > 若未指定任何傳回型別，則傳回值為 void。  
  
- 參數資訊。 (選用)  
  
- 定義函數主體的 [Entity SQL](./ef/language-reference/entity-sql-language.md) 運算式。  
  
 請注意，模型定義函式不支援輸出參數。 有此限制後才能夠撰寫模型定義函式。  
  
## <a name="example"></a>範例  

 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。  
  
 ![顯示具有已發行日期之模型的螢幕擷取畫面。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 定義概念模型中的函式，會傳回上圖中 `Book` 執行個體發行年度以來的年份。  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [實體資料模型：基本資料類型](entity-data-model-primitive-data-types.md)
