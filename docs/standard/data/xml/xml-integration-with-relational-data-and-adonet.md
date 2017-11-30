---
title: "XML 與關聯式資料和 ADO.NET 互相整合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d03a0ca7518b06c08d98967d7c5ae864f1c04ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>XML 與關聯式資料和 ADO.NET 互相整合
**XmlDataDocument**類別是在衍生的類別的**XmlDocument**，而且含有 XML 資料。 優點**XmlDataDocument**是提供關聯式及階層式資料之間的橋樑。 它是**XmlDocument** ，可以繫結至**資料集**這兩個類別能同步處理兩個類別中包含的資料所做的變更。 **XmlDocument**繫結至**資料集**允許 XML 與關聯式資料、 整合和您沒有將成為 XML 或以關聯式格式表示的資料。 兩種您都可以選擇，而不必受限於單一資料表示法。  
  
 資料以兩種型式提供的好處在於：  
  
-   XML 文件的結構化部分可以對應到資料集，因此可以有效的儲存、索引和搜尋。  
  
-   轉換、驗證和巡覽可透過以關聯方式儲存的 XML 資料上的游標模型有效達成。 有些時候，可以進行更有效率地運用關聯式結構如果 XML 儲存在**XmlDocument**模型。  
  
-   **資料集**可以儲存 XML 的部分。 也就是說，您可以使用**XPath**或**XslTransform**商店**資料集**項目與感興趣的屬性。 從該處，才能進行變更以較小、 篩選的資料子集，將變更傳送到在較大的資料與**XmlDataDocument**。  
  
 您也可以在已載入的資料上執行轉換**資料集**從 SQL Server。 另一個選項是將繫結 .NET Framework 類別樣式管理的 WinForm 和 WebForm 控制項**資料集**填入 XML 輸入資料流。  
  
 除了支援**XslTransform**、 **XmlDataDocument**公開關聯式資料給**XPath**查詢和驗證。  基本上，關聯式資料和關聯式設備都提供所有的 XML 服務，如控制項結合、Codegen 等等，可以在不危害 XML 真實性的結構化 XML 設計上使用。  
  
 因為**XmlDataDocument**繼承自**XmlDocument**，它會提供 W3C DOM 的實作 事實上， **XmlDataDocument**相關聯，並將內，其資料的子集**資料集**不會限制或改變其作為**XmlDocument**以任何方式。 程式碼撰寫來取用**XmlDocument**而**XmlDataDocument**。 **資料集**藉由定義資料表、 資料行、 關聯和條件約束提供相同資料的關聯式檢視，而且是獨立、 記憶體中的使用者資料存放區。  
  
 下圖顯示不同的關聯的 XML 資料具有**資料集**和**XmlDataDocument**。  
  
 ![XML 資料集](../../../../docs/standard/data/xml/media/xmlintegrationwithrelationaldataandadodotnet.gif "xmlIntegrationWithRelationalDataAndADOdotNet")  
  
 下圖顯示的 XML 資料可以直接載入**資料集**，允許以關聯方式直接管理 XML。 或者，可以將 XML 載入至 DOM，也就是在衍生類別**XmlDataDocument**，並會載入且與同步處理**資料集**。 因為**資料集**和**XmlDataDocument**會透過一組同步處理的資料，一個存放區中的資料所做的變更會反映在其他存放區。  
  
 **XmlDataDocument**繼承所有的編輯和巡覽功能**XmlDocument**。 有時候當使用**XmlDataDocument**其繼承的功能，與同步處理**資料集**，為更適當的選項，比將 XML 直接載入**資料集**. 下表顯示當您選擇哪一種方法，要用來載入時被視為項目**資料集**。  
  
|直接將 XML 載入 DataSet 的時機|同步 DataSet 與 XmlDataDocument 的時機|  
|----------------------------------------------|-----------------------------------------------------------|  
|查詢中的資料**資料集**較容易使用 SQL 比使用 XPath。|XPath 查詢中的資料需要**資料集**。|  
|來源 XML 中項目順序的保留並不重要。|來源 XML 中項目順序的保留很重要。|  
|項目和格式間的泛空白字元不需要保留在來源 XML 中。|在來源 XML 中保留泛空白字元和格式很重要。|  
  
 如果載入和寫入 XML，直接傳入和傳出**資料集**滿足時，請參閱[從 XML 載入 DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)和[撰寫為 XML 資料的資料集](../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)。  
  
 如果載入**資料集**從**XmlDataDocument**滿足時，請參閱[使用 XML 文件同步處理](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 DataSet 中使用 XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
