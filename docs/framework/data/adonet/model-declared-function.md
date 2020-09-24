---
title: 模型宣告函式
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: fb30dd86c29d6a7fff6f2c71d5fd892326e1fda4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147849"
---
# <a name="model-declared-function"></a>模型宣告函式

模型宣告函式是在概念模型中宣告的函 *式* ，但不是在該概念模型中定義的函數。 該函式可能是在裝載或儲存環境中定義的。 例如，模型宣告函式可能對應到在資料庫中定義的函式，因而在概念模型中公開伺服器端的功能。  
  
 模型宣告函式的宣告包含下列資訊：  
  
- 函式的名稱。 (必要)  
  
- 傳回值的型別。 (選用)  
  
    > [!NOTE]
    > 若未指定任何傳回值，則傳回型別為 void。  
  
- 參數資訊，包括參數名稱和型別。 (選用)  
  
## <a name="example"></a>範例  

 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 在 CSDL 中，模型宣告函式的其中一個實作為函式匯入 (使用 [FunctionImport 元素](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)) 。 下列 CSDL 定義具有函式匯入定義的實體容器。 請注意，由於沒有指定傳回型別，因此該函式的傳回型別為 void。  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
