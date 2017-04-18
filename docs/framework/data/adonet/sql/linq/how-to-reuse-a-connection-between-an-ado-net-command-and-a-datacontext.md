---
title: "HOW TO：重複使用 ADO.NET 命令和 DataContext 之間的連接 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：重複使用 ADO.NET 命令和 DataContext 之間的連接
因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 為 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 技術家族的一部分，而且是以 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 所提供的服務為基礎，所以您可重複使用介於 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 命令和 <xref:System.Data.Linq.DataContext> 之間的連接。  
  
## 範例  
 下列範例會顯示如何重複使用介於 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 命令和 <xref:System.Data.Linq.DataContext> 之間的相同連接。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## 請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [ADO.NET 和 LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)   
 [與資料庫通訊](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)