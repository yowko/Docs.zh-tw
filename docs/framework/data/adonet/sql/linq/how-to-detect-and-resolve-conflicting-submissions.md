---
title: 作法：偵測和解決發生衝突的提交內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 96e96208d9bb28092701164e6cd5943ef81515a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147719"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>作法：偵測和解決發生衝突的提交內容

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了許多資源，以便偵測和解決多位使用者變更資料庫所造成的衝突。 如需詳細資訊，請參閱 [如何：管理變更衝突](how-to-manage-change-conflicts.md)。  
  
## <a name="example"></a>範例  

 下列範例顯示 `try` / `catch` 攔截例外狀況的區塊 <xref:System.Data.Linq.ChangeConflictException> 。 主控台視窗中會顯示每個衝突的實體和成員資訊。  
  
> [!NOTE]
> 您必須納入 `using System.Reflection` 指示詞 (在 Visual Basic 中為 `Imports System.Reflection`)，才能支援資訊擷取。 如需詳細資訊，請參閱<xref:System.Reflection>。  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [變更資料和提交](making-and-submitting-data-changes.md)
- [作法：管理變更衝突](how-to-manage-change-conflicts.md)
