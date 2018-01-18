---
title: "LINQ to SQL 中的安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0ee361c27bd14f0266b2b86f315f9c091e049c12
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="security-in-linq-to-sql"></a>LINQ to SQL 中的安全性
當您連接至資料庫時，永遠都會存在安全性風險。 雖然 LINQ to SQL 可能會包含一些使用 SQL Server 資料的新方式，但是並不會提供任何額外的安全性機制。  
  
## <a name="access-control-and-authentication"></a>存取控制和驗證  
 LINQ to SQL 本身並沒有使用者模型或驗證機制。 您可以使用 SQL Server 安全性來控制對應至物件模型 (Object Model) 之資料庫、資料庫資料表、檢視表和預存程序 (Stored Procedure) 的存取權。 請將最低必要存取權授與使用者，並且要求增強式密碼來進行使用者驗證。  
  
## <a name="mapping-and-schema-information"></a>對應和結構描述資訊  
 物件模型或外部對應檔案中的 SQL-CLR 型別對應和資料庫結構描述資訊可供所有在檔案系統中擁有這些檔案之存取權的使用者使用。 假設結構描述資訊可供所有可存取物件模型或外部對應檔案的使用者使用。若要防止其他人對結構描述資訊進行更普遍的存取，請使用檔案安全性機制來保護原始程式檔 (Source File) 和對應檔案的安全。  
  
## <a name="connection-strings"></a>連接字串  
 請盡可能避免在連接字串中使用密碼。 不但連接字串本身會產生安全性風險，而且使用物件關聯式設計工具或 SQLMetal 命令列工具時，連接字串可能也會以純文字的方式加入至物件模型或外部對應檔案。 可經由檔案系統存取物件模型或外部對應檔案的任何人都可能會看見連接密碼 (如果包含在連接字串中的話)。  
  
 若要將這類風險降到最低，請使用整合式安全性，與 [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] 進行信任連接。 使用這種方法，就不需要將密碼儲存在連接字串中。 如需詳細資訊，請參閱[SQL Server 安全性](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md)。  
  
 如果沒有整合式安全性，連接字串將會需要純文字密碼。 協助保護連接字串安全的最佳方法如下所示 (按照風險的遞增順序列出)：  
  
-   使用整合式安全性。  
  
-   使用密碼來保護連接字串的安全，並且盡可能減少在連接字串前後傳遞密碼。  
  
-   使用 <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> 類別 (Class) 來取代連接字串，因為它會限制公開的持續期間。 您可以使用 <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> 來具現化 LINQ to SQL <xref:System.Data.SqlClient.SqlConnection> 類別。  
  
-   盡可能減少所有連接字串的存留期 (Lifetime) 和接觸點。  
  
## <a name="see-also"></a>請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [常見問題集](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
