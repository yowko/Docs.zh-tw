---
title: 資料集結構描述推斷程序摘要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 8d517487b96aa7f204ea9f25d326500db7df413a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198505"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>資料集結構描述推斷程序摘要

推斷程序首先會決定要將 XML 文件的哪個項目推斷為資料表， 再從剩餘的 XML 決定這些資料表的資料行， 若為巢狀資料表，推斷程序會產生巢狀的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。  
  
 以下是推斷規則的簡短摘要：  
  
- 具有屬性的項目會推斷為資料表。  
  
- 具有項目子系的項目會推斷為資料表。  
  
- 重複的項目會推斷為單一資料表。  
  
- 如果文件或根項目沒有可被推斷為資料行的屬性和子項目，則該項目將被推斷為 <xref:System.Data.DataSet>。 否則，該文件項目就會推斷為資料表。  
  
- 屬性會推斷為資料行。  
  
- 沒有屬性或項目子系且不重複的項目，會推斷為資料行。  
  
- 針對在其他專案（也會推斷為數據表）中推斷為嵌套資料表的專案，會在這兩個數據表之間建立嵌套 **DataRelation** 。 名為 **TableName_Id** 的新主鍵資料行，會加入至這兩個數據表，而且 **DataRelation**所使用的資料行。 使用**TableName_Id**資料行，在兩個數據表之間建立**ForeignKeyConstraint** 。  
  
- 對於推斷為數據表且包含文字但沒有子專案的專案，會針對每個元素的文字建立名為 **TableName_Text** 的新資料行。 如果項目是推斷為資料表且同時具有文字和項目子系，則會忽略文字。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [在資料集中使用 XML](using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
