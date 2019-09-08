---
title: 高可用性、嚴重損壞修復的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: b51c3cb1eb3c8726b7de007a1c1519eae0733392
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791608"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>高可用性、嚴重損壞修復的 SqlClient 支援
本主題討論適用于高可用性、嚴重損壞修復的 SqlClient 支援（新增于 .NET Framework 4.5）--AlwaysOn 可用性群組。  AlwaysOn 可用性群組功能已新增至 SQL Server 2012。 如需 AlwaysOn 可用性群組的詳細資訊，請參閱 SQL Server 線上叢書。  
  
 您現在可以在連接屬性中指定（高可用性、嚴重損壞修復）可用性群組（AG）或 SQL Server 2012 容錯移轉叢集實例的可用性群組接聽程式。 如果 SqlClient 應用程式連接到容錯移轉的 AlwaysOn 資料庫，原始連接會中斷。容錯移轉之後，應用程式必須開啟新的連接才能繼續工作。  
  
 如果您不是連接到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集實例，而且如果有多個 IP 位址與主機名稱相關聯，SqlClient 會依序逐一查看所有與 DNS 專案相關聯的 IP 位址。 如果 DNS 傳回的第一個 IP 位址未繫結至任何網路介面卡 (NIC)，可能會很耗時。 當連接到可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集實例時，SqlClient 會嘗試平行建立與所有 IP 位址的連線，如果連線嘗試成功，驅動程式就會捨棄任何暫止的連接機會.  
  
> [!NOTE]
> 增加連接逾時和實作連接重試邏輯，可提高應用程式連接到可用性群組的可能性。 此外，由於連接可能因為容錯移轉而失敗，因此您應實作連接重試邏輯，重試失敗的連接直到重新連接為止。  
  
 下列連接屬性已新增至 .NET Framework 4.5 中的 SqlClient：  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 您可以利用程式設計方式修改這些連接字串關鍵字：  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
> .NET Framework `MultiSubnetFailover` 4.6.1 `true`或更新版本不需要將設定為。
  
## <a name="connecting-with-multisubnetfailover"></a>連接 MultiSubnetFailover  
 當連接`MultiSubnetFailover=True`到 SQL Server 2012 可用性群組接聽程式或 SQL Server 2012 容錯移轉叢集實例時，一律指定。 `MultiSubnetFailover`針對 SQL Server 2012 中的所有可用性群組和或容錯移轉叢集實例啟用更快速的容錯移轉，並大幅縮短單一和多重子網 AlwaysOn 拓撲的容錯移轉時間。 在多重子網路容錯移轉時，用戶端將嘗試並行連接。 子網路容錯移轉期間，將積極重試 TCP 連接。  
  
 `MultiSubnetFailover`連接屬性工作表示應用程式正在可用性群組或 SQL Server 2012 容錯移轉叢集實例中部署，而且 SqlClient 會嘗試連接到主要 SQL Server 實例上的資料庫，方法是嘗試連接到所有 IP 位址。 指定連接的 `MultiSubnetFailover=True` 時，用戶端重試 TCP 連接嘗試的速度會比作業系統預設的 TCP 重新傳送間隔更快。 這樣可以在 AlwaysOn 可用性群組或 AlwaysOn 容錯移轉叢集執行個體容錯移轉後更快重新連接，而且適用於單一子網路和多重子網路可用性群組與容錯移轉叢集執行個體。  
  
 如需 SqlClient 中有關連接字串關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。  
  
 指定`MultiSubnetFailover=True`連接到可用性群組接聽程式以外的專案或 SQL Server 2012 容錯移轉叢集實例時，可能會造成負面的效能影響，而且不受支援。  
  
 使用下列指導方針，連接到可用性群組中的伺服器或 SQL Server 2012 容錯移轉叢集實例：  
  
- 連接至單一子網路或多重子網路時，使用 `MultiSubnetFailover` 連接屬性可以提高兩者的效能。  
  
- 若要連接到可用性群組，請在連接字串中將該可用性群組的可用性群組接聽程式指定為伺服器。  
  
- 連接到設定了超過64個 IP 位址的 SQL Server 實例，將會導致連線失敗。  
  
