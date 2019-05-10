---
title: HOW TO：使用 WCF REST 程式設計模型建立接受任意資料的服務
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: a1c30491f6c5b0a91f93a6f26417f9dc2b996a48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614783"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="27e33-102">HOW TO：使用 WCF REST 程式設計模型建立接受任意資料的服務</span><span class="sxs-lookup"><span data-stu-id="27e33-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="27e33-103">有時候，開發人員必須要能夠完全控制資料從服務作業傳回的方式。</span><span class="sxs-lookup"><span data-stu-id="27e33-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="27e33-104">這是服務作業必須傳回格式的資料不支援 byWCF 情況。</span><span class="sxs-lookup"><span data-stu-id="27e33-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="27e33-105">本主題說明如何使用 WCF REST 程式設計模型建立接收任意資料的服務。</span><span class="sxs-lookup"><span data-stu-id="27e33-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="27e33-106">若要實作服務合約</span><span class="sxs-lookup"><span data-stu-id="27e33-106">To implement the service contract</span></span>  
  
1. <span data-ttu-id="27e33-107">定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="27e33-107">Define the service contract.</span></span> <span data-ttu-id="27e33-108">接收任意資料的作業必須擁有 <xref:System.IO.Stream> 型別的參數。</span><span class="sxs-lookup"><span data-stu-id="27e33-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="27e33-109">此外，此參數必須是以要求本文傳遞的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="27e33-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="27e33-110">此範例中說明的作業也會接收檔案名稱參數。</span><span class="sxs-lookup"><span data-stu-id="27e33-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="27e33-111">這個參數會透過要求的 URL 來傳遞。</span><span class="sxs-lookup"><span data-stu-id="27e33-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="27e33-112">您可以在 <xref:System.UriTemplate> 中指定 <xref:System.ServiceModel.Web.WebInvokeAttribute>，指定以 URL 傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="27e33-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="27e33-113">在此情況下，URI 用來呼叫這個方法將於"UploadFile/Some-filename"結束。</span><span class="sxs-lookup"><span data-stu-id="27e33-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="27e33-114">URI 範本的"{filename}"部份會指定作業的檔案名稱參數會傳遞用來呼叫作業的 URI 內。</span><span class="sxs-lookup"><span data-stu-id="27e33-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. <span data-ttu-id="27e33-115">實作服務合約。</span><span class="sxs-lookup"><span data-stu-id="27e33-115">Implement the service contract.</span></span> <span data-ttu-id="27e33-116">此合約只有一個方法 `UploadFile`，其可接收資料流中任意資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="27e33-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="27e33-117">作業會讀取計算讀取之位元組數目的資料流，然後顯示該檔案名稱和所讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="27e33-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a><span data-ttu-id="27e33-118">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="27e33-118">To host the service</span></span>  
  
1. <span data-ttu-id="27e33-119">建立裝載服務的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="27e33-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. <span data-ttu-id="27e33-120">建立一個變數，以保留該服務位於 `Main`方法內的基底位址。</span><span class="sxs-lookup"><span data-stu-id="27e33-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="27e33-121">建立可指定該服務類別及基底位址之服務的 <xref:System.ServiceModel.ServiceHost> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="27e33-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="27e33-122">加入指定合約、<xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior> 的端點。</span><span class="sxs-lookup"><span data-stu-id="27e33-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="27e33-123">開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="27e33-123">Open the service host.</span></span> <span data-ttu-id="27e33-124">現在服務已準備好接收要求。</span><span class="sxs-lookup"><span data-stu-id="27e33-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="27e33-125">以程式設計的方式呼叫服務</span><span class="sxs-lookup"><span data-stu-id="27e33-125">To call the service programmatically</span></span>  
  
1. <span data-ttu-id="27e33-126">使用用來呼叫服務的 URI 建立 <xref:System.Net.HttpWebRequest>。</span><span class="sxs-lookup"><span data-stu-id="27e33-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="27e33-127">在此程式碼中，基底位址會與 `"/UploadFile/Text"` 合併。</span><span class="sxs-lookup"><span data-stu-id="27e33-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="27e33-128">URI 的 `"UploadFile"` 部份會指定要呼叫的作業。</span><span class="sxs-lookup"><span data-stu-id="27e33-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="27e33-129">URI 的 `"Test.txt"` 部份會指定要傳遞至 `UploadFile` 作業的檔案名稱參數。</span><span class="sxs-lookup"><span data-stu-id="27e33-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="27e33-130">這兩個項目都對應到已套用至此作業合約的 <xref:System.UriTemplate>。</span><span class="sxs-lookup"><span data-stu-id="27e33-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <span data-ttu-id="27e33-131">將 <xref:System.Net.HttpWebRequest.Method%2A> 的 <xref:System.Net.HttpWebRequest> 屬性設為 `POST`，以及 <xref:System.Net.HttpWebRequest.ContentType%2A> 屬性設為 `"text/plain"`。</span><span class="sxs-lookup"><span data-stu-id="27e33-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="27e33-132">這樣做會告知服務，程式碼將傳送資料且資料為純文字。</span><span class="sxs-lookup"><span data-stu-id="27e33-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <span data-ttu-id="27e33-133">呼叫 <xref:System.Net.HttpWebRequest.GetRequestStream%2A> 取得要求資料流，建立要傳送的資料，將該資料寫入要求資料流，然後關閉資料流。</span><span class="sxs-lookup"><span data-stu-id="27e33-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4. <span data-ttu-id="27e33-134">透過呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A> 取得服務的回應，然後對主控台顯示回應資料。</span><span class="sxs-lookup"><span data-stu-id="27e33-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. <span data-ttu-id="27e33-135">關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="27e33-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="27e33-136">範例</span><span class="sxs-lookup"><span data-stu-id="27e33-136">Example</span></span>  
 <span data-ttu-id="27e33-137">以下是這個範例的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="27e33-137">The following is a complete listing of the code for this example.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27e33-138">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="27e33-138">Compiling the Code</span></span>  
  
- <span data-ttu-id="27e33-139">編譯程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll</span><span class="sxs-lookup"><span data-stu-id="27e33-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e33-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27e33-140">See also</span></span>

- [<span data-ttu-id="27e33-141">UriTemplate 與 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="27e33-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="27e33-142">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="27e33-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="27e33-143">WCF Web HTTP 程式設計模型概觀</span><span class="sxs-lookup"><span data-stu-id="27e33-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
