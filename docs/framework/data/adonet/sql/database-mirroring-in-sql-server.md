---
title: "在 SQL Server 中建立資料庫鏡像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ec0b25976b1b54c91fcdebbc80bc048d2b48823
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="database-mirroring-in-sql-server"></a>在 SQL Server 中建立資料庫鏡像
SQL Server 中的資料庫鏡像可讓您將 SQL Server 資料庫的複本或鏡像保存在待命伺服器上。 鏡像可確保永遠存在兩份分開的資料複本，這會提供高可用性及完整的資料重複性。 .NET Data Provider for SQL Server 提供對資料庫鏡像的隱含支援，這樣將其設定給 SQL Server 資料庫後，開發人員即無需採取任何動作或撰寫任何程式碼。 此外，<xref:System.Data.SqlClient.SqlConnection> 物件支援明確連接模式，可在 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 中提供容錯移轉夥伴伺服器的名稱。  
  
 下列簡化的事件序列會針對目標鎖定設定為鏡像之資料庫的 <xref:System.Data.SqlClient.SqlConnection> 物件發生：  
  
1.  用戶端應用程式成功連接至主體資料庫，伺服器再傳送回夥伴伺服器的名稱，稍後會在用戶端上快取該名稱。  
  
2.  如果包含主體資料庫的伺服器失敗或連接中斷，則會遺失連接及交易狀態。 用戶端應用程式會嘗試重新建立與主體資料庫的連接，但失敗。  
  
3.  然後，用戶端應用程式會透明地嘗試建立與夥伴伺服器上鏡像資料庫的連接。 如果成功，則連接會重新導向至稍後會變成新主體資料庫的鏡像資料庫。  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>在連接字串中指定容錯移轉夥伴  
 如果您在連接字串 (Connection String) 中提供了容錯移轉夥伴伺服器的名稱，只要用戶端應用程式第一次連接時主體資料庫無法使用，用戶端就會透明地嘗試與容錯移轉夥伴連接。  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 如果您省略了容錯移轉夥伴伺服器的名稱，而且用戶端應用程式第一次連接時主體資料庫無法使用，就會引發 <xref:System.Data.SqlClient.SqlException>。  
  
 成功開啟 <xref:System.Data.SqlClient.SqlConnection> 時，伺服器就會傳回容錯移轉夥伴名稱，並且取代連接字串中提供的任何值。  
  
> [!NOTE]
>  在資料庫鏡像案例中，您必須在連接字串中明確指定初始資料庫目錄和資料庫名稱。 如果用戶端在沒有明確指定初始資料庫目錄或資料庫的連接上收到容錯移轉資訊，則不會快取該容錯移轉資訊，而且應用程式在主體伺服器失敗時不會嘗試容錯移轉。 如果連接字串具有容錯移轉夥伴的值，但是沒有初始資料庫目錄或資料庫的值，就會引發 `InvalidArgumentException`。  
  
## <a name="retrieving-the-current-server-name"></a>擷取目前的伺服器名稱  
 在容錯移轉時，您可藉由使用 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性，擷取目前連接實際連接的伺服器名稱。 下列程式碼片段會擷取作用中伺服器的名稱，並假設連接變數參考開啟的 <xref:System.Data.SqlClient.SqlConnection>。  
  
 當發生容錯移轉事件且連接切換至鏡像伺服器， **DataSource**屬性會更新以反映鏡像名稱。  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>SqlClient 鏡像行為  
 用戶端會永遠嘗試連接至目前的主體伺服器。 如果連接失敗，則會嘗試容錯移轉夥伴。 如果鏡像資料庫已切換至夥伴伺服器上的主體角色，則連接成功，並在呼叫 <xref:System.AppDomain> 的存留期內，將新主體鏡像對應傳送至用戶端並快取它。 它不會儲存在永續性儲存體，並不適用於以不同的後續連接**AppDomain**或處理程序。 不過，它是適用於在相同的後續連線**AppDomain**。 請注意，另一個**AppDomain**或一律在相同或不同電腦上執行的處理程序有自己的連接集區，並不會重設那些連接。 在此情況下，如果主要資料庫關閉時，每個處理序或**AppDomain**失敗一次，而且集區會自動清除。  
  
> [!NOTE]
>  會在每個資料庫上設定伺服器上的鏡像支援。 如果藉由使用多個名稱或變更目前的資料庫，針對主體/鏡像組中不包括的其他資料庫執行資料管理作業，則在失敗時，不會傳播對這些資料庫所做的變更。 當在未鏡像的資料庫中修改資料時，不會產生錯誤。 開發人員必須評估此類作業可能會產生的影響。  
  
## <a name="database-mirroring-resources"></a>資料庫鏡像資源  
 如需設定、部署和管理鏡像的概念文件和詳細資訊，請參閱《SQL Server 線上叢書》中的下列資源。  
  
|資源|說明|  
|--------------|-----------------|  
|[資料庫鏡像](http://msdn.microsoft.com/library/bb934127.aspx)SQL Server 線上叢書中|說明如何在 SQL Server 中設定鏡像。|  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
