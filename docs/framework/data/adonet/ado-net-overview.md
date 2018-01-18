---
title: "ADO.NET 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0857df4e4f7e12f78af6b91a76022bcaf94cc027
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-overview"></a>ADO.NET 概觀
ADO.NET 可讓您以一致的方式存取資料來源 (例如 SQL Server 與 XML)，以及透過 OLE DB 和 ODBC 所公開的資料來源。 資料共用的消費者應用程式可使用 ADO.NET 來連接至這些資料來源，並且擷取、處理及更新其中所含的資料。  
  
 ADO.NET 可將資料管理的資料存取分成不連續的元件，這些元件可分開使用，也可串聯使用。 ADO.NET 也包含 .NET Framework 資料提供者，以用於連接資料庫、執行命令和擷取結果。 這些結果會直接處理、放入 ADO.NET <xref:System.Data.DataSet> 物件中以便利用臨機操作 (Ad Hoc) 的方式公開給使用者、與多個來源的資料結合，或在各層之間進行傳遞。 `DataSet` 物件也可以與 .NET Framework 資料提供者分開使用，以便管理應用程式本機的資料或來自 XML 的資料。  
  
 ADO.NET 類別 (Class) 位於 System.Data.dll 中，而且會與 System.Xml.dll 中的 XML 類別整合。 範例程式碼連接至資料庫時，擷取資料，然後顯示該資料在主控台視窗中，請參閱[ADO.NET 程式碼範例](../../../../docs/framework/data/adonet/ado-net-code-examples.md)。  
  
 ADO.NET 可為撰寫 Managed 程式碼的開發人員提供類似於 ActiveX Data Objects (ADO) 提供給原生元件物件模型 (Component Object Model，COM) 開發人員的功能。 我們建議您使用 ADO.NET (而非 ADO) 來存取 .NET 應用程式中的資料。  
  
 ADO.NET 會提供最直接的方法，讓您在 .NET Framework 中進行資料存取。 較高層級的抽象概念，可讓應用程式來處理針對概念模型，而不是基礎儲存體模型，請參閱[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)。  
  
 **隱私權聲明**: System.Data.dll、 System.Data.Design.dll、 System.Data.OracleClient.dll、 System.Data.SqlXml.dll、 System.Data.Linq.dll、 System.Data.SqlServerCe.dll 和 System.Data.DataSetExtensions.dll 組件不相符區分使用者的私用資料和非私用資料。  這些組件不會收集、儲存或傳輸任何使用者的私用資料。 不過，協力廠商應用程式可能會使用這些組件來收集、儲存或傳輸使用者的私用資料。  
  
## <a name="in-this-section"></a>本節內容  
 [ADO.NET 架構](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 提供 ADO.NET 架構和元件的概觀。  
  
 [ADO.NET 技術選項和方針](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 說明實體資料平台隨附的產品和技術。  
  
 [LINQ 和 ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 說明如何在 ADO.NET 中實作 Language-Integrated Query (LINQ)，並且提供相關主題的連結。  
  
 [.NET Framework 資料提供者](../../../../docs/framework/data/adonet/data-providers.md)  
 提供 .NET Framework 資料提供者的設計概觀，以及 ADO.NET 所包含的 .NET Framework 資料提供者概觀。  
  
 [ADO.NET 資料集](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 提供 `DataSet` 設計與元件的概觀。  
  
 [ADO.NET 中的並存執行](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 討論各個 ADO.NET 版本之間的差異，以及它們在並存執行與應用程式相容性上的影響。  
  
 [ADO.NET 程式碼範例](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 提供使用 ADO.NET 資料提供者來擷取資料的程式碼範例。  
  
## <a name="related-sections"></a>相關章節  
 [ADO.NET 的新功能](../../../../docs/framework/data/adonet/whats-new.md)  
 簡介 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 的新功能。  
  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 說明使用 ADO.NET 的安全程式碼撰寫實施方針。  
  
 [ADO.NET 中的資料類型對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 說明 .NET Framework 資料型別與 .NET Framework 資料提供者之間的資料型別對應。  
  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 說明如何連接至資料來源、擷取資料和修改資料。 這包括 `DataReaders` 和 `DataAdapters`。  
  
## <a name="see-also"></a>請參閱  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
