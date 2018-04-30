---
title: HOW TO：使用組態檔發行服務的中繼資料
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d30031db590b424688cc0af6a573c1042099e64e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="cad60-102">HOW TO：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="cad60-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="cad60-103">在兩個示範如何發行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務中繼資料的 HOW TO 主題中，這是其中一個。</span><span class="sxs-lookup"><span data-stu-id="cad60-103">This is one of two how-to topics that demonstrate publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="cad60-104">有兩種方法可以指定服務發行中繼資料的方式，分別是使用組態檔和使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="cad60-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="cad60-105">本主題說明如何使用組態檔發行服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cad60-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cad60-106">本主題將示範以不安全的方法發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cad60-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="cad60-107">任何用戶端都能從服務擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cad60-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="cad60-108">如果您需要您的服務發行中繼資料以安全的方式，請參閱[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="cad60-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="cad60-109">如需程式碼中發行中繼資料的詳細資訊，請參閱[How to： 服務使用程式碼發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)。</span><span class="sxs-lookup"><span data-stu-id="cad60-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="cad60-110">發行中繼資料可讓用戶端透過 WS-Transfer GET 要求，或是透過使用 `?wsdl` 查詢字串的 HTTP/GET 要求來擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cad60-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="cad60-111">若要確定程式碼可以正常運作，請建立基本的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="cad60-111">To be sure that the code is working, create a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="cad60-112">為了方便使用，下列程式碼提供基本的自我裝載服務。</span><span class="sxs-lookup"><span data-stu-id="cad60-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cad60-113">此服務是透過組態檔設定的自我裝載服務。</span><span class="sxs-lookup"><span data-stu-id="cad60-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="cad60-114">下列組態檔將做為起點。</span><span class="sxs-lookup"><span data-stu-id="cad60-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="cad60-115">若要使用應用程式組態檔來發行 WCF 服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="cad60-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="cad60-116">在 App.config 檔案中，於結尾的 `</services>` 項目之後，建立 `<behaviors>` 項目。</span><span class="sxs-lookup"><span data-stu-id="cad60-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="cad60-117">在 `<behaviors>` 項目中，新增 `<serviceBehaviors>` 項目。</span><span class="sxs-lookup"><span data-stu-id="cad60-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="cad60-118">將 `<behavior>` 項目新增至 `<serviceBehaviors>` 項目，並指定 `name` 項目的  `<behavior>` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="cad60-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="cad60-119">將 `<serviceMetadata>` 項目加入至 `<behavior>` 項目。</span><span class="sxs-lookup"><span data-stu-id="cad60-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="cad60-120">將 `httpGetEnabled` 屬性設為 `true` 並將 `policyVersion` 屬性設為 Policy15。</span><span class="sxs-lookup"><span data-stu-id="cad60-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="cad60-121">`httpGetEnabled` 允許服務回應由 HTTP GET 要求所提出的中繼資料要求。</span><span class="sxs-lookup"><span data-stu-id="cad60-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="cad60-122">`policyVersion` 會在產生中繼資料時，要求服務符合 WS-Policy 1.5 規定。</span><span class="sxs-lookup"><span data-stu-id="cad60-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="cad60-123">將 `behaviorConfiguration` 屬性加入至 `<service>` 項目，並指定 `name` 項目的 `<behavior>` 屬性 (於步驟 1 中加入)，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="cad60-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6.  <span data-ttu-id="cad60-124">加入一個或多個 `<endpoint>` 項目，並將合約設為 `IMetadataExchange`，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="cad60-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7.  <span data-ttu-id="cad60-125">針對上一個步驟中加入的中繼資料端點，將 `binding` 屬性設為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cad60-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="cad60-126">`mexHttpBinding` (適用 HTTP 發行)。</span><span class="sxs-lookup"><span data-stu-id="cad60-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="cad60-127">`mexHttpsBinding` (適用 HTTPS 發行)。</span><span class="sxs-lookup"><span data-stu-id="cad60-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="cad60-128">`mexNamedPipeBinding` (適用具名管道發行)。</span><span class="sxs-lookup"><span data-stu-id="cad60-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="cad60-129">`mexTcpBinding` (適用 TCP 發行)。</span><span class="sxs-lookup"><span data-stu-id="cad60-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="cad60-130">針對上一個步驟中加入的中繼資料端點，將位址設為與下列項目相等：</span><span class="sxs-lookup"><span data-stu-id="cad60-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="cad60-131">如果基底位址與中繼資料繫結相同，則設定空字串以使用主應用程式的基底位址做為發行點。</span><span class="sxs-lookup"><span data-stu-id="cad60-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="cad60-132">如果主應用程式具有基底位址，則設為相對位址。</span><span class="sxs-lookup"><span data-stu-id="cad60-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="cad60-133">絕對位址。</span><span class="sxs-lookup"><span data-stu-id="cad60-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="cad60-134">建置並執行主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cad60-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="cad60-135">使用 Internet Explorer 瀏覽至服務的基底位址 (http://localhost:8001/MetadataSample在此範例中)，並確認已開啟中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="cad60-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="cad60-136">如果沒有的話，結果頁面上方應該會顯示：「為此服務發行的中繼資料目前停用」。</span><span class="sxs-lookup"><span data-stu-id="cad60-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="cad60-137">若要使用預設端點</span><span class="sxs-lookup"><span data-stu-id="cad60-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="cad60-138">若要對使用預設端點的服務設定中繼資料，請在組態檔中指定 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> (如上一個範例所示)，但不要指定任何端點。</span><span class="sxs-lookup"><span data-stu-id="cad60-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="cad60-139">組態檔如下所示。</span><span class="sxs-lookup"><span data-stu-id="cad60-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="cad60-140">因為服務有 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 且 `httpGetEnabled` 設為 `true`，服務已經啟用發行中繼資料，但是因為沒有明確加入端點，所以執行階段加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="cad60-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="cad60-141">如需有關預設端點、 繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cad60-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cad60-142">範例</span><span class="sxs-lookup"><span data-stu-id="cad60-142">Example</span></span>  
 <span data-ttu-id="cad60-143">下列程式碼範例顯示基本 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的實作，以及發行服務中繼資料的組態檔。</span><span class="sxs-lookup"><span data-stu-id="cad60-143">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cad60-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cad60-144">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="cad60-145">如何：於受管理的應用程式中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="cad60-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="cad60-146">自我裝載</span><span class="sxs-lookup"><span data-stu-id="cad60-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="cad60-147">中繼資料架構概觀</span><span class="sxs-lookup"><span data-stu-id="cad60-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="cad60-148">使用中繼資料</span><span class="sxs-lookup"><span data-stu-id="cad60-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="cad60-149">如何：使用程式碼發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="cad60-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
