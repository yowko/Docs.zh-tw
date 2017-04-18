---
title: "含 WCF 服務的 ASMX 用戶端 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 含 WCF 服務的 ASMX 用戶端
這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 建立服務，然後從像是 ASMX 用戶端的非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端存取服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例是由用戶端主控台程式 \(.exe\) 和網際網路資訊服務 \(IIS\) 所裝載的服務程式庫 \(.dll\) 所組成。服務會實作定義要求\-回覆通訊模式的合約。合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 \(`Add`、`Subtract`、`Multiply` 和 `Divide`\)。ASMX 用戶端會對數學運算作業提出同步要求，服務則會以結果回覆。  
  
 此服務會實作 `ICalculator` 合約，如下列程式碼中所定義。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer> 會將 CLR 型別對應成 XML 表示。<xref:System.Runtime.Serialization.DataContractSerializer> 解譯某些 XML 表示的方式與 XmlSerializer 的方式不同。當使用 XmlSerializer 時，非 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Proxy 產生器 \(例如 Wsdl.exe\) 會產生更實用的介面。<xref:System.ServiceModel.XmlSerializerFormatAttribute> 會套用至 `ICalculator` 介面，以確定已使用 XmlSerializer 將 CLR 型別對應至 XML。服務實作會計算並傳回適當結果。  
  
 此服務會公開 \(Expose\) 單一的端點來與已使用組態檔 Web.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。服務會公開位在網際網路資訊服務 \(IIS\) 主機提供之基底位址上的端點。`binding` 屬性會設定為 basicHttpBinding，它會提供使用 SOAP 1.1 並與 WS\-I BasicProfile 1.1 相容的 HTTP 通訊，如下列範例組態所示。  
  
```  
<services>  
   <service   
       name="Microsoft.ServiceModel.Samples.CalculatorService"  
       behaviorConfiguration="CalculatorServiceBehavior">  
       <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
      <endpoint address=""  
               binding="basicHttpBinding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
</services>  
  
```  
  
 ASMX 用戶端會使用具型別的 Proxy \(由 Web Services Description Language \(WSDL\) 公用程式 \(Wsdl.exe\) 所產生\) 來與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務進行通訊。此具型別的 Proxy 會包含在 generatedClient.cs 檔中。WSDL 公用程式會擷取所指定服務的中繼資料，然後產生讓用戶端用來進行通訊的具型別 Proxy。根據預設，此架構不會公開任何中繼資料。若要公開產生 Proxy 時的必要中繼資料，您必須新增 [\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)，並將其 `httpGetEnabled` 屬性設定為 `True`，如下列組態所示。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 請從用戶端目錄中的命令提示字元執行下列命令，以產生具有型別的 Proxy。  
  
```  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
  
```  
  
 藉由使用產生之具型別的 Proxy，用戶端便可以設定適當的位址來存取指定的服務端點。用戶端會使用組態檔 \(App.config\) 來指定要進行通訊的端點。  
  
```  
<appSettings>  
      <add key="CalculatorServiceAddress"   
      value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
  
```  
  
 用戶端實作會建構要開始與服務進行通訊之具型別 Proxy 的執行個體。  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
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
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
  
```  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨機器的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示進行。  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 傳遞和傳回複雜資料型別的詳細資訊，請參閱：[Windows Forms 用戶端中的資料繫結](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md)、[Windows Presentation Foundation 用戶端中的資料繫結](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)和 [ASP.NET 用戶端中的資料繫結](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## 請參閱