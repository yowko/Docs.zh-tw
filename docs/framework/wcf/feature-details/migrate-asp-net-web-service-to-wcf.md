---
title: HOW TO：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
ms.openlocfilehash: 90a6109a56299ec1bcaff4a35141abc194484772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496695"
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="70c44-102">HOW TO：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="70c44-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="70c44-103">下列程序說明如何將 ASP.NET Web 服務移轉到 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="70c44-103">The following procedure describes how to migrate an ASP.NET Web Service to Windows Communication Foundation (WCF).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="70c44-104">程序</span><span class="sxs-lookup"><span data-stu-id="70c44-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="70c44-105">將 ASP.NET Web 服務程式碼移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="70c44-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="70c44-106">請確定已存有服務的一組完整測試。</span><span class="sxs-lookup"><span data-stu-id="70c44-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="70c44-107">針對服務產生 WSDL，並在存放服務的 .asmx 檔案之相同資料夾中儲存複本。</span><span class="sxs-lookup"><span data-stu-id="70c44-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="70c44-108">升級 ASP.NET Web 服務以使用 .NET 2.0。</span><span class="sxs-lookup"><span data-stu-id="70c44-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="70c44-109">第一次在 IIS 中，應用程式部署.NET Framework 2.0，然後使用 Visual Studio 2005 自動化程式碼轉換處理程序中所述[逐步指南將 Web 專案從 Visual Studio.NET 2002年/2003 至 Visual Studio2005](http://go.microsoft.com/fwlink/?LinkId=96492)。</span><span class="sxs-lookup"><span data-stu-id="70c44-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="70c44-110">執行這組測試。</span><span class="sxs-lookup"><span data-stu-id="70c44-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="70c44-111">提供 `Namespace` 屬性之 `Name` 和 <xref:System.Web.Services.WebService> 參數的明確值 (如果尚未提供)。</span><span class="sxs-lookup"><span data-stu-id="70c44-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="70c44-112">對 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數執行一樣的動作。</span><span class="sxs-lookup"><span data-stu-id="70c44-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="70c44-113">如果尚未針對將要求遞送至方法時所使用 SOAPAction HTTP 標頭提供明確值，請使用 `Action` 明確指定 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> 參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="70c44-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
5.  <span data-ttu-id="70c44-114">測試變更。</span><span class="sxs-lookup"><span data-stu-id="70c44-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="70c44-115">將類別的方法之本文中的獨立程式碼移至原始類別要使用的不同類別。</span><span class="sxs-lookup"><span data-stu-id="70c44-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
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
  
7.  <span data-ttu-id="70c44-116">測試變更。</span><span class="sxs-lookup"><span data-stu-id="70c44-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="70c44-117">將 WCF 組件 System.ServiceModel，並將 System.Runtime.Serialization 參考加入至 ASP.NET Web 服務專案中。</span><span class="sxs-lookup"><span data-stu-id="70c44-117">Add references to WCF assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="70c44-118">執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從 WSDL 產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="70c44-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a WCF client class from the WSDL.</span></span> <span data-ttu-id="70c44-119">將產生的類別模組新增至解決方案。</span><span class="sxs-lookup"><span data-stu-id="70c44-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="70c44-120">前一個步驟所產生的類別模組會包含介面定義。</span><span class="sxs-lookup"><span data-stu-id="70c44-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
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
  
     <span data-ttu-id="70c44-121">修改 ASP.NET Web 服務類別的定義，如此會將類別定義為實作該介面，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="70c44-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
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
  
11. <span data-ttu-id="70c44-122">編譯專案。</span><span class="sxs-lookup"><span data-stu-id="70c44-122">Compile the project.</span></span> <span data-ttu-id="70c44-123">由於步驟九中產生的程式碼複製了某些型別定義，因此可能會出現一些錯誤。</span><span class="sxs-lookup"><span data-stu-id="70c44-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="70c44-124">通常刪除預先存在的型別定義即可修復這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="70c44-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="70c44-125">測試變更。</span><span class="sxs-lookup"><span data-stu-id="70c44-125">Test the change.</span></span>  
  
12. <span data-ttu-id="70c44-126">移除 ASP.NET 特定的屬性，例如 <xref:System.Web.Services.WebService>、<xref:System.Web.Services.WebMethodAttribute> 和 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>。</span><span class="sxs-lookup"><span data-stu-id="70c44-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
13. <span data-ttu-id="70c44-127">設定的類別，現在是 WCF 服務類型，需要 WCF ASP.NET 相容性模式，如果 ASP.NET Web 服務依賴下列任一項：</span><span class="sxs-lookup"><span data-stu-id="70c44-127">Configure the class, which is now a WCF service type, to require WCF ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="70c44-128"><xref:System.Web.HttpContext> 類別。</span><span class="sxs-lookup"><span data-stu-id="70c44-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="70c44-129">ASP.NET 設定檔。</span><span class="sxs-lookup"><span data-stu-id="70c44-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="70c44-130">在 .asmx 檔案上的 ACL。</span><span class="sxs-lookup"><span data-stu-id="70c44-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="70c44-131">IIS 驗證選項。</span><span class="sxs-lookup"><span data-stu-id="70c44-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="70c44-132">ASP.NET 模擬選項。</span><span class="sxs-lookup"><span data-stu-id="70c44-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="70c44-133">ASP.NET 全球化。</span><span class="sxs-lookup"><span data-stu-id="70c44-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="70c44-134">將原始 .asmx 檔案重新命名為 .asmx.old。</span><span class="sxs-lookup"><span data-stu-id="70c44-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="70c44-135">建立服務的 WCF 服務檔案，請將副檔名，.asmx，並將它儲存至 IIS 中的應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="70c44-135">Create a WCF service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="70c44-136">將服務的 WCF 組態加入至其 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="70c44-136">Add a WCF configuration for the service to its Web.config file.</span></span> <span data-ttu-id="70c44-137">將服務設定為使用[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 使用在前述步驟中，建立副檔名為.asmx 服務檔和 WSDL 不會產生其本身，但若要使用從第二個步驟的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="70c44-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="70c44-138">必要時，也設定為使用 ASP.NET 相容模式。</span><span class="sxs-lookup"><span data-stu-id="70c44-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
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
  
17. <span data-ttu-id="70c44-139">儲存組態。</span><span class="sxs-lookup"><span data-stu-id="70c44-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="70c44-140">編譯專案。</span><span class="sxs-lookup"><span data-stu-id="70c44-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="70c44-141">執行一組測試，以確定所有變更都已生效。</span><span class="sxs-lookup"><span data-stu-id="70c44-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c44-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70c44-142">See Also</span></span>  
 [<span data-ttu-id="70c44-143">如何：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="70c44-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
