---
title: 將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786069"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>將 XML 結構描述 (XSD) 條件約束對應至資料集條件約束
XML 結構描述定義語言 (XSD) 允許在其定義的項目和屬性上指定條件約束。 將 xml 架構對應至中<xref:System.Data.DataSet>的關聯式結構描述時，xml 架構條件約束會對應至**資料集**內資料表和資料行上適當的關聯式條件約束。  
  
 本節討論下列 XML 結構描述條件約束的對應：  
  
- 使用**unique**元素指定的唯一性條件約束。  
  
- 使用**key**元素指定的索引鍵條件約束。  
  
- 使用**keyref**元素指定的 keyref 條件約束。  
  
 您可以在項目或屬性上使用條件約束，為文件內任何執行個體項目的值指定特定限制。 例如，在架構中， **Customer**專案之**customerid**子項目的索引鍵條件約束表示**CustomerID**子項目的值在任何檔實例中必須是唯一的，而且不允許 null 值。  
  
 您也可以在文件的項目和屬性間指定條件約束，以便在文件中建立關係。 結構描述中會使用索引鍵條件約束和 keyref 條件約束在文件內指定條件約束，以建立文件項目和屬性之間的關係。  
  
 對應程式會將這些架構條件約束轉換成在**資料集**內建立之資料表的適當條件約束。  
  
## <a name="in-this-section"></a>本節內容  
 [將 unique XML 結構描述 (XSD) 條件約束對應至資料集條件約束](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來在**資料集中**建立唯一條件約束的 XML 架構元素。  
  
 [將 key XML 結構描述 (XSD) 條件約束對應至資料集條件約束](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述**資料集**內用來建立索引鍵條件約束（不允許 null 值的唯一條件約束）的 XML 架構元素。  
  
 [將 keyref XML 結構描述 (XSD) 條件約束對應至資料集條件約束](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 描述用來在**資料集**內建立 keyref （外鍵）條件約束的 XML 架構專案。  
  
## <a name="related-sections"></a>相關章節  
 [從 XML 結構描述 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 描述從 XSD 架構建立之**資料集**的關聯式結構（或架構）。  
  
 [從 XML 結構描述 (XSD) 產生資料集關聯](generating-dataset-relations-from-xml-schema-xsd.md)  
 描述用來在**資料集**內的資料表資料行之間建立關聯的 XML 架構元素。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](../ado-net-overview.md)
