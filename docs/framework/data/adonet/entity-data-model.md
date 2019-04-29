---
title: 實體資料模型
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 8e96890d97f652295a3fdb67c48ec37710280eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667141"
---
# <a name="entity-data-model"></a>實體資料模型
實體資料模型 (EDM) 是描述資料結構的概念集，不論其預存形式為何。 EDM 借用 Peter Chen 於 1976 年描述的實體關聯模型 (Entity-Relationship Model)，但同時補強實體關聯模型並延伸其傳統用法。  
  
 EDM 解決資料儲存形式過多所導致的難題。 例如，試想將資料儲存在關聯式資料庫、文字檔、XML 檔、試算表及報告中的企業。 這代表著資料模型、應用程式設計及資料存取各方面的重大挑戰。 設計資料導向應用程式時，難題在於撰寫有效率且可維護的程式碼，而不需犧牲資料存取、儲存的效率及擴充性。 資料具有關聯結構時，資料存取、儲存及擴充性非常有效率，但維持寫入效率及可維護的程式碼則更為困難。 當資料具有物件結構時，會反轉取捨：撰寫有效率且可維護的程式碼其實有效率的資料存取、 儲存體和延展性。 即使能在這些取捨當中找到平衡，在不同形式之間轉移資料時仍會出現新的挑戰。 實體資料模型能夠依據獨立於任何儲存結構描述的實體和關聯來描述資料結構，因此可以解決這些難題。 這也讓資料的預存形式與應用設計和開發不相關。 同時，由於實體和關聯會以應用程式中使用資料的方式 (而非其預存形式) 來描述資料結構，因此可以隨著應用程式的演進而演進。  
  
 `conceptual model`是以實體和關係代表資料結構的特定表示，而且通常是以實作 EDM 概念的特定定義域語言 (DSL) 定義而成。 [概念結構定義語言 (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)是這類特定領域語言的範例。 您可以將概念模型中描述的實體和關聯視為應用程式中的抽象物件和關聯。 這樣可讓開發人員專注於概念模型，不需擔心儲存結構描述，也可以讓他們有效率地撰寫程式碼並兼顧可維護性。 同時，儲存結構描述設計人員可以專注於資料存取、儲存的效率及擴充性。  
  
## <a name="in-this-section"></a>本節內容  
 本節的主題描述實體資料模型的概念。 實作 EDM 介面的任何 DSL 都應包括此處描述的概念。 請注意， [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用 CSDL 來定義概念模型。 如需詳細資訊，請參閱 [CSDL Specification](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)。  
  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [實體資料模型：命名空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [實體資料模型：基本資料型別](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [實體資料模型：繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [關聯 End](../../../../docs/framework/data/adonet/association-end.md)  
  
 [關聯 End 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [關聯集](../../../../docs/framework/data/adonet/association-set.md)  
  
 [關聯集 End](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [關聯類型](../../../../docs/framework/data/adonet/association-type.md)  
  
 [複雜類型](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [實體容器](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [實體集](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [實體類型](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [模型宣告函式](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [模型定義函式](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [屬性](../../../../docs/framework/data/adonet/property.md)  
  
 [參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [.edmx 檔案概觀](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [CSDL 規格](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
