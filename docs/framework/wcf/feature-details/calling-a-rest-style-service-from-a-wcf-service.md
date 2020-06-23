---
title: 從 WCF 服務呼叫 REST 樣式服務
description: 瞭解如何藉由建立範圍並從該範圍呼叫 REST 樣式服務，讓 WCF 服務使用與 REST 樣式服務的正確內容。
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 15f468923cf55feb85e7aeca1a2cc5e38050d665
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245293"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="792cc-103">從 WCF 服務呼叫 REST 樣式服務</span><span class="sxs-lookup"><span data-stu-id="792cc-103">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="792cc-104">由規則 (以 SOAP 為基礎) WCF 服務呼叫 REST 樣式服務時，服務方法的作業內容 (包含傳入要求的相關資訊) 會覆寫應該由輸出要求使用的內容。</span><span class="sxs-lookup"><span data-stu-id="792cc-104">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="792cc-105">這會導致 HTTP GET 要求變更為 HTTP POST 要求。</span><span class="sxs-lookup"><span data-stu-id="792cc-105">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="792cc-106">若要強制 WCF 服務使用正確的內容來呼叫 REST 樣式服務，請建立新的 <xref:System.ServiceModel.OperationContextScope>，並從作業內容範圍內呼叫 REST 樣式服務。</span><span class="sxs-lookup"><span data-stu-id="792cc-106">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="792cc-107">本主題將說明如何建立簡單的範例來示範這個技巧。</span><span class="sxs-lookup"><span data-stu-id="792cc-107">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="792cc-108">定義 REST 樣式服務合約</span><span class="sxs-lookup"><span data-stu-id="792cc-108">Define the REST-style service contract</span></span>

<span data-ttu-id="792cc-109">定義簡單的 REST 樣式服務合約：</span><span class="sxs-lookup"><span data-stu-id="792cc-109">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="792cc-110">實作 REST 樣式服務合約</span><span class="sxs-lookup"><span data-stu-id="792cc-110">Implement the REST-style service contract</span></span>

<span data-ttu-id="792cc-111">實作 REST 樣式服務合約：</span><span class="sxs-lookup"><span data-stu-id="792cc-111">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="792cc-112">定義 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="792cc-112">Define the WCF service contract</span></span>

<span data-ttu-id="792cc-113">定義要用來呼叫 REST 樣式服務的 WCF 服務合約：</span><span class="sxs-lookup"><span data-stu-id="792cc-113">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="792cc-114">實作 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="792cc-114">Implement the WCF service contract</span></span>

<span data-ttu-id="792cc-115">實作 WCF 服務合約：</span><span class="sxs-lookup"><span data-stu-id="792cc-115">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="792cc-116">為 REST 樣式服務建立用戶端 Proxy</span><span class="sxs-lookup"><span data-stu-id="792cc-116">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="792cc-117">使用 <xref:System.ServiceModel.ClientBase%601> 來執行用戶端 proxy。</span><span class="sxs-lookup"><span data-stu-id="792cc-117">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="792cc-118">針對所呼叫的每個方法，會建立一個新的 <xref:System.ServiceModel.OperationContextScope>，並用來呼叫作業。</span><span class="sxs-lookup"><span data-stu-id="792cc-118">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="792cc-119">裝載和呼叫服務</span><span class="sxs-lookup"><span data-stu-id="792cc-119">Host and call the services</span></span>

<span data-ttu-id="792cc-120">將兩個服務都裝載在主控台應用程式中，並加入所需的端點和行為。</span><span class="sxs-lookup"><span data-stu-id="792cc-120">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="792cc-121">然後呼叫一般 WCF 服務：</span><span class="sxs-lookup"><span data-stu-id="792cc-121">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="792cc-122">完整程式碼清單</span><span class="sxs-lookup"><span data-stu-id="792cc-122">Complete code listing</span></span>

<span data-ttu-id="792cc-123">以下是本主題實作範例的完整清單：</span><span class="sxs-lookup"><span data-stu-id="792cc-123">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="792cc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="792cc-124">See also</span></span>

- [<span data-ttu-id="792cc-125">如何：建立基本 WCF Web HTTP 服務</span><span class="sxs-lookup"><span data-stu-id="792cc-125">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="792cc-126">WCF Web HTTP 程式設計物件模型</span><span class="sxs-lookup"><span data-stu-id="792cc-126">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
