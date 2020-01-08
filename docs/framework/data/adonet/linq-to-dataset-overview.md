---
title: LINQ to DataSet 概觀
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 20d9be052ba2567c16718b4b1c1019427c9b5df1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634816"
---
# <a name="linq-to-dataset-overview"></a>LINQ to DataSet 概觀
<xref:System.Data.DataSet> 是 ADO.NET 中更廣泛使用的元件之一。 它是已中斷連線之程式設計模型的重要元素，ADO.NET 是以為基礎，可讓您明確地快取來自不同資料來源的資料。 若為展示層，<xref:System.Data.DataSet> 會與 GUI 控制項緊密整合，以便進行資料繫結 (Data Binding)。 若為中介層 (Middle Tier)，它會提供保留關聯式資料圖案的快取，而且包含快速簡易查詢和階層導覽服務。 用來降低資料庫要求數目的常見技術是使用 <xref:System.Data.DataSet> 在仲介層進行快取。 例如，假設有一個資料驅動的 ASP.NET Web 應用程式。 通常，應用程式資料的重要部分不會經常變更，而且在工作階段 (Session) 或使用者之間是通用的。 這項資料可以保留在 Web 伺服器的記憶體中，以便減少針對資料庫所進行的要求數目並加快使用者互動的速度。 <xref:System.Data.DataSet> 的另一個有用層面，就是它可讓應用程式將一或多個資料來源中的資料子集帶入應用程式空間。 然後，此應用程式就可以管理記憶體中資料，同時保留其關聯式圖案。  
  
 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。 <xref:System.Data.DataTable.Select%2A> 方法可用於篩選和排序，而 <xref:System.Data.DataRow.GetChildRows%2A> 和 <xref:System.Data.DataRow.GetParentRow%2A> 方法可用於階層導覽。 不過，若要進行更複雜的作業，開發人員就必須撰寫自訂查詢。 這樣做可能會產生執行效能較低而且難以維護的應用程式。  
  
 LINQ to DataSet 可讓您更輕鬆且更快速地查詢 <xref:System.Data.DataSet> 物件中快取的資料。 這些查詢是以程式語言本身表示，而非以內嵌於應用程式程式碼中的字串常值 (String Literal) 表示。 這表示，開發人員不需要學習不同的查詢語言。 此外，LINQ to DataSet 可讓 Visual Studio 的開發人員更有效率地工作，因為 Visual Studio IDE 會針對 LINQ 提供編譯時間語法檢查、靜態型別和 IntelliSense 支援。 LINQ to DataSet 也可以用來查詢已從一個或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>使用 LINQ to DataSet 來查詢 DataSet  
 您必須先填入 <xref:System.Data.DataSet>，才能開始使用 LINQ to DataSet 來查詢 <xref:System.Data.DataSet> 物件。 有數種方式可以將資料載入 <xref:System.Data.DataSet>，例如使用 <xref:System.Data.Common.DataAdapter> 類別或[LINQ to SQL](./sql/linq/index.md)。 將資料載入 <xref:System.Data.DataSet> 物件之後，您就可以開始查詢它。 使用 LINQ to DataSet 來編寫查詢，類似于針對其他啟用 LINQ 的資料來源使用語言整合式查詢（LINQ）。 您可以使用 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A> 標準查詢運算子，針對 <xref:System.Data.DataSet> 中的單一資料表或多個資料表執行 LINQ 查詢。  
  
 針對具類型和不具類型的 <xref:System.Data.DataSet> 物件，都支援 LINQ 查詢。 如果在應用程式設計階段中便已知 <xref:System.Data.DataSet> 的結構描述，建議您使用具型別 <xref:System.Data.DataSet>。 在具型別 <xref:System.Data.DataSet> 中，資料表和資料列會具有每個資料行的具型別成員，進而讓查詢更簡單且更方便讀取。  
  
 除了在 system.string 中實作為標準查詢運算子之外，LINQ to DataSet 新增數個 <xref:System.Data.DataSet>特定的擴充功能，讓您更輕鬆地對一組 <xref:System.Data.DataRow> 物件進行查詢。 這些 <xref:System.Data.DataSet> 專用的延伸模組包括比較資料列序列的運算子，以及可讓您存取 <xref:System.Data.DataRow> 之資料行值的方法。  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N-Tier 應用程式和 LINQ to DataSet  
 「多層式架構資料應用程式」(N-tier data application) 是以資料為主而且分成多個邏輯層 (或「層級」(tier)) 的應用程式。 一般的 N-Tier 應用程式包含展示層、中介層和資料層。 將應用程式元件分隔成不同的層級會提升應用程式的可維護性和延展性 (Scalability)。 如需多層式資料應用程式的詳細資訊，請參閱[在多層式應用程式中使用資料集](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)。  
  
 在 N-Tier 應用程式中，<xref:System.Data.DataSet> 通常會用於中介層，以便快取 Web 應用程式的資訊。 LINQ to DataSet 查詢功能是透過擴充方法來執行，並擴充現有的 ADO.NET 2.0 <xref:System.Data.DataSet>。  
  
## <a name="see-also"></a>請參閱

- [查詢資料集](querying-datasets-linq-to-dataset.md)
- [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
