---
title: "資料集結構描述推斷程序摘要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 63ab866785f1fea66ed72fa17589a5be790fcdaa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>資料集結構描述推斷程序摘要
推斷程序首先會決定要將 XML 文件的哪個項目推斷為資料表， 再從剩餘的 XML 決定這些資料表的資料行， 若為巢狀資料表，推斷程序會產生巢狀的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。  
  
 下列為推斷規則的簡明摘要：  
  
-   具有屬性的項目會推斷為資料表。  
  
-   具有項目子系的項目會推斷為資料表。  
  
-   重複的項目會推斷為單一資料表。  
  
-   如果文件或根項目沒有可被推斷為資料行的屬性和子項目，則該項目將被推斷為 <xref:System.Data.DataSet>。 否則，該文件項目就會推斷為資料表。  
  
-   屬性會推斷為資料行。  
  
-   沒有屬性或項目子系且不重複的項目，會推斷為資料行。  
  
-   項目會推斷為巢狀資料表內其他項目也被推斷為資料表，巢狀**DataRelation**建立兩個資料表之間。 新的主要索引鍵資料行名為**TableName_Id**加入兩個資料表，並使用**DataRelation**。 A **ForeignKeyConstraint**使用兩個資料表之間會建立**TableName_Id**資料行。  
  
-   針對項目，會推斷為資料表，而且會包含文字，但沒有子元素，新的資料行名為**TableName_Text**建立的每個元素的文字。 如果項目是推斷為資料表且同時具有文字和項目子系，則會忽略文字。  
  
## <a name="see-also"></a>請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
