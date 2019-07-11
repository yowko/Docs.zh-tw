---
title: SQL Server Compact 和 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 5fa8f8ba2b0c5bdb92ad507bd48839a26837ba41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742860"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact 和 LINQ to SQL
SQL Server Compact 是與 Visual Studio 一起安裝的預設資料庫。 如需詳細資訊，請參閱 <<c0> [ 使用 SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))。  
  
 本主題概述使用狀況、 組態、 功能集，以及範圍的主要不同處[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>有關 LINQ to SQL 的 SQL Server Compact 特性  
 根據預設，SQL Server Compact 安裝適用於所有的 Visual Studio 版本，因此可用於開發電腦上[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。 但使用 SQL Server Compact 的應用程式的部署和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]不同於 SQL Server 應用程式。 SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。  
  
 並注意下列特性：  
  
- SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。  
  
- SQL Server Compact 會在執行用戶端應用程式相同的程序。 與 SQL Server Compact 通訊的效率，因此可能遠大於與 SQL Server 通訊。 相反地，SQL Server Compact 一定需要 managed 和 unmanaged 程式碼與其附帶成本之間的互通性。  
  
- SQL Server Compact DLL 的大小很小。 這項功能可縮減應用程式整體大小。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。  
  
- 物件關聯式設計工具不支援 SQL Server Compact。  
  
## <a name="feature-set"></a>功能集  
 SQL Server Compact 功能集是 SQL Server 的功能集比簡單多了下列方式，可能會影響[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]應用程式：  
  
- SQL Server Compact 不支援預存程序或檢視。  
  
- SQL Server Compact 僅支援部分的資料類型和 SQL 函式。  
  
- SQL Server Compact 僅支援部分的 SQL 建構。  
  
- SQL Server Compact 僅提供最簡單的最佳化工具。 可以，有些查詢可能會逾時。  
  
- SQL Server Compact 不支援部分信任。  
  
## <a name="see-also"></a>另請參閱

- [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
