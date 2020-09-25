---
title: 啟用資料來源以進行 LINQ 查詢
description: '瞭解如何在 c # 中擴充 LINQ，讓任何資料來源能夠使用 LINQ 模式進行查詢，讓用戶端可以輕鬆地查詢資料來源。'
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: d7d751c0584072e740b4e5292071e400a5020f82
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202613"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>啟用資料來源以進行 LINQ 查詢

有多種方式可以擴充 LINQ，讓任何資料來源可在 LINQ 模式中進行查詢。 資料來源可能是資料結構、Web 服務、檔案系統或資料庫等等。 LINQ 模式方便用戶端查詢已啟用 LINQ 查詢的資料來源，因為查詢的語法和模式不會變更。 LINQ 可以擴充至這些資料來源的方式包括下列各項：  
  
- <xref:System.Collections.Generic.IEnumerable%601>在類型中執行介面，以啟用該類型的 LINQ to Objects 查詢。  
  
- 建立擴充類型的標準查詢運算子方法（例如 <xref:System.Linq.Enumerable.Where%2A> 和 <xref:System.Linq.Enumerable.Select%2A> ），以啟用該類型的自訂 LINQ 查詢。  
  
- 為資料來源建立實作 <xref:System.Linq.IQueryable%601> 介面的提供者。 實作為此介面的提供者會以運算式樹狀架構的形式接收 LINQ 查詢，它可以用自訂方式（例如遠端）執行。  
  
- 為數據源建立利用現有 LINQ 技術的提供者。 這種提供者不只會啟用查詢功能，也會插入、更新及刪除使用者定義類型的作業和對應。  
  
 本主題將討論這些選項。  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>如何啟用資料來源的 LINQ 查詢功能  
  
### <a name="in-memory-data"></a>記憶體中的資料  

 您可以使用兩種方式來啟用記憶體中資料的 LINQ 查詢。 如果資料是實作為的型別 <xref:System.Collections.Generic.IEnumerable%601> ，您可以使用 LINQ to Objects 來查詢資料。 如果透過實作為型別來啟用型別的列舉並不合理 <xref:System.Collections.Generic.IEnumerable%601> ，您可以在該型別中定義 linq 標準查詢運算子方法，或是建立可延伸型別的 linq 標準查詢運算子方法。 標準查詢運算子的自訂實作 (Implementation) 應該會使用延後執行 (Deferred Execution) 來傳回結果。  
  
### <a name="remote-data"></a>遠端資料  

 啟用遠端資料源之 LINQ 查詢的最佳選項是執行 <xref:System.Linq.IQueryable%601> 介面。 不過，這與擴充資料來源之提供者 (例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) 不同。 在 Visual Studio 2008 中，沒有任何提供者模型可用來將現有的 LINQ 技術（例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ）擴充至其他資料來源類型。
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ 提供者  

 執行的 LINQ 提供者 <xref:System.Linq.IQueryable%601> 在其複雜性上可能會有很大的差異。 本節將討論不同層次的複雜度。  
  
 複雜度較低的 `IQueryable` 提供者可能會與 Web 服務的單一方法互動。 這種類型的提供者非常特別，因為它預期本身所處理的查詢中應該有特定的資訊。 這種提供者具有封閉類型系統，可能會公開單一結果類型。 多數的查詢執行工作都是在本機進行，例如利用標準查詢運算子的 <xref:System.Linq.Enumerable> 實作。 複雜度較低的提供者可能只會在代表查詢的運算式樹狀架構中檢查一個方法呼叫運算式，並讓查詢的其餘邏輯在其他地方處理。  
  
 複雜度中等的 `IQueryable` 提供者可能以具有部分表示查詢語言的資料來源為目標。 若以 Web 服務做為目標，則其可能與該 Web 服務的多個方法連結，並依據查詢所提出的問題來選取要呼叫的方法。 中等複雜度的提供者擁有的類型系統雖然比簡單提供者更為多樣化，但仍然為固定類型系統。 例如，提供者可能會公開具有可周遊的一對多關聯性 (One-To-Many Relationship)，但卻不會提供使用者定義類型的對應。  
  
 複雜的 `IQueryable` 提供者（例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 提供者）可能會將完整的 LINQ 查詢轉譯成表達查詢語言，例如 SQL。 複雜的提供者比複雜度較低的提供者更為廣泛，因為它可以在查詢中處理更多種類的問題。 它也具有開放類型系統，因此必須包含廣泛的基礎結構，以對應使用者定義的類型。 開發複雜的提供者需要花費相當大量的心力。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
