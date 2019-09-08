---
title: SQL Server Compact 和 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792543"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact 和 LINQ to SQL
SQL Server Compact 是隨 Visual Studio 一起安裝的預設資料庫。 如需詳細資訊，請參閱[使用 SQL Server Compact （Visual Studio）](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))。  
  
 本主題概述使用方式、設定、功能集和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援範圍中的主要差異。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>有關 LINQ to SQL 的 SQL Server Compact 特性  
 根據預設，SQL Server Compact 會針對所有 Visual Studio 版本進行安裝，因此可在開發電腦上使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，以用於。 但是，部署使用 SQL Server Compact 且[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]與 SQL Server 應用程式不同的應用程式。 SQL Server Compact 不屬於 .NET Framework，因此必須封裝在應用程式中或從 Microsoft 網站個別下載。  
  
 並注意下列特性：  
  
- SQL Server Compact 會封裝成可直接用於資料庫檔案 (.sdf 副檔名) 的 DLL。  
  
- SQL Server Compact 在與用戶端應用程式相同的進程中執行。 因此，與 SQL Server Compact 通訊的效率會明顯高於與 SQL Server 通訊。 另一方面，SQL Server Compact 需要受控和非受控碼之間的互通性，以及其附隨的費用。  
  
- SQL Server Compact DLL 的大小很小。 這項功能可縮減應用程式整體大小。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行階段和 SQLMetal 命令列工具都支援 SQL Server Compact。  
  
- 物件關聯式設計工具不支援 SQL Server Compact。  
  
## <a name="feature-set"></a>功能集  
 SQL Server Compact 功能集比 SQL Server 的功能集簡單許多，可能會影響[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]應用程式：  
  
- SQL Server Compact 不支援預存程序或檢視。  
  
- SQL Server Compact 僅支援部分的資料類型和 SQL 函式。  
  
- SQL Server Compact 僅支援部分的 SQL 建構。  
  
- SQL Server Compact 僅提供最簡單的最佳化工具。 有些查詢可能會超時。  
  
- SQL Server Compact 不支援部分信任。  
  
## <a name="see-also"></a>另請參閱

- [參考資料](reference.md)
