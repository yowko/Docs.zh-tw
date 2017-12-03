---
title: "從 WCF 服務呼叫 REST 樣式服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: efb04f36ad83755edd2e7d49c7cdec3cce77273b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="50adf-102">從 WCF 服務呼叫 REST 樣式服務</span><span class="sxs-lookup"><span data-stu-id="50adf-102">Calling a REST-style service from a WCF service</span></span>
<span data-ttu-id="50adf-103">由規則 (以 SOAP 為基礎) WCF 服務呼叫 REST 樣式服務時，服務方法的作業內容 (包含傳入要求的相關資訊) 會覆寫應該由輸出要求使用的內容。</span><span class="sxs-lookup"><span data-stu-id="50adf-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="50adf-104">這會導致 HTTP GET 要求變更為 HTTP POST 要求。</span><span class="sxs-lookup"><span data-stu-id="50adf-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="50adf-105">若要強制 WCF 服務使用正確的內容來呼叫 REST 樣式服務，請建立新的 <xref:System.ServiceModel.OperationContextScope>，並從作業內容範圍內呼叫 REST 樣式服務。</span><span class="sxs-lookup"><span data-stu-id="50adf-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="50adf-106">本主題將說明如何建立簡單的範例來示範這個技巧。</span><span class="sxs-lookup"><span data-stu-id="50adf-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>  
  
## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="50adf-107">定義 REST 樣式服務合約</span><span class="sxs-lookup"><span data-stu-id="50adf-107">Define the REST-style service contract</span></span>  
 <span data-ttu-id="50adf-108">定義簡單的 REST 樣式服務合約：</span><span class="sxs-lookup"><span data-stu-id="50adf-108">Define a simple  REST-style service contract:</span></span>  
  
```csharp
[ServiceContract]
public interface IRestInterface  
{  
    [OperationContract, WebGet]
    int Add(int x, int y);
    
    [OperationContract, WebGet]
    string Echo(string input);
}
```
  
## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="50adf-109">實作 REST 樣式服務合約</span><span class="sxs-lookup"><span data-stu-id="50adf-109">Implement the REST-style service contract</span></span>  
 <span data-ttu-id="50adf-110">實作 REST 樣式服務合約：</span><span class="sxs-lookup"><span data-stu-id="50adf-110">Implement the REST-style service contract:</span></span>  
  
```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }
    
    public string Echo(string input)
    {
        return input;
    }
}
```
  
## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="50adf-111">定義 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="50adf-111">Define the WCF service contract</span></span>  
 <span data-ttu-id="50adf-112">定義要用來呼叫 REST 樣式服務的 WCF 服務合約：</span><span class="sxs-lookup"><span data-stu-id="50adf-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>  
  
```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);
    
    [OperationContract]
    string CallEcho(string input);
}
```  
  
## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="50adf-113">實作 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="50adf-113">Implement the WCF service contract</span></span>  
 <span data-ttu-id="50adf-114">實作 WCF 服務合約：</span><span class="sxs-lookup"><span data-stu-id="50adf-114">Implement the WCF service contract:</span></span>  
  
```csharp
public class NormalService : INormalInterface  
{  
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
    public int CallAdd(int x, int y)  
    {  
        return client.Add(x, y);  
    }  
    
    public string CallEcho(string input)  
    {  
        return client.Echo(input);  
    }  
}  
```  
  
## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="50adf-115">為 REST 樣式服務建立用戶端 Proxy</span><span class="sxs-lookup"><span data-stu-id="50adf-115">Create the client proxy for the REST-style service</span></span>  
 <span data-ttu-id="50adf-116">使用<!--zz<xref:System.ServiceModel.ClientBase%60>-->`System.ServiceModel.ClientBase`實作用戶端 proxy。</span><span class="sxs-lookup"><span data-stu-id="50adf-116">Using <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` implement the client proxy.</span></span> <span data-ttu-id="50adf-117">針對所呼叫的每個方法，會建立一個新的 <xref:System.ServiceModel.OperationContextScope>，並用來呼叫作業。</span><span class="sxs-lookup"><span data-stu-id="50adf-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>  
  
```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```  
  
## <a name="host-and-call-the-services"></a><span data-ttu-id="50adf-118">裝載和呼叫服務</span><span class="sxs-lookup"><span data-stu-id="50adf-118">Host and call the services</span></span>  
 <span data-ttu-id="50adf-119">將兩個服務都裝載在主控台應用程式中，並加入所需的端點和行為。</span><span class="sxs-lookup"><span data-stu-id="50adf-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="50adf-120">然後呼叫一般 WCF 服務：</span><span class="sxs-lookup"><span data-stu-id="50adf-120">And then call the regular WCF service:</span></span>  
  
```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```  
  
## <a name="complete-code-listing"></a><span data-ttu-id="50adf-121">列出完整的程式碼清單</span><span class="sxs-lookup"><span data-stu-id="50adf-121">Complete code listing</span></span>  
 <span data-ttu-id="50adf-122">以下是本主題實作範例的完整清單：</span><span class="sxs-lookup"><span data-stu-id="50adf-122">The following is a complete listing of the sample implemented in this topic:</span></span>  
  
```csharp
public class CallingRESTSample  
{  
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";  
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";  

    [ServiceContract]  
    public interface IRestInterface  
    {  
        [OperationContract, WebGet]  
        int Add(int x, int y);  
        [OperationContract, WebGet]  
        string Echo(string input);  
    }  

    [ServiceContract]  
    public interface INormalInterface  
    {  
        [OperationContract]  
        int CallAdd(int x, int y);  
        [OperationContract]  
        string CallEcho(string input);  
    }  

    public class RestService : IRestInterface  
    {  
        public int Add(int x, int y)  
        {  
            return x + y;  
        }  

        public string Echo(string input)  
        {  
            return input;  
        }  
    }  

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface  
    {  
        public MyRestClient(string address)  
            : base(new WebHttpBinding(), new EndpointAddress(address))  
        {  
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());  
        }  

        public int Add(int x, int y)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Add(x, y);  
            }  
        }  

        public string Echo(string input)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Echo(input);  
            }  
        }  
    }  

    public class NormalService : INormalInterface  
    {  
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
        public int CallAdd(int x, int y)  
        {  
            return client.Add(x, y);  
        }  

        public string CallEcho(string input)  
        {  
            return client.Echo(input);  
        }  
    }
    
    public static void Main()  
    {  
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));  
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
        restHost.Open();  

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));  
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");  
        normalHost.Open();  

        Console.WriteLine("Hosts opened");  

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));  
        INormalInterface proxy = factory.CreateChannel();  

        Console.WriteLine(proxy.CallAdd(123, 456));  
        Console.WriteLine(proxy.CallEcho("Hello world"));  
    }  
}
```
  
## <a name="see-also"></a><span data-ttu-id="50adf-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50adf-123">See Also</span></span>  
 [<span data-ttu-id="50adf-124">如何： 建立基本 WCF Web HTTP 服務</span><span class="sxs-lookup"><span data-stu-id="50adf-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 [<span data-ttu-id="50adf-125">WCF Web HTTP 程式設計物件模型</span><span class="sxs-lookup"><span data-stu-id="50adf-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
