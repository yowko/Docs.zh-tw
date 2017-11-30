---
title: "ADO.NET 架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 227bef975a54676ceda5f922ed02f98c27fc8759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-architecture"></a>ADO.NET 架構
傳統的資料處理主要是依賴相互連接的雙層式模型。 隨著資料處理朝多層式架構發展，程式設計人員也逐漸改用中斷連接的方式，使應用程式更具延展性 (Scalability)。  
  
## <a name="adonet-components"></a>ADO.NET 元件  
 [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] 中用於存取和管理資料的兩個主要元件是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者和 <xref:System.Data.DataSet>。  
  
### <a name="net-framework-data-providers"></a>.NET Framework 資料提供者  
 .NET Framework 資料提供者是一種明確設計用於管理資料以及快速存取順向唯讀資料的元件。 `Connection` 物件會提供資料來源的連接。 `Command` 物件可讓您存取資料庫命令，以便傳回資料、修改資料、執行預存程序 (Stored Procedure)，並且傳送或擷取參數資訊。 `DataReader` 則可提供來自資料來源的高效能資料流。 最後，`DataAdapter` 會提供 `DataSet` 物件與資料來源之間的橋接器 (Bridge)。 `DataAdapter` 會使用 `Command` 物件於資料來源處執行 SQL 命令，以便將資料載入 `DataSet`，並且將 `DataSet` 內的資料變更調節回資料來源。 如需詳細資訊，請參閱[.NET Framework 資料提供者](../../../../docs/framework/data/adonet/data-providers.md)和[擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)。  
  
### <a name="the-dataset"></a>DataSet  
 ADO.NET `DataSet` 的設計已明確指出它可獨立於任何資料來源外而存取資料。 因此，它可與多個不同的資料來源搭配使用、與 XML 資料搭配使用，或用來管理應用程式的本機資料。 `DataSet` 包含一或多個由資料列和資料行所組成的 <xref:System.Data.DataTable> 物件集合，以及 `DataTable` 物件中的主索引鍵、外部索引鍵、條件約束 (Constraint) 及資料的關聯資訊。 如需詳細資訊，請參閱[資料集、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。  
  
 下圖將說明 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者與 `DataSet` 之間的關聯性。  
  
 ![ADO.Net 圖形](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET 架構  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>選擇 DataReader 或 DataSet  
 當您決定您的應用程式應該要使用`DataReader`(請參閱[使用擷取資料 DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) 或`DataSet`(請參閱[資料集、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md))，考慮的類型應用程式所需的功能。 請使用 `DataSet` 來進行下列作業：  
  
-   請快取應用程式本機的資料，如此您才能夠管理它。 若您只需要讀取查詢結果，`DataReader` 將是比較理想的選擇。  
  
-   在各層間或從 XML Web Service 遠端處理資料。  
  
-   與資料動態互動 (例如繫結 Windows Form 控制項)，或是將來自多個來源的資料合併和關聯。  
  
-   針對資料進行廣泛處理，並不需要與資料來源間有開放連接，如此便可將連接釋放給其他用戶端使用。  
  
 如果您不需要 `DataSet` 所提供的功能，則可採用 `DataReader` 以順向、唯讀的方式來傳回資料，藉以提升應用程式的效能。 雖然`DataAdapter`使用`DataReader`填滿的內容`DataSet`(請參閱[填入資料集從 DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md))，使用`DataReader`，因為您將會節省記憶體，您就可以提高效能會由`DataSet`，並避免的處理，才能建立並填入內容`DataSet`。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet 會針對在 DataSet 物件中快取的資料提供查詢功能和編譯階段型別檢查。 它可讓您使用其中一種 .NET Framework 開發語言 (例如 C# 或 Visual Basic) 來撰寫查詢。 如需詳細資訊，請參閱 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL 可針對對應到關聯式資料庫資料結構的物件模型進行查詢，而不必使用中繼的概念模型。 每個資料表都是由個別的類別表示，將物件模型與關聯式資料庫結構描述緊密結合。 LINQ to SQL 會將物件模型中的 Language-Integrated Query 轉譯成 Transact-SQL，然後將其傳送至資料庫進行執行。 當資料庫傳回結果時，LINQ to SQL 會將結果轉譯回物件。 如需詳細資訊，請參閱 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework 的設計目標是要讓開發人員針對概念應用程式模型進行程式設計來建立資料存取應用程式，而不用直接對關聯式儲存結構描述進行程式設計。 其目的是要減少資料導向應用程式所需程式碼和維護的工作量。 如需詳細資訊，請參閱[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)。  
  
## <a name="wcf-data-services"></a>WCF 資料服務  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 是用於在 Web 或內部網路上部署資料服務。 系統會根據實體資料模型的規格，讓資料結構化成實體與關聯性。 部署在這個模型上的資料可由標準 HTTP 通訊協定定址。 如需詳細資訊，請參閱[WCF 資料服務 4.5](../../../../docs/framework/data/wcf/index.md)。  
  
## <a name="xml-and-adonet"></a>XML 和 ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 會利用 XML 的功能，以中斷連接的方式存取資料。 在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中，已將 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 和 XML 類別設計得相當緊密，因為這兩者都是同一個架構上的元件。  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 和 XML 類別的交集在於 `DataSet` 物件。 `DataSet` 可以填入 XML 來源的資料，無論它是檔案或 XML 資料流都一樣。 不管 `DataSet` 的資料來源為何，`DataSet` 都可組合成與全球資訊網協會 (W3C) 相容的 XML，而且包含其結構描述當做 XML 結構描述定義語言 (XSD) 結構描述。 由於 `DataSet` 的原生序列化格式是 XML，所以相當適合當做在各層之間移動資料的媒體，如此當需要在遠端對 XML Web Service 來回傳送資料和結構描述內容時，`DataSet` 將會是最佳選擇。 如需詳細資訊，請參閱 [XML 文件和資料](../../../../docs/standard/data/xml/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
