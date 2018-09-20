---
title: LocalDB 的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 1ef75def3f3de44b5e23cb1197a4410dcf6b547f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492635"
---
# <a name="sqlclient-support-for-localdb"></a>LocalDB 的 SqlClient 支援
從 SQL Server 代號 Denali，輕量版的 SQL Server，名為 LocalDB，將可。 本主題討論如何連接到 LocalDB 資料庫。  
  
## <a name="remarks"></a>備註  
 如需有關 LocalDB 的詳細資訊，包括如何安裝 LocalDB 和設定您的 LocalDB 執行個體，請參閱 SQL Server 線上叢書 》。  
  
 LocalDB 功能摘要：  
  
-   以 sqllocaldb.exe 或您的 app.config 檔建立及啟動 LocalDB 執行個體。  
  
-   使用 sqlcmd.exe 新增及修改 LocalDB 執行個體中的資料庫。 例如， `sqlcmd -S (localdb)\myinst`。  
  
-   使用 `AttachDBFilename` 連接字串關鍵字將資料庫新增到 LocalDB 執行個體。 使用 `AttachDBFilename`時，如果您不以 `Database` 連接字串關鍵字指定資料庫名稱，當應用程式關閉時，會將資料庫從 LocalDB 執行個體中移除。  
  
-   在連接字串中指定 LocalDB 執行個體。 例如，您的執行個體名稱是 `myInstance`，連接字串將包括：  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 連接至 LocalDB 資料庫時不允許`User Instance=True` 。  
  
 您可以下載從 LocalDB [Microsoft SQL Server 2012 功能套件](https://www.microsoft.com/download/en/details.aspx?id=29065)。 如果您將使用 sqlcmd.exe 來修改 LocalDB 執行個體中的資料，您必須從 SQL Server 2012，您也可以從 SQL Server 2012 功能套件取得 sqlcmd。  
  
## <a name="programmatically-create-a-named-instance"></a>以程式設計方式建立具名執行個體  
 應用程式可以建立具名執行個體並指定資料庫，如下所示：  
  
-   在 app.config 檔中指定要建立的 LocalDB 執行個體，如下所示。  執行個體的版本號碼應與 LocalDB 安裝的版本號碼相同。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   使用 `server` 連接字串關鍵字指定執行個體的名稱。  在 `server` 連接字串關鍵字中指定的執行個體名稱，必須與 app.config 檔中指定的名稱相符。  
  
-   使用 `AttachDBFilename` 連接字串關鍵字來指定 .MDF 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 功能和 ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
