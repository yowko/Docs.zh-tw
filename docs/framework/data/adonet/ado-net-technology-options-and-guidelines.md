---
title: ADO.NET 技術選項和方針
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 106fdbc121c3b1c15aaced5e0314e0651387cede
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="adonet-technology-options-and-guidelines"></a>ADO.NET 技術選項和方針
ADO.NET 資料平台是一種多重發行策略，可讓開發人員針對概念實體資料模型進行程式設計，藉以減少所需程式碼和維護的工作量。 這個平台包含 ADO.NET Entity Framework 和相關的技術。  
  
## <a name="entity-framework"></a>Entity Framework  
 ADO.NET Entity Framework 的設計目標是要讓開發人員針對概念應用程式模型進行程式設計來建立資料存取應用程式，而不用直接對關聯式儲存結構描述進行程式設計。 其目的是要減少資料導向應用程式所需程式碼和維護的工作量。 如需詳細資訊，請參閱[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)。  
  
### <a name="entity-data-model-edm"></a>實體資料模型 (EDM)  
 實體資料模型 (EDM) 是將應用程式資料定義成實體與關聯性集合的設計規格。 這個模型中的資料支援跨應用程式界限的物件關聯式對應與資料可程式性。  
  
### <a name="object-services"></a>物件服務  
 物件服務允許程式設計人員透過 Common Language Runtime (CLR) 類別的集合，與概念模型進行互動。 這些類別可自動從概念模型產生或獨立開發，以便反映概念模型的結構。 物件服務也會針對 Entity Framework 提供基礎結構支援，包括一些服務，例如狀態管理、變更追蹤、識別解析、載入和瀏覽關聯性、將物件變更傳播至資料庫修改，以及 Entity SQL 的查詢建立支援。 如需詳細資訊，請參閱[物件服務概觀 (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038)。  
  
### <a name="linq-to-entities"></a>LINQ to Entities  
 LINQ to Entities 是 Language-integrated Query (LINQ) 實作 (Implementation)，可讓開發人員使用 LINQ 運算式和 LINQ 標準查詢運算子，針對 Entity Framework 物件內容建立強型別 (Strongly Typed) 查詢。 LINQ to Entities 可讓開發人員使用跨 Microsoft SQL Server 與協力廠商資料庫之非常彈性的物件關聯式對應，處理概念模型。 如需詳細資訊，請參閱[LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)。  
  
### <a name="entity-sql"></a>Entity SQL  
 Entity SQL 是設計成與實體資料模型互動之以文字為基礎的查詢語言。 Entity SQL 是一種 SQL Dialect，其中包含以較高層級模型概念進行查詢的建構，例如繼承 (Inheritance)、複雜類型和明確關聯性。 開發人員也可以直接使用 Entity SQL 搭配物件服務。 如需詳細資訊，請參閱[Entity SQL 語言](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)。  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient 是用於與實體資料模型互動的新 .NET Framework 資料提供者 (Data Provider)。 EntityClient 會遵循公開 (Expose) 可傳回 <xref:System.Data.EntityClient.EntityConnection> 之 <xref:System.Data.EntityClient.EntityCommand> 和 <xref:System.Data.EntityClient.EntityDataReader> 物件的 .NET Framework 資料提供者模式。 EntityClient 會使用 Entity SQL 語言，並提供彈性的對應給儲存體特有的資料提供者。 如需詳細資訊，請參閱[EntityClient 和 Entity SQL](http://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527)。  
  
### <a name="entity-data-model-tools"></a>實體資料模型工具  
 Entity Framework 會提供一些命令列工具、精靈和設計工具來協助您建立 EDM 應用程式。 EntityDataSource 控制項支援以 EDM 為基礎的資料繫結案例。 EntityDataSource 控制項的程式設計介面與 Visual Studio 中的其他資料來源控制項很相似。 如需詳細資訊，請參閱[ADO.NET 實體資料模型工具](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL 是物件關聯式對應 (OR/M) 實作，可讓您透過使用 .NET Framework 類別將 SQL Server 資料庫製成模型。 LINQ to SQL 可讓您使用 LINQ 來查詢資料庫，以及在其中更新、插入和刪除資料。 LINQ to SQL 支援交易、檢視表和預存程序，也是您將資料驗證及商務邏輯整合到資料模型時可用的簡易方法。 您可以使用物件關聯式設計工具 (O/R 設計工具)，將以資料庫之物件為基礎的實體類別和關聯製成模型。 如需詳細資訊，請參閱 [Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。  
  
## <a name="wcf-data-services"></a>WCF 資料服務  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會在 Web 或內部網路上部署資料服務。 系統會根據實體資料模型的規格，讓資料結構化成實體與關聯性。 部署在這個模型上的資料可由標準 HTTP 通訊協定定址。 如需詳細資訊，請參閱[WCF 資料服務 4.5](../../../../docs/framework/data/wcf/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET 的新功能](../../../../docs/framework/data/adonet/whats-new.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
