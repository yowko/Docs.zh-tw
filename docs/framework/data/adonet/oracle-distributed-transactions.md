---
title: Oracle 分散式異動
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 4af1c98818f1929850c5ae78892c64993a93d4d2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116213"
---
# <a name="oracle-distributed-transactions"></a>Oracle 分散式異動
如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定異動處於作用中，便會自動登記在現有的分散式異動中。 當從連接共用開啟或擷取連接時，會發生自動異動登記。 您可以停用現有交易的自動登記功能，方法是指定   
  
```  
Enlist=false  
```  
  
 做為 <xref:System.Data.OracleClient.OracleConnection> 的連接字串參數。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
