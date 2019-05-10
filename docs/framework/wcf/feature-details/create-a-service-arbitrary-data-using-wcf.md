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
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>HOW TO：使用 WCF REST 程式設計模型建立接受任意資料的服務
有時候，開發人員必須要能夠完全控制資料從服務作業傳回的方式。 這是服務作業必須傳回格式的資料不支援 byWCF 情況。 本主題說明如何使用 WCF REST 程式設計模型建立接收任意資料的服務。  
  
### <a name="to-implement-the-service-contract"></a>若要實作服務合約  
  
1. 定義服務合約。 接收任意資料的作業必須擁有 <xref:System.IO.Stream> 型別的參數。 此外，此參數必須是以要求本文傳遞的唯一參數。 此範例中說明的作業也會接收檔案名稱參數。 這個參數會透過要求的 URL 來傳遞。 您可以在 <xref:System.UriTemplate> 中指定 <xref:System.ServiceModel.Web.WebInvokeAttribute>，指定以 URL 傳遞參數。 在此情況下，URI 用來呼叫這個方法將於"UploadFile/Some-filename"結束。 URI 範本的"{filename}"部份會指定作業的檔案名稱參數會傳遞用來呼叫作業的 URI 內。  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. 實作服務合約。 此合約只有一個方法 `UploadFile`，其可接收資料流中任意資料的檔案。 作業會讀取計算讀取之位元組數目的資料流，然後顯示該檔案名稱和所讀取的位元組數目。  
  
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
  
### <a name="to-host-the-service"></a>若要裝載服務  
  
1. 建立裝載服務的主控台應用程式。  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. 建立一個變數，以保留該服務位於 `Main`方法內的基底位址。  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. 建立可指定該服務類別及基底位址之服務的 <xref:System.ServiceModel.ServiceHost> 執行個體。  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. 加入指定合約、<xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior> 的端點。  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. 開啟服務主機。 現在服務已準備好接收要求。  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>以程式設計的方式呼叫服務  
  
1. 使用用來呼叫服務的 URI 建立 <xref:System.Net.HttpWebRequest>。 在此程式碼中，基底位址會與 `"/UploadFile/Text"` 合併。 URI 的 `"UploadFile"` 部份會指定要呼叫的作業。 URI 的 `"Test.txt"` 部份會指定要傳遞至 `UploadFile` 作業的檔案名稱參數。 這兩個項目都對應到已套用至此作業合約的 <xref:System.UriTemplate>。  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. 將 <xref:System.Net.HttpWebRequest.Method%2A> 的 <xref:System.Net.HttpWebRequest> 屬性設為 `POST`，以及 <xref:System.Net.HttpWebRequest.ContentType%2A> 屬性設為 `"text/plain"`。 這樣做會告知服務，程式碼將傳送資料且資料為純文字。  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. 呼叫 <xref:System.Net.HttpWebRequest.GetRequestStream%2A> 取得要求資料流，建立要傳送的資料，將該資料寫入要求資料流，然後關閉資料流。  
  
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
  
4. 透過呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A> 取得服務的回應，然後對主控台顯示回應資料。  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. 關閉服務主機。  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>範例  
 以下是這個範例的完整程式碼清單。  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
- 編譯程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll  
  
## <a name="see-also"></a>另請參閱

- [UriTemplate 與 UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
