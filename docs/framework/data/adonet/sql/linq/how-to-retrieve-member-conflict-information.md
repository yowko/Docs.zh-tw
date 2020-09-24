---
title: 作法：擷取成員衝突資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 4848ef69914f0520d2365538faea7fa064c1a15c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155805"
---
# <a name="how-to-retrieve-member-conflict-information"></a>作法：擷取成員衝突資訊

您可以使用 <xref:System.Data.Linq.MemberChangeConflict> 類別來擷取衝突中各個成員的相關資訊。 在此相同狀況下，您可以替任何成員做好自訂處理衝突的準備。 如需詳細資訊，請參閱 [開放式平行存取：總覽](optimistic-concurrency-overview.md)。  
  
## <a name="example"></a>範例  

 下列程式碼會逐一查看 <xref:System.Data.Linq.ObjectChangeConflict> 物件。 對於每個物件，它會接著逐一查看 <xref:System.Data.Linq.MemberChangeConflict> 物件。  
  
> [!NOTE]
> 納入 <xref:System.Reflection>，以便提供 <xref:System.Data.Linq.MemberChangeConflict.Member%2A> 資訊。  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [作法：管理變更衝突](how-to-manage-change-conflicts.md)
