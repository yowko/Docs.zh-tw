---
title: 作法：連接到資料庫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 48ff4af2c881104d5699910e20ef86eea0466d2a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793856"
---
# <a name="how-to-connect-to-a-database"></a>HOW TO：連接到資料庫
<xref:System.Data.Linq.DataContext> 是主要管道，您可以透過該管道連接至資料庫、擷取資料庫中的物件，以及將變更送回給資料庫。 您可以使用<xref:System.Data.Linq.DataContext> ，就像使用 ADO.NET <xref:System.Data.SqlClient.SqlConnection>一樣。 事實上，<xref:System.Data.Linq.DataContext> 是使用您所提供的連接或連接字串 (Connection String) 來初始化。 如需詳細資訊，請參閱[DataCoNtext 方法（O/R 設計工具）](/visualstudio/data-tools/datacontext-methods-o-r-designer)。  
  
 <xref:System.Data.Linq.DataContext> 的用途是將物件的要求轉譯為針對資料庫進行的 SQL 查詢，然後再從結果中組合物件。 <xref:System.Data.Linq.DataContext> 會實作與標準查詢運算子 (如 [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] 和 `Where`) 相同的運算子模式，來啟用 `Select`。  
  
> [!IMPORTANT]
> 維護安全的連接是最重要的事。 如需詳細資訊，請參閱[LINQ to SQL 中的安全性](security-in-linq-to-sql.md)。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Data.Linq.DataContext> 是用來連接至 Northwind 範例資料庫，以及擷取城市為倫敦 (London) 之客戶的資料列。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 使用實體類別來識別每個資料庫資料表，這樣每個資料庫資料表會以透過 `Table` 方法取得的 <xref:System.Data.Linq.DataContext.GetTable%2A> 集合表示。  
  
## <a name="example"></a>範例  
 最佳做法是宣告強型別 (Strongly Typed) <xref:System.Data.Linq.DataContext>，而不是依賴基本 <xref:System.Data.Linq.DataContext> 類別和 <xref:System.Data.Linq.DataContext.GetTable%2A> 方法。 強型別 <xref:System.Data.Linq.DataContext> 會將所有 `Table` 集合宣告為內容的成員 (如下列範例所示)。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 接著，您可以用下列更簡單的方式表示針對倫敦 (London) 客戶的查詢：  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [與資料庫通訊](communicating-with-the-database.md)
