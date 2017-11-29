---
title: "SQL Server Common Language Runtime 整合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3705db8b9d359ce83c6c47bef58de327745bed44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-common-language-runtime-integration"></a>SQL Server Common Language Runtime 整合
SQL Server 2005 導入了 .NET Framework for Microsoft Windows 之 Common Language Runtime (CLR) 元件的整合。 這表示您可以使用任何 .NET Framework 語言 (包括 Microsoft Visual Basic .NET 及 Microsoft Visual C#)，撰寫預存程序 (Stored Procedure)、觸發程序 (Trigger)、使用者定義型別、使用者定義函式、使用者定義彙總及資料流資料表值函式。 <xref:Microsoft.SqlServer.Server> 命名空間包含一組新的應用程式開發介面 (API)，以便 Managed 程式碼可與 Microsoft SQL Server 環境互動。  
  
 本節說明 SQL Server Common Language Runtime (CLR) 整合特定的功能及行為，以及 ADO.NET 的 SQL Server 同處理序特定擴充。  
  
 本節的目的是僅提供以 SQL Server CLR 整合進行程式設計快速入門所需的足夠資訊，並未包含廣泛資訊。 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
1.  [Common Language Runtime (CLR) 整合程式設計概念](http://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>本章節內容  
 [SQL Server CLR 整合簡介](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 提供 SQL Server CLR 整合的簡介。 同時提供其他主題的連結。  
  
 [CLR 使用者定義函式](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 描述如何實作與使用各種類型的 CLR 函數：資料表值函式、純量函式，以及使用者定義彙總函式。  
  
 [CLR 使用者定義型別](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 說明如何實作及使用 CLR 使用者定義型別。 同時提供其他主題的連結。  
  
 [CLR 預存程序](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 說明如何實作及使用 CLR 預存程序。 同時提供其他主題的連結。  
  
 [CLR 觸發程序](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 說明如何實作及使用 CLR 觸發程序。 同時提供其他主題的連結。  
  
 [內容連接](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 說明內容連接。  
  
 [ADO.NET 的 SQL Server 中處理序特定行為](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 說明 ADO.NET 的 SQL Server 同處理序特定擴充及內容連接。 同時提供其他主題的連結。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [在 Managed 程式碼中建立 SQL Server 2005 物件](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
