---
title: "如何：表示主索引鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c832b7c54ecbd1f4c4a3bebcbf7f293b9a45e46c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-primary-keys"></a>如何：表示主索引鍵
使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定屬性或欄位來表示資料庫資料行的主索引鍵。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援以計算資料行做為主索引鍵。  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>若要指定屬性或欄位做為主索引鍵  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2.  將值指定為 `true`。  
  
## <a name="see-also"></a>請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [如何：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
