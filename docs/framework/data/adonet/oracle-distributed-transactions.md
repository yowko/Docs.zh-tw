---
title: "Oracle 分散式異動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c48232bb204b71c662a99bf210ad54fc3ee9eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-distributed-transactions"></a>Oracle 分散式異動
如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定交易處於作用中，便會自動登記在現有的分散式交易中。 當從連接共用開啟或擷取連接時，會發生自動交易登記。 您可以停用現有交易的自動登記功能，方法是指定   
  
```  
Enlist=false  
```  
  
 做為 <xref:System.Data.OracleClient.OracleConnection> 的連接字串參數。  
  
## <a name="see-also"></a>另請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
