---
title: Oracle 分散式異動
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a3b8a50b42b945a0cdc1cbfbc4cc9eab835e90e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505395"
---
# <a name="oracle-distributed-transactions"></a>Oracle 分散式異動
如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定交易處於作用中，便會自動登記在現有的分散式交易中。 當從連接共用開啟或擷取連接時，會發生自動交易登記。 您可以停用現有交易的自動登記功能，方法是指定   
  
```  
Enlist=false  
```  
  
 做為 <xref:System.Data.OracleClient.OracleConnection> 的連接字串參數。  
  
## <a name="see-also"></a>另請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
