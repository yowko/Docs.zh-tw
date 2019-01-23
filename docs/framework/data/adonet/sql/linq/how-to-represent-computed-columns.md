---
title: HOW TO：表示計算資料行
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 97db5d69cd97922acefb0b1f3b10f69cf99e3583
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608328"
---
# <a name="how-to-represent-computed-columns"></a>HOW TO：表示計算資料行
使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性以表示其內容為計算結果的資料行。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援以計算資料行做為主索引鍵。  
  
### <a name="to-represent-a-computed-column"></a>若要表示計算資料行  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2.  將公式的字串表示指派至 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property)。  
  
## <a name="see-also"></a>另請參閱
- [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [如何：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
