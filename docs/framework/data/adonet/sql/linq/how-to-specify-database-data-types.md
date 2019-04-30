---
title: HOW TO：指定資料庫的資料類型
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 67f23ff06aefbcff4ba7e2eaab63d9b8493b9717
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033666"
---
# <a name="how-to-specify-database-data-types"></a>HOW TO：指定資料庫的資料類型
使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定 T-SQL 資料表宣告中定義的資料行的確切文字。  
  
 只有在計劃使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 建立資料庫執行個體時，才必須指定 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 屬性 (Property)。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>。  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>若要指定文字以定義 T-SQL 資料表中的資料型別  
  
1. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性的值設定為 T-SQL 使用的確切文字。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [如何：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
