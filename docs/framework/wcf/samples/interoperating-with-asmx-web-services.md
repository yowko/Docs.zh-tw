---
title: 與 ASMX Web 服務交互操作
ms.date: 03/30/2017
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
ms.openlocfilehash: b5af8f15d38f730d2243c642d4623c0bc6e1343c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183579"
---
# <a name="interoperating-with-asmx-web-services"></a>與 ASMX Web 服務交互操作
此示例演示如何將 Windows 通信基礎 （WCF） 用戶端應用程式與現有的 ASMX Web 服務集成。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例是由用戶端主控台程式 (.exe) 和網際網路資訊服務 (IIS) 所裝載的服務程式庫 (.dll) 所組成。 此服務是 ASMX Web 服務，會實作定義要求-回覆通訊模式的合約。 此服務會公開數學作業 (`Add`、`Subtract`、`Multiply` 和 `Divide`)。 用戶端會對數學運算作業提出同步要求，服務則會以結果回覆。 您可以在主控台視窗中看到用戶端活動。  
  
 下列範例程式碼中示範的 ASMX Web 服務實作會計算並傳回適當的結果。  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 配置後，同一台電腦上的用戶端可以在該`http://localhost/servicemodelsamples/service.asmx`電腦上訪問該服務。 若要讓遠端電腦上的用戶端存取服務，就必須指定完整的網域名稱，而不是 localhost。  
  
 通信是通過[服務模型中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成的用戶端完成的。 用戶端會包含在 generatedClient.cs 檔案中。 ASMX 服務必須可供使用才能產生 Proxy 程式碼，因為它可用於擷取更新的中繼資料。 請從用戶端目錄中的命令提示字元執行下列命令，以產生具有型別的 Proxy。  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 透過使用產生的用戶端，您可以藉由設定適當的位址和繫結來存取服務端點。 與服務相同，用戶端使用組態檔 (App.config) 來指定要通訊的端點。 用戶端的端點組態是由服務端點的絕對位址、繫結和合約所組成，如下列範例組態所示。  
  
```xml  
<client>  
   <endpoint
      address="http://localhost/ServiceModelSamples/service.asmx"
      binding="basicHttpBinding"
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 用戶端實作會建構所產生之用戶端的執行個體。 然後，產生的用戶端就可以用來與服務通訊。  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