- 根據驗證類型，使用`MultiSubnetFailover`連接屬性之應用程式的行為不會受到影響：SQL Server 驗證、Kerberos 驗證或 Windows 驗證。  
  
- 提高 `Connect Timeout` 的值可延長容錯移轉時間並減少應用程式重試連接的次數。  
  
- 不支援分散式異動。  
  
 如果唯讀路由沒有作用，在下列情況下連接到次要複本位置會失敗：  
  
1. 如果未將次要複本位置設定為接受連接。  
  
2. 如果應用程式使用 `ApplicationIntent=ReadWrite` (討論如下)，且次要複本位置設定為唯讀存取。  
  
 唯讀次要複本不支援 <xref:System.Data.SqlClient.SqlDependency>。  
  
 如果主要複本設定為拒絕唯讀工作負載，且連接字串包含 `ApplicationIntent=ReadOnly`，連接將會失敗。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>從資料庫鏡像升級以使用多重子網路叢集  
 如果連接字串中出現 <xref:System.ArgumentException> 和 `MultiSubnetFailover` 連接關鍵字，或者使用了 `Failover Partner` 和 TCP 以外的通訊協定，就會發生連接錯誤 (`MultiSubnetFailover=True`)。 <xref:System.Data.SqlClient.SqlException>如果`MultiSubnetFailover`使用，而且 SQL Server 傳回容錯移轉夥伴回應，指出它是資料庫鏡像配對的一部分，也會發生錯誤（）。  
  
 如果將目前使用資料庫鏡像的 SqlClient 應用程式升級至多重子網路案例，您應該移除 `Failover Partner` 連接屬性，並將 `MultiSubnetFailover` 集合設為 `True` 以取代該連接屬性，然後將連接字串中的伺服器名稱取代為可用性群組接聽程式。 如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=True`，驅動程式將產生錯誤。 但是，如果連接字串使用 `Failover Partner` 和 `MultiSubnetFailover=False` (或 `ApplicationIntent=ReadWrite`)，應用程式將使用資料庫鏡像。  
  
 如果在 AG 的主要資料庫中使用資料庫鏡像，且若在連接至主要資料庫而非可用性群組接聽程式的連接字串中使用 `MultiSubnetFailover=True`，驅動程式會傳回錯誤。  
  
## <a name="specifying-application-intent"></a>指定應用程式用途  
 當 `ApplicationIntent=ReadOnly` 時，用戶端會在連接至啟用 AlwaysOn 的資料庫時要求讀取工作負載。 伺服器將在連接及 USE 資料庫陳述式時強制該用途，但僅限於啟用 Always On 的資料庫。  
  
 `ApplicationIntent` 關鍵字不適用於舊式的唯讀資料庫。  
  
 資料庫可以允許或不允許目標 AlwaysOn 資料庫上的讀取工作負載。 （這是透過`ALLOW_CONNECTIONS` `PRIMARY_ROLE`和`SECONDARY_ROLE`transact-sql 語句的子句來完成）。  
  
 `ApplicationIntent` 關鍵字可用於啟用唯讀路由。  
  
## <a name="read-only-routing"></a>唯讀路由  
 唯讀路由功能可確保唯讀資料庫複本的可用性。 若要啟用唯讀路由：  
  
1. 您必須連接到 AlwaysOn 可用性群組的可用性群組接聽程式。  
  
2. `ApplicationIntent` 連接字串關鍵字必須設為 `ReadOnly`。  
  
3. 資料庫管理員必須設定可用性群組以啟用唯讀路由。  
  
 使用唯讀路由的多個連接可能不會全數連接至同一個唯讀複本。 資料庫同步作業或伺服器路由組態中的變更可能會導致用戶端連接至不同的唯讀複本。 為確保所有唯讀要求能連接到同一個唯讀複本，請勿將可用性群組接聽程式傳送到 `Data Source` 連接字串關鍵字。 相反地，請指定唯讀執行個體的名稱。  
  
 唯讀路由連接到主要複本的時間較長，因為唯讀路由會先連接到主要複本，再尋找最適合的可讀次要複本。 因此，您應延長登入逾時。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 功能和 ADO.NET](sql-server-features-and-adonet.md)
- [ADO.NET 概觀](../ado-net-overview.md)
