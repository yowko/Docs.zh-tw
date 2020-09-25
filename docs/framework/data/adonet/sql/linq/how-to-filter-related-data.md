---
title: 作法：篩選相關資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e12bab55b03fac3383b98b8ee1c56ab1954ff978
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173454"
---
# <a name="how-to-filter-related-data"></a>作法：篩選相關資料

使用 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法，可指定子查詢限制所擷取的資料量。  
  
## <a name="example"></a>範例  

 在下列範例中，<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 方法會將所擷取的 `Orders` 限制為今天尚未運送的訂單。 若不使用這種方法，則即使只需要某個子集，仍然會擷取所有 `Orders`。  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [查詢資料庫](querying-the-database.md)
