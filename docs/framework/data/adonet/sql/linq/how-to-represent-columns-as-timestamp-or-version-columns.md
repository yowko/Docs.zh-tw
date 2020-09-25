---
title: 作法：將資料行表示為時間戳記或版本資料行
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: cc8538ab7b2ecf5183cfb97995c04648493a369f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191745"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>作法：將資料行表示為時間戳記或版本資料行

您 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 可以使用屬性（ <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute）屬性（attribute）來指定欄位或屬性（property），以代表保存資料庫時間戳記或版本號碼的資料庫資料行。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>若要指定欄位或屬性以表示時間戳記或版本資料行  
  
1. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 值設定為 `true`。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
- [作法：指定用於測試並行衝突的成員](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [作法：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
