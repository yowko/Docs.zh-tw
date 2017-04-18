---
title: "LINQ to DataSet 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# LINQ to DataSet 概觀
<xref:System.Data.DataSet> 是其中一個常用的 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 元件。 它是 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 所依據之中斷連接程式撰寫模型 \(Programming Model\) 的重要項目，而且可讓您明確快取來自不同資料來源的資料。 若為展示層，<xref:System.Data.DataSet> 會與 GUI 控制項緊密整合，以便進行資料繫結 \(Data Binding\)。 若為中介層 \(Middle Tier\)，它會提供保留關聯式資料圖案的快取，而且包含快速簡易查詢和階層導覽服務。  在資料庫上降低要求數目常用的技巧是針對中介層的快取使用 <xref:System.Data.DataSet>。  例如，請考慮使用資料驅動的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式。  通常，應用程式資料的重要部分不會經常變更，而且在工作階段 \(Session\) 或使用者之間是通用的。  這項資料可以保留在 Web 伺服器的記憶體中，以便減少針對資料庫所進行的要求數目並加快使用者互動的速度。  <xref:System.Data.DataSet> 另一個有用的層面是，它可讓應用程式將一個或多個資料來源的資料子集帶入應用程式空間中。  然後，此應用程式就可以管理記憶體中資料，同時保留其關聯式圖案。  
  
 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。  <xref:System.Data.DataTable.Select%2A> 方法可用於篩選和排序，而 <xref:System.Data.DataRow.GetChildRows%2A> 和 <xref:System.Data.DataRow.GetParentRow%2A> 方法可用於階層導覽。  不過，若要進行更複雜的作業，開發人員就必須撰寫自訂查詢。  這樣做可能會產生執行效能較低而且難以維護的應用程式。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。  這些查詢是以程式語言本身表示，而非以內嵌於應用程式程式碼中的字串常值 \(String Literal\) 表示。  這表示，開發人員不需要學習不同的查詢語言。  此外，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可提升 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 開發人員的產能，因為 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE 會針對 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 提供編譯時期語法檢查、靜態型別和 IntelliSense 支援。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也可用來查詢已經從一個或多個資料來源合併的資料。  這點可以實現許多資料表示和處理方式需要彈性的案例。  尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
## 使用 LINQ to DataSet 來查詢 DataSet  
 您必須先填入 \(Populate\) <xref:System.Data.DataSet>，然後才能開始使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來查詢 <xref:System.Data.DataSet> 物件。 目前有許多方式可以將資料載入 <xref:System.Data.DataSet> 中，例如使用 <xref:System.Data.Common.DataAdapter> 類別 \(Class\) 或 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。  當資料已經載入 <xref:System.Data.DataSet> 物件之後，您就可以開始查詢它。  使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來編寫查詢與針對其他啟用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 的資料來源使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 很相似。  您可以使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 和 <xref:System.Data.DataSet> 標準查詢運算子，針對 <xref:System.Linq.Enumerable.Join%2A> 中的單一資料表或針對一個以上的資料表執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 查詢。  
  
 目前支援針對具型別和不具型別的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 物件進行 <xref:System.Data.DataSet> 查詢。  如果在應用程式設計階段中便已知 <xref:System.Data.DataSet> 的結構描述，建議您使用具型別 <xref:System.Data.DataSet>。 在具型別 <xref:System.Data.DataSet> 中，資料表和資料列會具有每個資料行的具型別成員，進而讓查詢更簡單且更方便讀取。  
  
 除了在 System.Core.dl 中實作的標準查詢運算子以外，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 加入了許多 <xref:System.Data.DataSet> 專用的延伸模組，可讓它更容易查詢 <xref:System.Data.DataRow> 物件的集合。  這些 <xref:System.Data.DataSet> 專用的延伸模組包括比較資料列序列的運算子，以及可讓您存取 <xref:System.Data.DataRow> 之資料行值的方法。  
  
## N\-Tier 應用程式和 LINQ to DataSet  
 N\-Tier 資料應用程式是指分隔成多個邏輯層 \(或層級\) 的資料中心應用程式。  一般的 N\-Tier 應用程式包含展示層、中介層和資料層。  將應用程式元件分隔成不同的層級會提升應用程式的可維護性和延展性 \(Scalability\)。  如需 N\-Tier 資料應用程式的詳細資訊，請參閱 [使用多層式架構應用程式中的資料集](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md)。  
  
 在 N\-Tier 應用程式中，<xref:System.Data.DataSet> 通常會用於中介層，以便快取 Web 應用程式的資訊。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢功能是透過擴充方法實作的，而且會擴充現有的 ADO.NET 2.0 <xref:System.Data.DataSet>。  
  
## 請參閱  
 [查詢 DataSet](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)