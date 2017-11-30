---
title: "如何：指定私用儲存欄位"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1095189eaefa8fe34dd554a982110754bb3bd135
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-private-storage-fields"></a>如何：指定私用儲存欄位
使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>屬性<xref:System.Data.Linq.Mapping.DataAttribute>屬性來指定基礎儲存欄位的名稱。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a>若要指定基礎儲存欄位的名稱  
  
1.  將 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。  
  
2.  指定欄位名稱做為 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 的值。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [如何： 使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
