---
title: SQL Server Compact 和 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355782"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact 和 LINQ to SQL
SQL Server Compact 是與 Visual Studio 一起安裝的預設資料庫。 如需詳細資訊，請參閱[PAVE 透過使用 SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc)。  
  
 本主題概述使用方式、 設定、 功能集和範圍的主要差異[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>有關 LINQ to SQL 的 SQL Server Compact 特性  
 根據預設，SQL Server Compact 安裝適用於所有的 Visual Studio 版本，因此搭配使用的開發電腦上可用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。 但使用 SQL Server Compact 的應用程式的部署和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]不同於 SQL Server 應用程式。 SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。  
  
 並注意下列特性：  
  
-   SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。  
  
-   SQL Server Compact 在用戶端應用程式相同的程序中執行。 與 SQL Server Compact 通訊的效率，因此可以遠大於與 SQL Server 通訊。 相反地，SQL Server Compact 一定需要 managed 和 unmanaged 程式碼與其附帶成本之間的互通性。  
  
-   SQL Server Compact DLL 的大小很小。 這項功能可縮減應用程式整體大小。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]不支援 SQL Server Compact。  
  
## <a name="feature-set"></a>功能集  
 SQL Server Compact 功能集是以下列方式可能會影響 SQL Server 的功能集比更簡單[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]應用程式：  
  
-   SQL Server Compact 不支援預存程序或檢視。  
  
-   SQL Server Compact 僅支援部分的資料類型和 SQL 函式。  
  
-   SQL Server Compact 僅支援部分的 SQL 建構。  
  
-   SQL Server Compact 僅提供最簡單的最佳化工具。 有可能，有些查詢可能會逾時。  
  
-   SQL Server Compact 不支援部分信任。  
  
## <a name="see-also"></a>另請參閱  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
