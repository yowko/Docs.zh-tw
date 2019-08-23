---
title: 作法：表示主索引鍵
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 28c62798f965edfcffe1a156213c2481a8193b49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943534"
---
# <a name="how-to-represent-primary-keys"></a>HOW TO：表示主索引鍵
使用屬性[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ( <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute) 上的<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>屬性 (property) 來指定屬性或欄位, 以代表資料庫資料行的主要索引鍵。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>。  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援以計算資料行做為主索引鍵。  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>若要指定屬性或欄位做為主索引鍵  
  
1. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2. 將值指定為 `true`。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [如何：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
