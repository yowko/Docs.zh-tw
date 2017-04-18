---
title: "SQL Server Compact 和 LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# SQL Server Compact 和 LINQ to SQL
SQL Server Compact 是與 Visual Studio 一起安裝的預設資料庫。如需詳細資訊，請參閱 [PAVE OVER Using SQL Server Compact \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/13320dd1-94e5-4077-bf76-8df253695ccc)。  
  
 本主題簡述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援之使用方式、設定、功能集與範圍的主要差異。  
  
## 有關 LINQ to SQL 的 SQL Server Compact 特性  
 根據預設，所有 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 版本都會安裝 SQL Server Compact，因此可在開發電腦上搭配 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 使用。  但是，部署使用 SQL Server Compact 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的應用程式與部署 [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] 應用程式不同  SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。  
  
 並注意下列特性：  
  
-   SQL Server Compact 會封裝成可直接用於資料庫檔案 \(.sdf 副檔名\) 的 DLL。  
  
-   SQL Server Compact 會在與用戶端應用程式相同的處理序中執行。  因此，與 SQL Server Compact 通訊的效率遠大於與 [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] 通訊的效率。  另一方面，SQL Server Compact 一定需要 Managed 程式碼和 Unmanaged 程式碼與其附帶成本之間的互通性。  
  
-   SQL Server Compact DLL 不大。  這項功能可縮減應用程式整體大小。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]不支援 SQL Server Compact。  
  
## 功能集  
 從下列會影響 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式的層面來說，SQL Server Compact 功能集比 [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] 的功能集簡單許多：  
  
-   SQL Server Compact 不支援預存程序或檢視。  
  
-   SQL Server Compact 僅支援部分的資料類型和 SQL 函式。  
  
-   SQL Server Compact 僅支援部分的 SQL 建構。  
  
-   SQL Server Compact 僅提供最簡單的最佳化工具。  因此有些查詢可能會逾時。  
  
-   SQL Server Compact 不支援部分信任。  
  
## 請參閱  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)