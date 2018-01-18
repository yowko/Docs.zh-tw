---
title: "如何：指定用於測試並行衝突的成員"
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
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0c65299f48db3ba727cece673e6a7df2d9cd8872
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>如何：指定用於測試並行衝突的成員
套用至三個列舉的其中一個[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>開放式並行存取衝突的偵測會檢查屬性來指定要包含在更新中的哪些成員。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (在設計階段對應) 是與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的執行階段並行存取功能搭配使用。 如需詳細資訊，請參閱[開放式並行存取： 概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
> [!NOTE]
>  只要未將成員指定為 `IsVersion=true`，原始成員值就會與目前資料庫狀態進行比較。 如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>若一律要使用這個成員來偵測衝突  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `Always`。  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>若永不使用這個成員來偵測衝突  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `Never`。  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>若只有在應用程式已變更成員的值時，才使用這個成員來偵測衝突  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `WhenChanged`。  
  
## <a name="example"></a>範例  
 下列範例指定 `HomePage` 物件永遠不應該在更新檢查期間進行測試。 如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [變更和提交資料](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
