---
title: 作法：將資料表表示為類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781755"
---
# <a name="how-to-represent-tables-as-classes"></a>作法：將資料表表示為類別
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 使用屬性來指定類別，做為與資料庫資料表相關<xref:System.Data.Linq.Mapping.TableAttribute>聯的實體類別。  
  
### <a name="to-map-a-class-to-a-database-table"></a>若要將類別對應至資料庫資料表  
  
- 將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性加入至類別宣告。  
  
## <a name="example"></a>範例  
 下列程式碼所建立的 `Customer` 類別，可做為與 `Customers` 資料庫資料表相關聯的實體類別。  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性。 如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
- [如何：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
