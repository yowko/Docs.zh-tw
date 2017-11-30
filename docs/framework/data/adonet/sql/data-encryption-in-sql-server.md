---
title: "在 SQL Server 中加密資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4428cf8fbfcaa853ca2c877a8cc4902f585b6754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="data-encryption-in-sql-server"></a>在 SQL Server 中加密資料
SQL Server 提供使用憑證、非對稱金鑰或對稱金鑰來加密及解密資料的功能， 而且可在內部的憑證存放區內管理上述所有項目。 此存放區會使用加密階層，藉由階層中的上層層級來確保下層層級的憑證及金鑰。 SQL Server 的此功能區也稱為「秘密儲存區」(Secret Storage)。  
  
 由加密功能所支援的最快加密模式是對稱金鑰加密。 此模式適合用來處理大量的資料。 對稱金鑰可以藉由憑證、密碼或其他對稱金鑰進行加密。  
  
## <a name="keys-and-algorithms"></a>金鑰和演算法  
 SQL Server 支援數種對稱金鑰加密演算法，包括 DES、Triple DES、RC2、RC4、128 位元 RC4、DESX、128 位元 AES、192 位元 AES 和 256 位元 AES 等， 這些演算法是使用 Windows Crypto API 來實作。  
  
 SQL Server 可在資料庫連接的範圍內維護多個開放式的對稱金鑰。 您可從存放區擷取開放式金鑰，並將其用於解密資料。 在資料解密後，就不需指定要使用的對稱金鑰。 每個加密的值都包含加密時所使用金鑰的識別碼 (金鑰 GUID)。 如果已解密並開啟了正確的金鑰，則引擎會比對加密的位元組資料流與開放式對稱金鑰， 然後再使用此金鑰來執行解密作業並傳回資料。 如果沒有開啟正確的金鑰，則會傳回 NULL。  
  
 如需示範如何使用資料庫中的加密資料的範例，請參閱[如何： 加密資料行的資料](http://go.microsoft.com/fwlink/?LinkID=128559)SQL Server 線上叢書 》 中。  
  
## <a name="external-resources"></a>外部資源  
 如需有關資料加密的詳細資訊，請參閱下列資源。  
  
|||  
|-|-|  
|[SQL Server 加密](http://msdn.microsoft.com/library/bb510663.aspx)SQL Server 線上叢書中|提供 SQL Server 中的加密概觀。 此主題包含其他主題和「如何」文件的連結。|  
|[加密階層](http://msdn.microsoft.com/library/ms189586.aspx)和[加密的如何主題](http://msdn.microsoft.com/library/aa337557.aspx)SQL Server 線上叢書中|提供 SQL Server 中的加密概觀。 此主題包含其他主題和「如何」文件的連結。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [在 SQL Server 驗證](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [伺服器和 SQL Server 中的資料庫角色](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [擁有權和 SQL Server 中的使用者結構描述分隔](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [授權和 SQL Server 中的權限](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
