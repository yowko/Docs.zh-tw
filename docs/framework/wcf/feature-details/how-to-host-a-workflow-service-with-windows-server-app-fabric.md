---
title: HOW TO：使用 Windows Server App Fabric 裝載工作流程服務
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: ecc7a954b2d88cdbcf934cc836e9ad6e3ef7ed52
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964756"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>HOW TO：使用 Windows Server App Fabric 裝載工作流程服務

在 AppFabric 中裝載工作流程服務與在 IIS/WAS 底下裝載很相似。 唯一的差異在於 AppFabric 針對部署、監視和管理工作流程服務所提供的工具。 本主題使用建立[長期執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)中所建立的工作流程服務。 該主題將逐步引導您建立工作流程服務。 本主題會說明如何使用 AppFabric 來裝載工作流程服務。 如需 Windows Server App Fabric 的詳細資訊，請參閱[Windows Server App Fabric 檔](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))。 完成下列步驟之前，請先確定您已安裝 Windows Server AppFabric。  若要這麼做，請開啟 Internet Information Services （inetmgr），**在 [連線**] 視圖中按一下您的伺服器名稱，按一下 [網站]，然後按一下 [**預設的網站**]。 在畫面右手邊，您應該會看到一個稱為「**應用程式網狀架構**」的區段。 如果您沒有看見此區段 (位於右側窗格的頂端)，表示您沒有安裝 App Fabric。 如需安裝 Windows Server App Fabric 的詳細資訊，請參閱[安裝 Windows Server App fabric](https://docs.microsoft.com/previous-versions/appfabric/ee790960(v=azure.10))。  
  
### <a name="creating-a-simple-workflow-service"></a>建立簡單的工作流程服務  
  
1. 開啟 Visual Studio 2012，並載入您在[建立長時間執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)主題中建立的 OrderProcessing 解決方案。  
  
2. 以滑鼠右鍵按一下**OrderService**專案，並選取 [**屬性**]，然後選取 [ **Web** ] 索引標籤。  
  
3. 在屬性頁的 [**起始動作**] 區段中，選取 [**特定頁面**]，然後在編輯方塊中輸入 Service1. service1.xamlx。  
  
4. 在屬性頁的 [**伺服器**] 區段中，選取 [**使用本機 IIS Web 服務器**]，然後輸入下列 URL： `http://localhost/OrderService`。  
  
5. 按一下 [**建立虛擬目錄**] 按鈕。 這樣就會建立新的虛擬目錄並設定專案，以便在建置專案時，將所需的檔案複製到虛擬目錄。  或者，您也可以將 .xamlx、web.config 和任何所需的 DLL 手動複製到虛擬目錄。  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>設定在 Windows Server AppFabric 中裝載的工作流程服務  
  
1. 開啟 Internet Information Services 管理員 (inetmgr.exe)。  
  
2. 在 [**連線] 窗格中，流覽**至 OrderService 虛擬目錄。  
  
3. 以滑鼠右鍵按一下 OrderService，並選取 [**管理 WCF 和 WF 服務**]、[**設定 ...** ]。 [**設定應用程式的 WCF 和 WF** ] 對話方塊隨即顯示。  
  
4. 選取 [**一般**] 索引標籤，以顯示應用程式的一般資訊，如下列螢幕擷取畫面所示。  
  
     ![[App Fabric 設定] 對話方塊的 [一般] 索引標籤](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration-一般")  
  
5. 選取 [**監視**] 索引標籤。這會顯示各種監視設定，如下列螢幕擷取畫面所示。  
  
     ![[App Fabric 設定監視] 索引標籤](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-監視")  
  
     如需有關在應用程式網狀架構中設定工作流程服務監視的詳細資訊，請參閱[使用 App fabric 設定監視](https://docs.microsoft.com/previous-versions/appfabric/ee677384(v=azure.10))。  
  
6. 選取 [**工作流程持續**性] 索引標籤。這可讓您將應用程式設定為使用 App Fabric 的預設持續性提供者，如下列螢幕擷取畫面所示。  
  
     ![App Fabric 設定&#45;持續性](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-持續性")  
  
     如需在 Windows Server App Fabric 中設定工作流程持續性的詳細資訊，請參閱[在 App fabric 中設定工作流程持續](https://docs.microsoft.com/previous-versions/appfabric/ee677353(v=azure.10))性。  
  
7. 選取 [**工作流程主機管理**] 索引標籤。這可讓您指定何時應卸載並保存閒置的工作流程服務實例，如下列螢幕擷取畫面所示。  
  
     ![App Fabric 設定工作流程主機管理](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration-管理")  
  
     如需工作流程主機管理設定的詳細資訊，請參閱[在 App Fabric 中設定工作流程主機管理](https://docs.microsoft.com/previous-versions/appfabric/ff383424(v=azure.10))。  
  
8. 選取 [**自動啟動**] 索引標籤。這可讓您為應用程式中的工作流程服務指定自動啟動設定，如下列螢幕擷取畫面所示。  
  
     ![顯示 App Fabric 自動&#45;啟動設定的螢幕擷取畫面。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     如需設定自動啟動的詳細資訊，請參閱[使用 App Fabric 設定自動啟動](https://docs.microsoft.com/previous-versions/appfabric/ee677261(v=azure.10))。  
  
9. 選取 [**節流**] 索引標籤。這可讓您設定工作流程服務的節流設定，如下列螢幕擷取畫面所示。  
  
     ![顯示 App Fabric 節流設定的螢幕擷取畫面。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     如需設定節流的詳細資訊，請參閱[使用 App Fabric 設定節流](https://docs.microsoft.com/previous-versions/appfabric/ee677261(v=azure.10))。  
  
10. 選取 [**安全性**] 索引標籤。這可讓您設定應用程式的安全性設定，如下列螢幕擷取畫面所示。  
  
     ![App Fabric 安全性設定](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration-安全性")  
  
     如需使用 Windows Server App Fabric 設定安全性的詳細資訊，請參閱[使用 App fabric 設定安全性](https://docs.microsoft.com/previous-versions/appfabric/ee677278(v=azure.10))。  
  
### <a name="using-windows-server-app-fabric"></a>使用 Windows Server AppFabric  
  
1. 建置方案，以便將必要的檔案複製到虛擬目錄。  
  
2. 以滑鼠右鍵按一下 Orderclient 專案，然後選取  **Debug**，**啟動新的實例** 來啟動用戶端應用程式。  
  
3. 用戶端將會執行，Visual Studio 將會顯示 [**附加安全性警告**] 對話方塊中，按一下 [**不要附加**] 按鈕。 這樣會告知 Visual Studio 不要附加至 IIS 處理序進行偵錯。  
  
4. 用戶端應用程式會立即呼叫工作流程服務，然後等候。 工作流程服務將處於閒置狀態並保存。 您可以啟動 Internet Information Services (inetmgr.exe)、在 [連線] 窗格中巡覽至 OrderService，然後選取它，藉以確認這點。 接著，在右側窗格中，按一下 [AppFabric 儀表板] 圖示。 在持續性的 WF 實例底下，您會看到有一個持續性的工作流程服務實例，如下列螢幕擷取畫面所示。  
  
     ![顯示 App Fabric 儀表板的螢幕擷取畫面。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     **WF 實例歷程記錄**會列出工作流程服務的相關資訊，例如工作流程服務啟動的數目、工作流程服務實例完成的數目，以及失敗的工作流程實例數目。 在 [作用中] 或 [閒置實例] 底下，會顯示連結，按一下此連結將會顯示有關閒置工作流程實例的詳細資訊，如下列螢幕擷取畫面所示。  
  
     ![顯示持續性工作流程實例詳細資料的螢幕擷取畫面。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     如需 Windows Server App Fabric 功能及其使用方式的詳細資訊，請參閱[Windows Server App Fabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))  
  
## <a name="see-also"></a>請參閱

- [建立長期執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
- [安裝 Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee790960(v=azure.10))
- [Windows Server App Fabric 檔](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))
