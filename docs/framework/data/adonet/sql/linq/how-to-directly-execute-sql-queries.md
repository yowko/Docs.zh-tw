---
title: 作法：直接執行 SQL 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: a4971bc05b22c38790c5fd1493e70cccf5eaae16
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793778"
---
# <a name="how-to-directly-execute-sql-queries"></a>HOW TO：直接執行 SQL 查詢
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您撰寫的查詢轉譯為參數型 SQL 查詢 (文字格式)，並將它們傳送給 SQL Server 進行處理。  
  
 SQL 無法執行您應用程式可以在本機使用的各種方法。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會嘗試將這些本機方法轉換為可以在 SQL 環境內進行的對等作業和函式。 .NET Framework 內建型別的大部分方法和運算子都可以直接轉譯為 SQL 命令。 而有些方法和運算則可以透過可用的函式產生。 無法產生的部分則會產生執行階段例外狀況。 如需詳細資訊，請參閱[SQL-CLR 型別對應](sql-clr-type-mapping.md)。  
  
 如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢不足以進行特殊化工作，則可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法執行 SQL 查詢，然後將查詢結果直接轉換為物件。  
  
## <a name="example"></a>範例  
 在下列範例中，假設 `Customer` 類別的資料分佈於兩張資料表 (customer1 和 customer2)。 這個查詢會傳回 `Customer` 物件的序列。  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 只要表格式結果中的資料行名稱符合實體類別的資料行屬性， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]就會從任何 SQL 查詢建立物件。  
  
## <a name="example"></a>範例  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法也允許使用參數。 使用下列程式碼，就可以執行參數型查詢。  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 查詢文字中的參數使用與 `Console.WriteLine()` 和 `String.Format()` 所用的相同大括號標記法來表示。 事實上， `String.Format()`實際上是在您所提供的查詢字串上呼叫，並以產生的參數名稱@p0（例如， @p1 ...、 @p（n））取代大括弧參數。  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
- [查詢資料庫](querying-the-database.md)
