---
title: SQL Server Common Language Runtime 整合
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 12ae15d72644e314aa694f8d169bc8f45fa284a2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452340"
---
# <a name="sql-server-common-language-runtime-integration"></a>SQL Server Common Language Runtime 整合
SQL Server 2005 導入了 .NET Framework for Microsoft Windows 之 Common Language Runtime (CLR) 元件的整合。 這表示您可以使用任何 .NET Framework 語言 (包括 Microsoft Visual Basic .NET 及 Microsoft Visual C#)，撰寫預存程序 (Stored Procedure)、觸發程序 (Trigger)、使用者定義型別、使用者定義函式、使用者定義彙總及資料流資料表值函式。 <xref:Microsoft.SqlServer.Server> 命名空間包含一組新的應用程式開發介面 (API)，以便 Managed 程式碼可與 Microsoft SQL Server 環境互動。  
  
 本節說明 SQL Server Common Language Runtime (CLR) 整合特定的功能及行為，以及 ADO.NET 的 SQL Server 同處理序特定擴充。  
  
 本節的目的是僅提供以 SQL Server CLR 整合進行程式設計快速入門所需的足夠資訊，並未包含廣泛資訊。 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 文件**  
  
1. [Common Language Runtime (CLR) 整合程式設計概念](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a>本節內容  
 [SQL Server CLR 整合簡介](introduction-to-sql-server-clr-integration.md)  
 提供 SQL Server CLR 整合的簡介。 同時提供其他主題的連結。  
  
 [CLR 使用者定義函式](clr-user-defined-functions.md)  
 描述如何實作與使用各種類型的 CLR 函數：資料表值函式、純量函數，以及使用者定義彙總函式。  
  
 [CLR 使用者定義型別](clr-user-defined-types.md)  
 描述如何實作及使用 CLR 使用者定義型別。 同時提供其他主題的連結。  
  
 [CLR 預存程序](clr-stored-procedures.md)  
 描述如何實作及使用 CLR 預存程序。 同時提供其他主題的連結。  
  
 [CLR 觸發程序](clr-triggers.md)  
 描述如何實作及使用 CLR 觸發程序。 同時提供其他主題的連結。  
  
 [內容連線](the-context-connection.md)  
 說明內容連接。  
  
 [ADO.NET 的 SQL Server 同處理序特定行為](sql-server-in-process-specific-behavior-of-adonet.md)  
 說明 ADO.NET 的 SQL Server 同處理序特定擴充及內容連接。 同時提供其他主題的連結。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)
- [ADO.NET 概觀](../ado-net-overview.md)
