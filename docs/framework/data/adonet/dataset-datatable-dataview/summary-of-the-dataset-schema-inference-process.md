---
title: 資料集結構描述推斷程序摘要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 5266d08212e5259bd5b242a70d61e29ad9008006
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203252"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>資料集結構描述推斷程序摘要
推斷程序首先會決定要將 XML 文件的哪個項目推斷為資料表， 再從剩餘的 XML 決定這些資料表的資料行， 若為巢狀資料表，推斷程序會產生巢狀的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。  
  
 下列為推斷規則的簡明摘要：  
  
- 具有屬性的項目會推斷為資料表。  
  
- 具有項目子系的項目會推斷為資料表。  
  
- 重複的項目會推斷為單一資料表。  
  
- 如果文件或根項目沒有可被推斷為資料行的屬性和子項目，則該項目將被推斷為 <xref:System.Data.DataSet>。 否則，該文件項目就會推斷為資料表。  
  
- 屬性會推斷為資料行。  
  
- 沒有屬性或項目子系且不重複的項目，會推斷為資料行。  
  
- 針對在其他專案中推斷為嵌套資料表的專案, 這些專案也會推斷為數據表, 這兩個數據表之間會建立一個嵌套**DataRelation** 。 名為**TableName_Id**的新主鍵資料行會加入至資料表, 並供**DataRelation**使用。 這兩個數據表之間會使用**TableName_Id**資料行來建立**ForeignKeyConstraint** 。  
  
- 對於推斷為數據表並包含文字但沒有子項目的專案, 會針對每個專案的文字建立名為**TableName_Text**的新資料行。 如果項目是推斷為資料表且同時具有文字和項目子系，則會忽略文字。  
  
## <a name="see-also"></a>另請參閱

- [從 XML 推斷資料集關聯式結構](inferring-dataset-relational-structure-from-xml.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [在 DataSet 中使用 XML](using-xml-in-a-dataset.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
