---
title: "SQL Server 中的 CLR 整合安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37437d827fc0ff6583178f33f4cceaa86f5175dd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server 中的 CLR 整合安全性
Microsoft SQL Server 提供 .NET Framework 之 Common Language Runtime (CLR) 元件的整合。 CLR 整合可讓您使用任意 .NET Framework 語言 (包括 Microsoft Visual Basic .NET 或 Microsoft Visual C#)，撰寫預存程序 (Stored Procedure)、觸發程序 (Trigger)、使用者定義型別、使用者定義函式、使用者定義彙總及資料流資料表值函式等。  
  
 CLR 支援稱為 Managed 程式碼之程式碼存取安全性 (CAS) 的安全性模型。 此模型會根據中繼資料中的程式碼所提供的辨識項，為組件授與權限。 SQL Server 將 SQL Server 的使用者架構安全性模型與 CLR 的程式碼存取架構安全性模型相整合。  
  
## <a name="external-resources"></a>外部資源  
 如需有關 SQL Server 的 CLR 整合的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[程式碼存取安全性](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|包含說明 .NET Framework 中的 CAS 的主題。|  
|[CLR 整合安全性](http://go.microsoft.com/fwlink/?LinkId=59998)|討論在 SQL Server 內部執行之 Managed 程式碼的安全性模型。|  
  
## <a name="see-also"></a>請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server Common Language Runtime 整合](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
