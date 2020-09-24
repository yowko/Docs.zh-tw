---
title: 作法：對應資料庫關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 2f612877f5e7da6442c242aa0d56d811c0aa7cf8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166452"
---
# <a name="how-to-map-database-relationships"></a>作法：對應資料庫關聯性

您可以將任何永遠相同的資料關聯性 (Relationship)，編碼成為實體類別 (Entity Class) 中的屬性參考。 例如，在 Northwind 範例資料庫中，因為客戶往往會下單，所以模型中的客戶與其訂單之間一定有關聯性。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 定義 <xref:System.Data.Linq.Mapping.AssociationAttribute> 可協助表示這類關聯性的屬性。 這個屬性會與 <xref:System.Data.Linq.EntitySet%601> 和 <xref:System.Data.Linq.EntityRef%601> 型別一起使用，以表示資料庫中的外部索引鍵關聯性為何。 如需詳細資訊，請參閱以屬性為 [基礎之對應](attribute-based-mapping.md)的 [關聯屬性] 區段。  
  
> [!NOTE]
> AssociationAttribute 和 ColumnAttribute Storage 屬性值會區分大小寫。 例如，請確定用於 AssociationAttribute.Storage 屬性 (Property) 之屬性 (Attribute) 中的值與用於程式碼中其他位置之對應屬性 (Property) 名稱的大小寫相符。 這適用于所有 .NET 程式設計語言，即使它們通常不區分大小寫，包括 Visual Basic。 如需 Storage 屬性的詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>。  
  
 如本主題後面的範例所示，大部分關聯性都是一對多關聯性 (One-To-Many Relationship)。 您也可以表示一對一關聯性 (One-To-One Relationship) 和多對多關聯性 (Many-To-Many Relationship)，如下所示：  
  
- 一對一：同時在兩邊包含 <xref:System.Data.Linq.EntitySet%601>，以表示這種關聯性。  
  
     例如，請考慮建立關聯性，如此一來，就 `Customer` - `SecurityCode` 不會在資料表中找到客戶的安全碼， `Customer` 而且只能由授權的人員存取。  
  
- 多對多：在多對多關聯性中，連結資料表的主鍵 (也命名為 *聯接* 資料表) 通常是由其他兩個數據表中的外鍵複合構成。  
  
     例如，請考慮 `Employee` - `Project` 使用連結資料表所形成的多對多關聯性 `EmployeeProject` 。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 要求使用下列三個類別塑造此種關聯性：`Employee`、`Project` 和 `EmployeeProject`。 在此情況下，變更 `Employee` 和 `Project` 之間的關聯性，似乎需要更新主索引鍵 `EmployeeProject`。 但是，刪除現有的 `EmployeeProject` 再建立新的 `EmployeeProject` 時，其實最能模擬此種情況。  
  
    > [!NOTE]
    > 關聯式資料庫中的關聯性通常會塑造成需參考其他資料表中主索引鍵的外部索引鍵值。 若要在兩者之間流覽，您可以使用關聯式 *聯結* 作業明確地建立這兩個數據表的關聯。  
    >
    >  另一方面，中的物件 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用您使用 *點* 標記法流覽的屬性參考或參考集合來彼此參考。  
  
## <a name="example"></a>範例  

 在下列一對多範例中，`Customer` 類別有個屬性會宣告客戶與其訂單之間的關聯性。  `Orders` 屬性是 <xref:System.Data.Linq.EntitySet%601> 型別。 這種型別表示這種關聯性為一對多 (一個客戶對多個訂單) 的關聯性。 <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> 屬性用於描述如何達成此種關聯，那就是指定相關類別中的屬性名稱與這個屬性名稱進行比較。 在此範例中， `CustomerID` 會比較屬性，就像資料庫 *聯結* 會比較該資料行的值一樣。  
  
> [!NOTE]
> 如果您使用 Visual Studio，可以使用物件關聯式設計工具來建立類別之間的關聯。  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>範例  

 您也可以反轉這種情況。 您可以使用 `Customer` 類別，而不要使用 `Order` 類別來描述客戶和訂單之間的關聯。 `Order` 類別會使用 <xref:System.Data.Linq.EntityRef%601> 型別來描述客戶的反向關聯性，如下列程式碼範例所示。  
  
> [!NOTE]
> <xref:System.Data.Linq.EntityRef%601>類別支援*延後載入*。 如需詳細資訊，*請參閱*[延後和立即載入](deferred-versus-immediate-loading.md)。  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [作法：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
