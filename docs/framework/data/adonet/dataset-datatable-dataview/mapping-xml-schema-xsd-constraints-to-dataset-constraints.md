---
title: 將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: c9cd97535a0165b82f0823c1f17f621491d4255c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276496"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束
XML 結構描述定義語言 (XSD) 允許在其定義的項目和屬性上指定條件約束。 對應 XML 結構描述中的關聯式結構描述時<xref:System.Data.DataSet>，XML 結構描述條件約束會對應到資料表和資料行內的適當關聯式條件約束**資料集**。  
  
 本節討論下列 XML 結構描述條件約束的對應：  
  
-   使用指定的唯一性條件約束**唯一**項目。  
  
-   使用指定的索引鍵條件約束**金鑰**項目。  
  
-   使用指定的 keyref 條件約束**keyref**項目。  
  
 您可以在項目或屬性上使用條件約束，為文件內任何執行個體項目的值指定特定限制。 例如，索引鍵條件約束**CustomerID**子項目**客戶**結構描述中的項目表示的值**CustomerID**子元素必須是在任何文件執行個體中是唯一而且不允許 null 值。  
  
 您也可以在文件的項目和屬性間指定條件約束，以便在文件中建立關係。 結構描述中會使用索引鍵條件約束和 keyref 條件約束在文件內指定條件約束，以建立文件項目和屬性之間的關係。  
  
 對應處理序會將這些結構描述條件約束轉換成適當的條件約束內建立的資料表上**資料集**。  
  
## <a name="in-this-section"></a>本節內容  
 [將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來建立唯一的條件約束中的 XML 結構描述項目**資料集**。  
  
 [將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來建立索引鍵條件約束 （不允許 null 值的唯一條件約束） 的 XML 結構描述項目**資料集**。  
  
 [將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來建立 keyref （外部索引鍵） 條件約束中的 XML 結構描述項目**資料集**。  
  
## <a name="related-sections"></a>相關章節  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 說明的關聯式結構描述**資料集**從 XSD 結構描述建立。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用來建立資料表中的資料行之間的關聯性的 XML 結構描述項目**資料集**。  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
