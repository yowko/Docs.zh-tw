---
title: "LINQ to SQL 多層式架構與 ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# LINQ to SQL 多層式架構與 ASP.NET
在使用 [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] 的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中，您可以使用 <xref:System.Web.UI.WebControls.LinqDataSource> Web 伺服器控制項。 這個控制項負責大多數的必要邏輯，以查詢 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、將資料傳遞至瀏覽器、擷取資料以及提交到 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>，後者接著會更新資料庫。 您只要在標記中設定控制項，該控制項就會負責 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 與瀏覽器之間的所有資料傳輸作業。 由於有這個控制項負責與展示層的互動，又有 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 負責與資料層溝通，您就能專注在 [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] 多層應用程式中撰寫自訂商務邏輯。  
  
 如需 `LINQDataSource` 的詳細資訊，請參閱 [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/zh-tw/104cfc3f-7385-47d3-8a51-830dfa791136)。  
  
## 請參閱  
 [使用 LINQ to SQL 的 N\-Tier 和遠端應用程式](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)