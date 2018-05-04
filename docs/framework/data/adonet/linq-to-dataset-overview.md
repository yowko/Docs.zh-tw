---
title: LINQ to DataSet 概觀
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: d269ea2899ffd8005aad9912cf9273a012e13edd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet 概觀
<xref:System.Data.DataSet> 是其中一個常用的 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 元件。 它是 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 所依據之中斷連接程式撰寫模型 (Programming Model) 的重要項目，而且可讓您明確快取來自不同資料來源的資料。 若為展示層，<xref:System.Data.DataSet> 會與 GUI 控制項緊密整合，以便進行資料繫結 (Data Binding)。 若為中介層 (Middle Tier)，它會提供保留關聯式資料圖案的快取，而且包含快速簡易查詢和階層導覽服務。 較低的資料庫上的要求數目常用的技巧是使用<xref:System.Data.DataSet>的中介層的快取。 例如，請考慮資料導向[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 應用程式。 通常，應用程式資料的重要部分不會經常變更，而且在工作階段 (Session) 或使用者之間是通用的。 這項資料可以保留在 Web 伺服器的記憶體中，以便減少針對資料庫所進行的要求數目並加快使用者互動的速度。 另一個有用的層面<xref:System.Data.DataSet>是它可讓應用程式從一個或多個資料來源的資料子集帶入應用程式空間。 然後，此應用程式就可以管理記憶體中資料，同時保留其關聯式圖案。  
  
 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。 <xref:System.Data.DataTable.Select%2A> 方法可用於篩選和排序，而 <xref:System.Data.DataRow.GetChildRows%2A> 和 <xref:System.Data.DataRow.GetParentRow%2A> 方法可用於階層導覽。 不過，若要進行更複雜的作業，開發人員就必須撰寫自訂查詢。 這樣做可能會產生執行效能較低而且難以維護的應用程式。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。 這些查詢是以程式語言本身表示，而非以內嵌於應用程式程式碼中的字串常值 (String Literal) 表示。 這表示，開發人員不需要學習不同的查詢語言。 此外，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]可讓 Visual Studio 開發人員更有效率地工作，因為 Visual Studio IDE 提供編譯時期語法檢查、 靜態型別和 IntelliSense 支援[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也可用來查詢已經從一個或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>使用 LINQ to DataSet 來查詢 DataSet  
 您必須先填入 (Populate) <xref:System.Data.DataSet>，然後才能開始使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來查詢 <xref:System.Data.DataSet> 物件。 有數種方法，將資料載入<xref:System.Data.DataSet>，例如使用<xref:System.Data.Common.DataAdapter>類別或[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。 將資料載入之後<xref:System.Data.DataSet>物件，您可以開始查詢它。 來編寫查詢使用[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]類似於使用[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]針對其他[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-啟用資料來源。 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 針對中的單一資料表執行查詢<xref:System.Data.DataSet>或針對多個資料表使用<xref:System.Linq.Enumerable.Join%2A>和<xref:System.Linq.Enumerable.GroupJoin%2A>標準查詢運算子。  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 支援針對具型別和不具類型的查詢<xref:System.Data.DataSet>物件。 如果在應用程式設計階段中便已知 <xref:System.Data.DataSet> 的結構描述，建議您使用具型別 <xref:System.Data.DataSet>。 在具型別 <xref:System.Data.DataSet> 中，資料表和資料列會具有每個資料行的具型別成員，進而讓查詢更簡單且更方便讀取。  
  
 除了 System.Core.dll 中實作的標準查詢運算子[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]加入了許多<xref:System.Data.DataSet>-專用的延伸模組，讓它更容易查詢一組<xref:System.Data.DataRow>物件。 這些 <xref:System.Data.DataSet> 專用的延伸模組包括比較資料列序列的運算子，以及可讓您存取 <xref:System.Data.DataRow> 之資料行值的方法。  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N-Tier 應用程式和 LINQ to DataSet  
 N-Tier 資料應用程式是指分隔成多個邏輯層 (或層級) 的資料中心應用程式。 一般的 N-Tier 應用程式包含展示層、中介層和資料層。 將應用程式元件分隔成不同的層級會提升應用程式的可維護性和延展性 (Scalability)。 如需多層式架構資料應用程式的詳細資訊，請參閱[處理在多層式架構應用程式中的資料集](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)。  
  
 在 N-Tier 應用程式中，<xref:System.Data.DataSet> 通常會用於中介層，以便快取 Web 應用程式的資訊。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢功能透過擴充方法實作，而且會擴充現有的 ADO.NET 2.0 <xref:System.Data.DataSet>。  
  
## <a name="see-also"></a>另請參閱  
 [查詢資料集](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
