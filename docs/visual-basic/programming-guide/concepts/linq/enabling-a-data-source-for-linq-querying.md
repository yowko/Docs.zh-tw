---
title: "啟用資料來源的 LINQ Querying2 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34bdc4e056d982799eac35eb2398dd3f23f6f351
ms.lasthandoff: 03/13/2017

---
# <a name="enabling-a-data-source-for-linq-querying"></a>啟用資料來源以進行 LINQ 查詢
有很多方法來擴充[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]啟用任何資料來源進行查詢[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]模式。 資料來源可能是資料結構、Web 服務、檔案系統或資料庫等等。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 模式可以讓用戶端輕鬆查詢已啟用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢的資料來源，因為查詢的語法和模式並未改變。 方式[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]可以擴充至這些資料來源包括下列︰  
  
-   實作<xref:System.Collections.Generic.IEnumerable%601>介面中輸入，以啟用[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]to Objects 查詢該型別的。</xref:System.Collections.Generic.IEnumerable%601>  
  
-   例如，建立標準查詢運算子方法<xref:System.Linq.Enumerable.Where%2A>和<xref:System.Linq.Enumerable.Select%2A>擴充型別，若要啟用自訂[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]該類型的查詢。</xref:System.Linq.Enumerable.Select%2A> </xref:System.Linq.Enumerable.Where%2A>  
  
-   建立資料來源實作的提供者<xref:System.Linq.IQueryable%601>介面。</xref:System.Linq.IQueryable%601> 實作此介面的提供者是以運算式樹狀架構的形式接收 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢，而它可以自訂方式 (例如從遠端) 執行這些查詢。  
  
-   建立您利用現有的資料來源的提供者[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]技術。 這種提供者不只會啟用查詢功能，也會插入、更新及刪除使用者定義類型的作業和對應。  
  
 本主題將討論這些選項。  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>如何啟用資料來源的 LINQ 查詢功能  
  
### <a name="in-memory-data"></a>記憶體中的資料  
 有兩種方式，您可以啟用[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]記憶體中資料的查詢。 如果資料是實作之型別的<xref:System.Collections.Generic.IEnumerable%601>，您可以藉由查詢資料[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]物件。</xref:System.Collections.Generic.IEnumerable%601> 如果它毫無意義，以啟動列舉型別之型別實作<xref:System.Collections.Generic.IEnumerable%601>介面，您可以定義[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]標準查詢運算子方法，該型別中的，或是建立[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]可擴充類型的標準查詢運算子方法。</xref:System.Collections.Generic.IEnumerable%601> 標準查詢運算子的自訂實作 (Implementation) 應該會使用延後執行 (Deferred Execution) 來傳回結果。  
  
### <a name="remote-data"></a>遠端資料  
 啟用的最佳選項[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]遠端資料來源的查詢是實作<xref:System.Linq.IQueryable%601>介面。</xref:System.Linq.IQueryable%601> 不過，這與擴充資料來源之提供者 (例如 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]) 不同。 不含任何提供者模型擴充現有[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]技術，例如[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]至其他資料來源類型可用於[!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)]。  
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ 提供者  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]實作提供者，<xref:System.Linq.IQueryable%601>可能大不相同在複雜度。</xref:System.Linq.IQueryable%601> 本節將討論不同層次的複雜度。  
  
 複雜度較低的 `IQueryable` 提供者可能會與 Web 服務的單一方法互動。 這種類型的提供者非常特別，因為它預期本身所處理的查詢中應該有特定的資訊。 這種提供者具有封閉類型系統，可能會公開單一結果類型。 大部分的查詢執行在本機進行，例如使用<xref:System.Linq.Enumerable>標準查詢運算子的實作。</xref:System.Linq.Enumerable> 複雜度較低的提供者可能只會在代表查詢的運算式樹狀架構中檢查一個方法呼叫運算式，並讓查詢的其餘邏輯在其他地方處理。  
  
 複雜度中等的 `IQueryable` 提供者可能以具有部分表示查詢語言的資料來源為目標。 若以 Web 服務做為目標，則其可能與該 Web 服務的多個方法連結，並依據查詢所提出的問題來選取要呼叫的方法。 中等複雜度的提供者擁有的類型系統雖然比簡單提供者更為多樣化，但仍然為固定類型系統。 例如，提供者可能會公開具有可周遊的一對多關聯性 (One-To-Many Relationship)，但卻不會提供使用者定義類型的對應。  
  
 複雜的 `IQueryable` 提供者 (例如 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 提供者) 可能會將完整的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢解譯成表示查詢語言，例如 SQL。 複雜的提供者比複雜度較低的提供者更為廣泛，因為它可以在查詢中處理更多種類的問題。 它也具有開放類型系統，因此必須包含廣泛的基礎結構，以對應使用者定義的類型。 開發複雜的提供者需要花費相當大量的心力。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.IQueryable%601></xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
