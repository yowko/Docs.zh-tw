---
title: 如何：對應資料庫關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148370"
---
# <a name="how-to-map-database-relationships"></a>如何：對應資料庫關聯性
您可以將任何永遠相同的資料關聯性 (Relationship)，編碼成為實體類別 (Entity Class) 中的屬性參考。 例如，在 Northwind 範例資料庫中，因為客戶往往會下單，所以模型中的客戶與其訂單之間一定有關聯性。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]定義屬性<xref:System.Data.Linq.Mapping.AssociationAttribute>以説明表示此類關係。 這個屬性會與 <xref:System.Data.Linq.EntitySet%601> 和 <xref:System.Data.Linq.EntityRef%601> 型別一起使用，以表示資料庫中的外部索引鍵關聯性為何。 有關詳細資訊，請參閱[基於屬性對應](attribute-based-mapping.md)的關聯屬性部分。  
  
> [!NOTE]
> AssociationAttribute 和 ColumnAttribute Storage 屬性值會區分大小寫。 例如，請確定用於 AssociationAttribute.Storage 屬性 (Property) 之屬性 (Attribute) 中的值與用於程式碼中其他位置之對應屬性 (Property) 名稱的大小寫相符。 這適用于所有 .NET 程式設計語言，即使是那些通常不區分大小寫的語言，包括 Visual Basic。 如需 Storage 屬性的詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>。  
  
 如本主題後面的範例所示，大部分關聯性都是一對多關聯性 (One-To-Many Relationship)。 您也可以表示一對一關聯性 (One-To-One Relationship) 和多對多關聯性 (Many-To-Many Relationship)，如下所示：  
  
- 一對一：同時在兩邊包含 <xref:System.Data.Linq.EntitySet%601>，以表示這種關聯性。  
  
     例如，考慮創建的關係`Customer`-`SecurityCode`，以便不會在`Customer`表中找到客戶的安全代碼，並且只能由授權人員訪問。  
  
- 多對多：在多對多關係中，連結表的主鍵（也稱為*交匯點*表）通常由其他兩個表中的外鍵組合組成。  
  
     例如`Employee`-`Project`，考慮使用連結表`EmployeeProject`形成的多對多關係。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 要求使用下列三個類別塑造此種關聯性：`Employee`、`Project` 和 `EmployeeProject`。 在此情況下，變更 `Employee` 和 `Project` 之間的關聯性，似乎需要更新主索引鍵 `EmployeeProject`。 但是，刪除現有的 `EmployeeProject` 再建立新的 `EmployeeProject` 時，其實最能模擬此種情況。  
  
    > [!NOTE]
    > 關聯式資料庫中的關聯性通常會塑造成需參考其他資料表中主索引鍵的外部索引鍵值。 要在它們之間導航，請使用關係*聯接*操作顯式關聯兩個表。  
    >
    >  另一[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]方面，使用屬性引用或使用*點*標記法導航的引用集合來相互引用。  
  
## <a name="example"></a>範例  
 在下列一對多範例中，`Customer` 類別有個屬性會宣告客戶與其訂單之間的關聯性。  `Orders` 屬性是 <xref:System.Data.Linq.EntitySet%601> 型別。 這種型別表示這種關聯性為一對多 (一個客戶對多個訂單) 的關聯性。 <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> 屬性用於描述如何達成此種關聯，那就是指定相關類別中的屬性名稱與這個屬性名稱進行比較。 在此示例中，將比較`CustomerID`該屬性，就像資料庫*聯接*將比較該列值一樣。  
  
> [!NOTE]
> 如果使用 Visual Studio，則可以使用物件關係設計器在類之間創建關聯。  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>範例  
 您也可以反轉這種情況。 您可以使用 `Customer` 類別，而不要使用 `Order` 類別來描述客戶和訂單之間的關聯。 `Order` 類別會使用 <xref:System.Data.Linq.EntityRef%601> 型別來描述客戶的反向關聯性，如下列程式碼範例所示。  
  
> [!NOTE]
> 類<xref:System.Data.Linq.EntityRef%601>支援*延遲載入*。 有關詳細資訊，*請參閱*[延遲載入與立即載入](deferred-versus-immediate-loading.md)。  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [如何：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
