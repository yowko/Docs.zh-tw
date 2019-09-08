---
title: 作法：將資料行表示為時間戳記或版本資料行
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793495"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>作法：將資料行表示為時間戳記或版本資料行
使用屬性（<xref:System.Data.Linq.Mapping.ColumnAttribute> attribute）的屬性（property）來指定欄位或屬性（property），以表示保存資料庫時間戳記或版本號碼的資料庫資料行。<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>若要指定欄位或屬性以表示時間戳記或版本資料行  
  
1. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2. 將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 值設定為 `true`。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
- [如何：指定測試並行衝突的成員](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [如何：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
