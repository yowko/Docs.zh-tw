---
title: SQL Server Compact 和 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 7963db9e05eca7a7a148228c6d2fbca0221ca870
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155675"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact 和 LINQ to SQL

SQL Server Compact 是隨 Visual Studio 安裝的預設資料庫。 如需詳細資訊，請參閱 [使用 SQL Server Compact (Visual Studio) ](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))。  
  
 本主題將概述使用方式、設定、功能集和支援範圍的主要差異 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>有關 LINQ to SQL 的 SQL Server Compact 特性  

 根據預設，會針對所有 Visual Studio 版本安裝 SQL Server Compact，因此可在開發電腦上使用，以搭配使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。 但是，部署使用 SQL Server Compact 的應用程式，以及與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server 應用程式不同的應用程式。 SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。  
  
 並注意下列特性：  
  
- SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。  
  
- SQL Server Compact 會在與用戶端應用程式相同的處理序中執行。 因此，與 SQL Server Compact 的通訊效率可能會比使用 SQL Server 更高。 另一方面，SQL Server Compact 一定需要 Managed 程式碼和 Unmanaged 程式碼與其附帶成本之間的互通性。  
  
- SQL Server Compact DLL 不大。 這項功能可縮減應用程式整體大小。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。  
  
- 物件關聯式設計工具不支援 SQL Server Compact。  
  
## <a name="feature-set"></a>功能集  

 SQL Server Compact 功能集比 SQL Server 的功能集簡單許多，可能會影響 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式：  
  
- SQL Server Compact 不支援預存程序或檢視。  
  
- SQL Server Compact 僅支援部分的資料類型和 SQL 函式。  
  
- SQL Server Compact 僅支援部分的 SQL 建構。  
  
- SQL Server Compact 僅提供最簡單的最佳化工具。 因此有些查詢可能會逾時。  
  
- SQL Server Compact 不支援部分信任。  
  
## <a name="see-also"></a>另請參閱

- [參考](reference.md)
