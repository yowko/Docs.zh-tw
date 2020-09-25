---
title: 作法：指定私用儲存欄位
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 7b47504e7dbad8a2d8414304ec19f2e9e2c06ef5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197166"
---
# <a name="how-to-specify-private-storage-fields"></a>作法：指定私用儲存欄位

您 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 可以使用屬性（attribute）上的屬性（property） <xref:System.Data.Linq.Mapping.DataAttribute> 來指定基礎儲存欄位的名稱。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a>若要指定基礎儲存欄位的名稱  
  
1. 將 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2. 指定欄位名稱做為 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 的值。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)
- [作法：使用程式碼編輯器自訂實體類別](how-to-customize-entity-classes-by-using-the-code-editor.md)
