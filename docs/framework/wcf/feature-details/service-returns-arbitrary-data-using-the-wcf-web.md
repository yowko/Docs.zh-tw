---
title: HOW TO：建立傳回任意使用 WCF Web HTTP 程式設計模型的資料服務
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 187db6d3c19373270b25000029f51aa70a81afd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576391"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>HOW TO：建立傳回任意使用 WCF Web HTTP 程式設計模型的資料服務
有時候，開發人員必須要能夠完全控制資料從服務作業傳回的方式。 這是服務作業必須由 WCF 不支援的格式傳回資料的情況。 本主題說明如何使用 WCF WEB HTTP 程式設計模型建立這類服務。 該項服務提供一種會傳回資料流的作業。  
  
### <a name="to-implement-the-service-contract"></a>若要實作服務合約  
  
1.  定義服務合約。 該合約名稱為 `IImageServer`，並且擁有會傳回 `GetImage`的<xref:System.IO.Stream> 方法。  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     因為此方法會傳回<xref:System.IO.Stream>WCF 會假設作業具有完整控制權會從服務作業傳回的位元組，它會套用任何格式傳回的資料。  
  
2.  實作服務合約。 該合約只能有一項作業 (`GetImage`)。 這個方法會產生一張點陣圖，然後以 JPG 格式儲存為 <xref:System.IO.MemoryStream>。 然後，這個作業會將該資料流傳回給呼叫者。  
  
    ```  
    public class Service : IImageServer  
       {  
           public Stream GetImage(int width, int height)  
           {  
               Bitmap bitmap = new Bitmap(width, height);  
               for (int i = 0; i < bitmap.Width; i++)  
               {  
                   for (int j = 0; j < bitmap.Height; j++)  
                   {  
                       bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                   }  
               }  
               MemoryStream ms = new MemoryStream();  
               bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
               ms.Position = 0;  
               WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
               return ms;  
           }  
       }  
    ```  
  
     請注意程式碼的倒數第二行：`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     這會將內容類型標頭`"image/jpeg"`。 雖然本範例示範的是如何傳回 JPG 檔案，但是您可以修改範例內容，使其傳回您所需的任何資料類型。 該作業必須要擷取或產生資料，然後將資料寫入資料流中。  
  
### <a name="to-host-the-service"></a>若要裝載服務  
  
1.  建立裝載服務的主控台應用程式。  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  建立一個變數，以保留該服務位於 `Main`方法內的基底位址。  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  指定服務類別及基底位址，以建立該服務的 <xref:System.ServiceModel.ServiceHost> 執行個體。  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  利用 <xref:System.ServiceModel.WebHttpBinding> 及 <xref:System.ServiceModel.Description.WebHttpBehavior>加入一個端點。  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  開啟服務主機。  
  
    ```  
    host.Open()  
    ```  
  
6.  等候使用者按下 ENTER 終止該服務。  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>若要使用 Internet Explorer 呼叫原始服務  
  
1.  執行服務後，您應該會看見下列來自服務的輸出： `Service is running Press ENTER to close the host`  
  
2.  開啟 Internet Explorer，輸入 `http://localhost:8000/Service/GetImage?width=50&height=40`，您應該會看見對角線為藍色的黃色長方形。  
  
## <a name="example"></a>範例  
 以下是這個主題的完整程式碼清單。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   編譯範例程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。  
  
## <a name="see-also"></a>另請參閱
- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
