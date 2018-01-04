---
title: "HOW TO：指定組態中的服務繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea54b2f84c9de233ff2560795dc97f79c15aa0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="6ddee-102">HOW TO：指定組態中的服務繫結</span><span class="sxs-lookup"><span data-stu-id="6ddee-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="6ddee-103">在此範例中會定義基本計算機服務的 `ICalculator` 合約，該服務會在 `CalculatorService` 類別中實作，然後會在 Web.config 檔案中設定其端點，其中會指定服務使用 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="6ddee-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="6ddee-104">如需如何設定此服務，使用程式碼，而不組態的說明，請參閱[How to： 指定程式碼中的服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="6ddee-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="6ddee-105">通常最佳作法是在組態中以宣告方式指定繫結和位址資訊，而不是在程式碼中強制指定。</span><span class="sxs-lookup"><span data-stu-id="6ddee-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="6ddee-106">在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。</span><span class="sxs-lookup"><span data-stu-id="6ddee-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="6ddee-107">比較一般性的作法是將繫結和位址資訊留在程式碼外面，如此一來，不需要重新編譯或重新部署應用程式，就可以變更繫結和位址資訊。</span><span class="sxs-lookup"><span data-stu-id="6ddee-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="6ddee-108">所有的下列設定步驟可以進行使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="6ddee-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="6ddee-109">此範例的來源副本，請參閱[BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="6ddee-109">For the source copy of this example, see [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span></span>  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="6ddee-110">指定用來設定服務的 BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6ddee-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1.  <span data-ttu-id="6ddee-111">定義服務類型的服務合約。</span><span class="sxs-lookup"><span data-stu-id="6ddee-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="6ddee-112">在服務類別中實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="6ddee-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6ddee-113">此服務的實作中不會指定位址或繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="6ddee-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="6ddee-114">同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ddee-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3.  <span data-ttu-id="6ddee-115">請建立 Web.config 檔，為使用 `CalculatorService` 的 <xref:System.ServiceModel.WSHttpBinding> 設定端點。</span><span class="sxs-lookup"><span data-stu-id="6ddee-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  <span data-ttu-id="6ddee-116">請建立 Service.svc 檔，其中包含下列這行文字，並且將它放入 Internet Information Services (IIS) 虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="6ddee-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="6ddee-117">若要修改繫結屬性的預設值</span><span class="sxs-lookup"><span data-stu-id="6ddee-117">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="6ddee-118">若要修改預設屬性值的其中一項<xref:System.ServiceModel.WSHttpBinding>，建立新的繫結組態名稱- `<binding name="Binding1">` -內[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目和設定的屬性的新值此繫結項目中的繫結。</span><span class="sxs-lookup"><span data-stu-id="6ddee-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="6ddee-119">例如，若要將預設的開啟和關閉逾時值從 1 分鐘變更為 2 分鐘，請將下列文字加入至組態檔。</span><span class="sxs-lookup"><span data-stu-id="6ddee-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6ddee-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ddee-120">See Also</span></span>  
 [<span data-ttu-id="6ddee-121">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6ddee-121">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="6ddee-122">指定端點位址</span><span class="sxs-lookup"><span data-stu-id="6ddee-122">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
