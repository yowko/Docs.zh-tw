---
title: HOW TO：指定資料庫名稱
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781572"
---
# <a name="how-to-specify-database-names"></a>HOW TO：指定資料庫名稱
在 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Attribute) 上使用 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 屬性 (Property)，可在連接未提供名稱時指定資料庫名稱。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>。  
  
### <a name="to-specify-the-name-of-the-database"></a>若要指定資料庫的名稱  
  
1. 將 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 屬性 (Attribute) 加入至資料庫的類別宣告。  
  
2. 將 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 屬性 (Attribute)。  
  
3. 將 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Property) 值設定為想要指定的名稱。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
- [如何：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
