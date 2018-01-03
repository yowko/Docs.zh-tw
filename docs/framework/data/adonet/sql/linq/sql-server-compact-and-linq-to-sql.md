---
title: "SQL Server Compact 和 LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2717a94228dc1be8da0d84179201747d60c896a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact 和 LINQ to SQL
SQL Server Compact 是與 Visual Studio 一起安裝的預設資料庫。 如需詳細資訊，請參閱[PAVE 透過使用 SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc)。  
  
 本主題概述使用方式、 設定、 功能集和範圍的主要差異[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>有關 LINQ to SQL 的 SQL Server Compact 特性  
 根據預設，SQL Server Compact 為所有安裝[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]版本中，因此會用於在開發電腦上[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。 但使用 SQL Server Compact 的應用程式的部署和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]不同[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]應用程式。 SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。  
  
 並注意下列特性：  
  
-   SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。  
  
-   SQL Server Compact 在用戶端應用程式相同的程序中執行。 與 SQL Server Compact 通訊的效率因此可能遠大於與通訊[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]。 相反地，SQL Server Compact 一定需要 managed 和 unmanaged 程式碼與其附帶成本之間的互通性。  
  
-   SQL Server Compact DLL 的大小很小。 這項功能可縮減應用程式整體大小。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]不支援 SQL Server Compact。  
  
## <a name="feature-set"></a>功能集  
 SQL Server Compact 功能集會更簡單的功能集比[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]以下列方式可能會影響[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]應用程式：  
  
-   SQL Server Compact 不支援預存程序或檢視。  
  
-   SQL Server Compact 僅支援部分的資料類型和 SQL 函式。  
  
-   SQL Server Compact 僅支援部分的 SQL 建構。  
  
-   SQL Server Compact 僅提供最簡單的最佳化工具。 有可能，有些查詢可能會逾時。  
  
-   SQL Server Compact 不支援部分信任。  
  
## <a name="see-also"></a>請參閱  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
