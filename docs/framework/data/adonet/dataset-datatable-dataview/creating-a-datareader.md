---
title: "建立 DataReader"
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
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05b3943613a6ab03e77dee7fb8262029618b5c7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-datareader"></a>建立 DataReader
<xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別 (Class) 具有 <xref:System.Data.DataTable.CreateDataReader%2A> 方法，可以用一或多個唯讀的順向結果集來傳回 <xref:System.Data.DataTable> 的內容或 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataSet.Tables%2A> 集合內容。  
  
## <a name="example"></a>範例  
 下列的主控台應用程式會建立 <xref:System.Data.DataTable> 執行個體 (Instance)。 此範例接著會將傳遞填<xref:System.Data.DataTable>要呼叫的程序<xref:System.Data.DataTable.CreateDataReader%2A>方法，這個方法會逐一查看包含在結果<xref:System.Data.DataTableReader>。  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 此範例會在主控台視窗中顯示以下輸出：  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
