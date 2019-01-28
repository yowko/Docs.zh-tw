---
title: 啟用資料來源以進行 LINQ 查詢1
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: d3faeb15c5c8deedec3c3347c6317cac872224f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515715"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>啟用資料來源以進行 LINQ 查詢
您可以使用各種方式來擴充 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，以啟用要在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 模式下進行查詢的任何資料來源。 資料來源可能是資料結構、Web 服務、檔案系統或資料庫等等。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 模式可以讓用戶端輕鬆查詢已啟用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的資料來源，因為查詢的語法和模式並未改變。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 可以擴充至這些資料來源的方式包括：  
  
-   在類型中實作 <xref:System.Collections.Generic.IEnumerable%601> 介面，以啟用該類型的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects 查詢功能。  
  
-   建立可擴充類型的標準查詢運算子方法 (例如 <xref:System.Linq.Enumerable.Where%2A> 和 <xref:System.Linq.Enumerable.Select%2A>)，以啟用該類型的自訂 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢功能。  
  
-   為資料來源建立實作 <xref:System.Linq.IQueryable%601> 介面的提供者。 實作此介面的提供者是以運算式樹狀架構的形式接收 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，而它可以自訂方式 (例如從遠端) 執行這些查詢。  
  
-   為利用現有 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 技術的資料來源建立提供者。 這種提供者不只會啟用查詢功能，也會插入、更新及刪除使用者定義類型的作業和對應。  
  
 本主題將討論這些選項。  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>如何啟用資料來源的 LINQ 查詢功能  
  
### <a name="in-memory-data"></a>記憶體中的資料  
 您可以使用兩種方式來啟用記憶體中資料的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢功能。 如果資料屬於實作 <xref:System.Collections.Generic.IEnumerable%601> 的類型，您可以使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects 來查詢該資料。 如果透過實作 <xref:System.Collections.Generic.IEnumerable%601> 介面來啟用類型列舉並不合理，您可以在該類型中定義 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 標準查詢運算子方法，或是建立可擴充類型的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 標準查詢運算子方法。 標準查詢運算子的自訂實作 (Implementation) 應該會使用延後執行 (Deferred Execution) 來傳回結果。  
  
### <a name="remote-data"></a>遠端資料  
 啟用遠端資料來源之 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的最佳選擇是實作 <xref:System.Linq.IQueryable%601> 介面。 不過，這與擴充資料來源之提供者 (例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) 不同。 Visual Studio 2008 中並無任何提供者模型可用來將現有的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 技術 (例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) 延伸到其他資料來源類型。
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ 提供者  
 實作 <xref:System.Linq.IQueryable%601> 的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供者在複雜度上有很大的差異。 本節將討論不同層次的複雜度。  
  
 複雜度較低的 `IQueryable` 提供者可能會與 Web 服務的單一方法互動。 這種類型的提供者非常特別，因為它預期本身所處理的查詢中應該有特定的資訊。 這種提供者具有封閉類型系統，可能會公開單一結果類型。 多數的查詢執行工作都是在本機進行，例如利用標準查詢運算子的 <xref:System.Linq.Enumerable> 實作。 複雜度較低的提供者可能只會在代表查詢的運算式樹狀架構中檢查一個方法呼叫運算式，並讓查詢的其餘邏輯在其他地方處理。  
  
 複雜度中等的 `IQueryable` 提供者可能以具有部分表示查詢語言的資料來源為目標。 若以 Web 服務做為目標，則其可能與該 Web 服務的多個方法連結，並依據查詢所提出的問題來選取要呼叫的方法。 中等複雜度的提供者擁有的類型系統雖然比簡單提供者更為多樣化，但仍然為固定類型系統。 例如，提供者可能會公開具有可周遊的一對多關聯性 (One-To-Many Relationship)，但卻不會提供使用者定義類型的對應。  
  
 複雜的 `IQueryable` 提供者 (例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 提供者) 可能會將完整的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢解譯成表示查詢語言，例如 SQL。 複雜的提供者比複雜度較低的提供者更為廣泛，因為它可以在查詢中處理更多種類的問題。 它也具有開放類型系統，因此必須包含廣泛的基礎結構，以對應使用者定義的類型。 開發複雜的提供者需要花費相當大量的心力。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
