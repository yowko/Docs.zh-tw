---
title: HOW TO：設定 Windows Communication Foundation 服務，以使用連接埠共用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 942dea9b745d3dd7cda366ad3e855ddaed0473db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582548"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="5ec3a-102">HOW TO：設定 Windows Communication Foundation 服務，以使用連接埠共用</span><span class="sxs-lookup"><span data-stu-id="5ec3a-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="5ec3a-103">使用 net.tcp:// 的連接埠共用您的 Windows Communication Foundation (WCF) 應用程式的最簡單方式是公開服務，使用<xref:System.ServiceModel.NetTcpBinding>。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="5ec3a-104">這項繫結會提供 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 屬性，以控制是否針對使用此繫結進行設定的服務啟用 net.tcp:// 連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="5ec3a-105">下列程序將說明如何使用 <xref:System.ServiceModel.NetTcpBinding> 類別來開啟統一資源識別元 (URI) net.tcp://localhost/MyService 中的端點 (先使用程式碼，然後再使用組態項目)。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="5ec3a-106">若要使用程式碼啟用 NetTcpBinding 上的 net.tcp:// 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="5ec3a-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="5ec3a-107">建立服務，以實作合約，稱為`IMyService`，並為它`MyService`。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="5ec3a-108">建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="5ec3a-109">建立 <xref:System.ServiceModel.ServiceHost>，並在其上為 `MyService` 新增服務端點，該服務會使用連接埠共用啟用之 <xref:System.ServiceModel.NetTcpBinding>，並在端點位址 URI "net.tcp://localhost/MyService" 上進行接聽。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5ec3a-110">此範例使用預設 TCP 連接埠號碼 808，因為端點位址 URI 並未指定不同的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="5ec3a-111">由於已在傳輸繫結程序上明確啟用連接埠共用，此服務可與其他處理序中的其他服務共用連接埠 808。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="5ec3a-112">如果不允許使用連接埠共用，而另一個應用程式已在使用連接埠 808，則此服務將在開啟時擲回 <xref:System.ServiceModel.AddressAlreadyInUseException>。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="5ec3a-113">若要使用組態啟用 NetTcpBinding 上的 net.tcp:// 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="5ec3a-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="5ec3a-114">下列範例將說明如何使用組態項目來啟用連接埠共用並新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="5ec3a-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ec3a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ec3a-115">See also</span></span>
- [<span data-ttu-id="5ec3a-116">Net.TCP 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="5ec3a-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="5ec3a-117">如何：啟用 Net.TCP Port Sharing Service</span><span class="sxs-lookup"><span data-stu-id="5ec3a-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
