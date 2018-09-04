---
title: HOW TO：在 WAS 中裝載 WCF 服務
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: fd48957f7f8410b4b0df39fe125c35e4fc98cb8e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560291"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>HOW TO：在 WAS 中裝載 WCF 服務
本主題概述建立 Windows Process Activation Services (亦稱為 WAS) 所需的基本步驟裝載 Windows Communication Foundation (WCF) 服務。 WAS 是新的處理序啟用服務，其為一般化的 Internet Information Services (IIS) 功能，與非 HTTP 傳輸通訊協定搭配使用。 WCF 會使用 WCF，例如 TCP、 具名管道，與訊息佇列所支援的非 HTTP 通訊協定接收啟用要求通訊接聽程式配接器介面。  
  
 這個裝載選項要求 WAS 啟用元件必須正確安裝與設定，但不要求將任何裝載程式碼撰寫為應用程式的一部分。 如需有關安裝與設定 WAS 的詳細資訊，請參閱 <<c0> [ 如何： 安裝和設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)。  
  
> [!WARNING]
>  如果 Web 伺服器的要求處理管線設定為「傳統」模式，就不支援 WAS 啟動。 若要使用 WAS 啟動，Web 伺服器的要求處理管線就必須設定為「整合」模式。  
  
 時在 WAS 中裝載 WCF 服務，標準繫結會使用以一般方式。 但是，當透過 <xref:System.ServiceModel.NetTcpBinding> 和 <xref:System.ServiceModel.NetNamedPipeBinding> 來設定 WAS 裝載的服務時，就必須滿足下列限制。 當不同的端點使用同一個傳輸，繫結設定必須符合下列七項屬性：  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   MaxPendingConnections  
  
-   MaxOutputDelay  
  
-   MaxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 否則，先初始化的端點一律直接決定這些屬性的值，而稍後新增的端點則會在這些屬性值未符合上述設定值時擲回 <xref:System.ServiceModel.ServiceActivationException>。  
  
 如需此範例中的來源複本，請參閱[TCP 啟動](../../../../docs/framework/wcf/samples/tcp-activation.md)。  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>若要建立 WAS 裝載的基本服務  
  
1.  定義服務類型的服務合約。  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  在服務類別中實作服務合約。 請注意，服務的實作內並未指定位址或繫結資訊。 同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  建立 Web.config 檔案，定義 <xref:System.ServiceModel.NetTcpBinding> 端點要使用的 `CalculatorService` 繫結。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  建立包含下列程式碼的 Service.svc 檔案。  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  將 Service.svc 檔放入您的 IIS 虛擬目錄中。  
  
### <a name="to-create-a-client-to-use-the-service"></a>若要建立用戶端來使用服務  
  
1.  使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從命令列，從服務中繼資料產生程式碼。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  產生的用戶端應用程式也包含 `ClientCalculator` 的實作。 請注意，服務的實作內部並未指定位址和繫結資訊。 同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  使用 <xref:System.ServiceModel.NetTcpBinding> 的用戶端組態也是由 Svcutil.exe 所產生的。 使用 Visual Studio 時，此檔案應該命名為 App.config。  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  請編譯並執行用戶端。  
  
## <a name="see-also"></a>另請參閱  
 [TCP 啟用](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Windows Server App Fabric 主控功能](https://go.microsoft.com/fwlink/?LinkId=201276)
