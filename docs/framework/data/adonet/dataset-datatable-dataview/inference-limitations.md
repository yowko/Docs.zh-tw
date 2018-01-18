---
title: "推斷限制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: af344055e511a2657007e216e1df304e2243362c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="inference-limitations"></a>推斷限制
根據每份文件的 XML 項目，當您執行從 XML 推斷 <xref:System.Data.DataSet> 結構描述的處理序時，可能會得到不同的結構描述。 例如，請考量下列 XML 文件。  
  
 Document1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 針對 「 文件 1 」，推斷程序會產生**資料集**名為"DocumentElement 」 和資料表，名為"Element1，"因為 「 Element1 」 是重複的項目。  
  
 **資料集：** DocumentElement  
  
 **Table:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 不過，如"Document2"，推斷程序會產生**資料集**名為"NewDataSet"和資料表，名為"DocumentElement。 」 Element1 會被推斷為資料行，因為它沒有屬性和項目子系。  
  
 **資料集：** NewDataSet  
  
 **Table:** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。  
  
 若要避免從 XML 文件產生結構描述時，可能會發生不一致，我們建議您明確指定載入時，使用 XML 結構描述定義語言 (XSD) 或 XML 資料精簡 (XDR) 結構描述**資料集**從XML。 如需有關明確指定**資料集**結構描述與 XML 結構描述，請參閱[衍生資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。  
  
## <a name="see-also"></a>請參閱  
 [從 XML 推斷資料集關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
