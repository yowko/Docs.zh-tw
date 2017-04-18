---
title: "Entity Framework 函式的 SqlClient | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Framework 函式的 SqlClient
本節將描述可讓 Entity Framework 透過 Microsoft SQL Server 運作的 .NET Framework Data Provider for SQL Server \(SqlClient\)。  
  
## Provider 結構描述屬性  
 在存放結構定義語言 \(SSDL\) 中，`Provider` 是 `Schema` 項目的屬性。  
  
 若要使用 SqlClient，請將字串 "System.Data.SqlClient" 指派給 `Schema` 項目的 `Provider` 屬性。  
  
## ProviderManifestToken 結構描述屬性  
 在 SSDL 中，`ProviderManifestToken` 是 `Schema` 項目的必要屬性。  這個語彙基元 \(Token\) 是用來載入提供者資訊清單以供離線案例使用。  如需 `ProviderManifestToken` 屬性的詳細資訊，請參閱 [Schema Element \(SSDL\)](http://msdn.microsoft.com/zh-tw/fec75ae4-7f16-4421-9265-9dac61509222)。  
  
 SqlClient 可當做不同 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 版本的資料提供者 \(Data Provider\) 使用。  這些版本具有不同的功能。  例如，[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] 不支援 [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] 所導入的 `varchar(max)` 和 `nvarchar(max)` 型別。  
  
 SqlClient 會針對不同的 SQL Server 版本，產生並接受下列提供者資訊清單語彙基元。  
  
||||  
|-|-|-|  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|2000|2005|2008|  
  
> [!NOTE]
>  自 [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010 開始，[ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/zh-tw/91076853-0881-421b-837a-f582f36be527) 不支援 SQL Server 2000。  
  
## 提供者命名空間名稱  
 所有提供者都必須指定命名空間。  這個屬性會告知 Entity Framework 此提供者對特定建構 \(例如型別和函式\) 所使用的前置詞。  SqlClient 提供者資訊清單的命名空間是 `SqlServer`。  如需命名空間的詳細資訊，請參閱[命名空間](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)。  
  
## 型別  
 適用於 Entity Framework 的 SqlClient 提供者會提供概念模型類型和 SQL Server 型別之間的對應資訊。  如需詳細資訊，請參閱[Entity FrameworkTypes 的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)。  
  
## 函式  
 Entity Framework 的 SqlClient 提供者會定義提供者所支援的函式清單。  如需支援之函式的清單，請參閱 [Entity Framework 函式的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。  
  
## 本章節內容  
 [Entity Framework 函式的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity FrameworkTypes 的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework SqlClient 中的已知問題](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## 請參閱  
 [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)   
 [語言參考](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)   
 [Known Issues in SqlClient Provider for Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)