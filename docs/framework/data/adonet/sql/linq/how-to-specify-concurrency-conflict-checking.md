---
title: HOW TO：指定並行衝突檢查
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 53d3ba6969705940c403795d3764c021f0829c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033679"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>HOW TO：指定並行衝突檢查
您可以指定在呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時要檢查並行存取衝突的資料庫資料行。 如需詳細資訊，請參閱[如何：指定的成員會用於測試並行衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)。  
  
## <a name="example"></a>範例  
 下列程式碼指定 `HomePage` 成員永遠不應該在更新檢查期間進行測試。 如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [如何：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
