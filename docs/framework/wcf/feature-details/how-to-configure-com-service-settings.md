---
title: "HOW TO：設定 COM+ 服務設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa497567c5cf380d7764499991ad9e7e95a5cbe0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="d69fa-102">HOW TO：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="d69fa-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="d69fa-103">使用 COM+ 服務組態工具加入或移除應用程式介面時，Web 服務組態會在應用程式的組態檔中更新。</span><span class="sxs-lookup"><span data-stu-id="d69fa-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="d69fa-104">在 COM + 裝載模式中，Application.config 檔案放在應用程式的根目錄中 (%PROGRAMFILES%\ComPlus 應用程式\\{appid} 是預設值)。</span><span class="sxs-lookup"><span data-stu-id="d69fa-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="d69fa-105">在兩個 Web 裝載模式中，Web.config 檔案都會放在指定的 vroot 目錄中。</span><span class="sxs-lookup"><span data-stu-id="d69fa-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d69fa-106">訊息簽章應用來保護用戶端和伺服器之間的訊息不受竄改。</span><span class="sxs-lookup"><span data-stu-id="d69fa-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="d69fa-107">此外，訊息或傳輸層加密也應該用來保護用戶端和伺服器之間的訊息，以免資訊洩漏。</span><span class="sxs-lookup"><span data-stu-id="d69fa-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="d69fa-108">如同 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務，您應使用節流來限制同時呼叫、連線、執行個體和暫止作業的數目。</span><span class="sxs-lookup"><span data-stu-id="d69fa-108">As with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="d69fa-109">這有助防止資源過度消耗。</span><span class="sxs-lookup"><span data-stu-id="d69fa-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="d69fa-110">節流行為是透過服務組態檔設定所指定的。</span><span class="sxs-lookup"><span data-stu-id="d69fa-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d69fa-111">範例</span><span class="sxs-lookup"><span data-stu-id="d69fa-111">Example</span></span>  
 <span data-ttu-id="d69fa-112">試想實作下列介面的元件：</span><span class="sxs-lookup"><span data-stu-id="d69fa-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="d69fa-113">如果元件公開為 Web 服務，則公開 (且用戶端必須符合) 的對應服務合約如下：</span><span class="sxs-lookup"><span data-stu-id="d69fa-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="d69fa-114">IID 是做為合約的初始命名空間一部分。</span><span class="sxs-lookup"><span data-stu-id="d69fa-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="d69fa-115">使用這個服務的用戶端應用程式必須符合這個合約，並且使用與應用程式組態中所指定的繫結相容的繫結。</span><span class="sxs-lookup"><span data-stu-id="d69fa-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="d69fa-116">下列程式碼範例中會示範預設組態檔。</span><span class="sxs-lookup"><span data-stu-id="d69fa-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="d69fa-117">它是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web 服務，符合標準的服務模型組態結構描述，而且可用其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務組態檔相同的方式加以編輯。</span><span class="sxs-lookup"><span data-stu-id="d69fa-117">Being a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services configuration files.</span></span>  
  
 <span data-ttu-id="d69fa-118">一般修改包含：</span><span class="sxs-lookup"><span data-stu-id="d69fa-118">Typical modifications would include:</span></span>  
  
-   <span data-ttu-id="d69fa-119">將端點位址從預設形式 ApplicationName/ComponentName/InterfaceName 變更為更容易使用的形式。</span><span class="sxs-lookup"><span data-stu-id="d69fa-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
-   <span data-ttu-id="d69fa-120">將服務的命名空間從預設形式 "http://tempuri.org/InterfaceID" 修改為更有意義的形式。</span><span class="sxs-lookup"><span data-stu-id="d69fa-120">Modifying the namespace of the service from the default "http://tempuri.org/InterfaceID" form to a more relevant form.</span></span>  
  
-   <span data-ttu-id="d69fa-121">變更端點以使用不同的傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="d69fa-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="d69fa-122">在 COM+ 裝載案例中，預設會使用具名管道，但也可以使用像 TCP 的電腦外傳輸。</span><span class="sxs-lookup"><span data-stu-id="d69fa-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d69fa-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d69fa-123">See Also</span></span>  
 [<span data-ttu-id="d69fa-124">整合 COM + 應用程式</span><span class="sxs-lookup"><span data-stu-id="d69fa-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
