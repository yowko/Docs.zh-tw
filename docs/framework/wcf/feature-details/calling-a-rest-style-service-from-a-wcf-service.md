---
title: "從 WCF 服務呼叫 REST 樣式服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 從 WCF 服務呼叫 REST 樣式服務
由規則 \(以 SOAP 為基礎\) WCF 服務呼叫 REST 樣式服務時，服務方法的作業內容 \(包含傳入要求的相關資訊\) 會覆寫應該由輸出要求使用的內容。  這會導致 HTTP GET 要求變更為 HTTP POST 要求。  若要強制 WCF 服務使用正確的內容來呼叫 REST 樣式服務，請建立新的 <xref:System.ServiceModel.OperationContextScope>，並從作業內容範圍內呼叫 REST 樣式服務。  本主題將說明如何建立簡單的範例來示範這個技巧。  
  
## 定義 REST 樣式服務合約  
 定義簡單的 REST 樣式服務合約：  
  
```  
[ServiceContract]  
        public interface IRestInterface  
        {  
            [OperationContract, WebGet]  
            int Add(int x, int y);  
            [OperationContract, WebGet]  
            string Echo(string input);  
        }  
```  
  
## 實作 REST 樣式服務合約  
 實作 REST 樣式服務合約：  
  
```  
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
  
## 定義 WCF 服務合約  
 定義要用來呼叫 REST 樣式服務的 WCF 服務合約：  
  
```  
[ServiceContract]  
 public interface INormalInterface  
 {  
     [OperationContract]  
     int CallAdd(int x, int y);  
     [OperationContract]  
     string CallEcho(string input);  
 }  
```  
  
## 實作 WCF 服務合約  
 實作 WCF 服務合約：  
  
```  
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
  
## 為 REST 樣式服務建立用戶端 Proxy  
 使用 <xref:System.ServiceModel.ClientBase%60> 實作用戶端 Proxy。  針對所呼叫的每個方法，會建立一個新的 <xref:System.ServiceModel.OperationContextScope>，並用來呼叫作業。  
  
```  
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
  
## 裝載和呼叫服務  
 將兩個服務都裝載在主控台應用程式中，並加入所需的端點和行為。  然後呼叫一般 WCF 服務：  
  
```  
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
  
## 列出完整的程式碼清單  
 以下是本主題實作範例的完整清單：  
  
```  
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
  
## 請參閱  
 [HOW TO：建立基本 WCF Web HTTP 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)   
 [WCF Web HTTP 程式設計物件模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)