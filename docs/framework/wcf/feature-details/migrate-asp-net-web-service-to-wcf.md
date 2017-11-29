---
title: "HOW TO：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 94d6cc499caddc8b3cbbf8ba7845e4de5441165c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a>HOW TO：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation
下列程序會描述如何將 ASP.NET Web 服務移轉至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a>將 ASP.NET Web 服務程式碼移轉至 WCF  
  
1.  請確定已存有服務的一組完整測試。  
  
2.  針對服務產生 WSDL，並在存放服務的 .asmx 檔案之相同資料夾中儲存複本。  
  
3.  升級 ASP.NET Web 服務以使用 .NET 2.0。 第一次在 IIS 中，應用程式部署.NET Framework 2.0，然後使用 Visual Studio 2005 自動化程式碼轉換處理程序中所述[逐步指南將 Web 專案從 Visual Studio.NET 2002年/2003 至 Visual Studio2005](http://go.microsoft.com/fwlink/?LinkId=96492)。 執行這組測試。  
  
4.  提供 `Namespace` 屬性之 `Name` 和 <xref:System.Web.Services.WebService> 參數的明確值 (如果尚未提供)。 對 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數執行一樣的動作。 如果尚未針對將要求遞送至方法時所使用 SOAPAction HTTP 標頭提供明確值，請使用 `Action` 明確指定 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> 參數的預設值。  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  測試變更。  
  
6.  將類別的方法之本文中的獨立程式碼移至原始類別要使用的不同類別。  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  測試變更。  
  
8.  將參考新增至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 組件 System.ServiceModel，並將 System.Runtime.Serialization 新增至 ASP.NET Web 服務專案。  
  
9. 執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]從 WSDL 的用戶端類別。 將產生的類別模組新增至解決方案。  
  
10. 前一個步驟所產生的類別模組會包含介面定義。  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     修改 ASP.NET Web 服務類別的定義，如此會將類別定義為實作該介面，如下列程式碼範例所示。  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. 編譯專案。 由於步驟九中產生的程式碼複製了某些型別定義，因此可能會出現一些錯誤。 通常刪除預先存在的型別定義即可修復這些錯誤。 測試變更。  
  
12. 移除 ASP.NET 特定的屬性，例如 <xref:System.Web.Services.WebService>、<xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>。  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. 如果 ASP.NET Web 服務依賴下列任一項，那麼請將類別 (目前為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務類型) 設定為需要 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET 相容模式：  
  
    -   <xref:System.Web.HttpContext> 類別。  
  
    -   ASP.NET 設定檔。  
  
    -   在 .asmx 檔案上的 ACL。  
  
    -   IIS 驗證選項。  
  
    -   ASP.NET 模擬選項。  
  
    -   ASP.NET 全球化。  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. 將原始 .asmx 檔案重新命名為 .asmx.old。  
  
15. 對服務建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務檔，將副檔名設為 .asmx，然後儲存至 IIS 的應用程式根目錄中。  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. 將服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 組態新增至其 Web.config 檔。 將服務設定為使用[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 使用在前述步驟中，建立副檔名為.asmx 服務檔和 WSDL 不會產生其本身，但若要使用從第二個步驟的 WSDL。 必要時，也設定為使用 ASP.NET 相容模式。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address=""  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
17. 儲存組態。  
  
18. 編譯專案。  
  
19. 執行一組測試，以確定所有變更都已生效。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
