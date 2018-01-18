---
title: "如何：擷取成員衝突資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fab9111bb14b41244fab3bcd9c2ea0b0f91d72ce
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-retrieve-member-conflict-information"></a>如何：擷取成員衝突資訊
您可以使用 <xref:System.Data.Linq.MemberChangeConflict> 類別來擷取衝突中各個成員的相關資訊。 在此相同狀況下，您可以替任何成員做好自訂處理衝突的準備。 如需詳細資訊，請參閱[開放式並行存取： 概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會逐一查看 <xref:System.Data.Linq.ObjectChangeConflict> 物件。 對於每個物件，它會接著逐一查看 <xref:System.Data.Linq.MemberChangeConflict> 物件。  
  
> [!NOTE]
>  納入 <xref:System.Reflection>，以便提供 <xref:System.Data.Linq.MemberChangeConflict.Member%2A> 資訊。  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
