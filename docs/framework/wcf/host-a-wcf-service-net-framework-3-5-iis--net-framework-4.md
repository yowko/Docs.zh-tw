---
title: HOW TO：在 .NET Framework 4 下執行的 IIS 中，裝載以 .NET Framework 3.5 寫入的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 83343cef119f6c8b97fd8f1be50c229c64b10227
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499124"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="1e05b-102">HOW TO：在 .NET Framework 4 下執行的 IIS 中，裝載以 .NET Framework 3.5 寫入的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="1e05b-102">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>
<span data-ttu-id="1e05b-103">裝載 Windows Communication Foundation (WCF) 服務，以撰寫時[!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]上執行的機器[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]，您可能會收到<xref:System.ServiceModel.ProtocolException>包含下列文字。</span><span class="sxs-lookup"><span data-stu-id="1e05b-103">When hosting a Windows Communication Foundation (WCF) service written with [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] on a machine running [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>  
  
```Output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="1e05b-104">或者，如果您嘗試瀏覽至服務的 .svc 檔，則可能會看到包含下列文字的錯誤網頁。</span><span class="sxs-lookup"><span data-stu-id="1e05b-104">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```Output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="1e05b-105">因為應用程式網域 IIS 執行的是 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，而 WCF 服務預期在 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 下執行，所以會發生這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e05b-105">These errors occur because the application domain IIS is running within is running [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] and the WCF service is expecting to run under [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="1e05b-106">本主題說明要讓服務執行所需進行的修改。</span><span class="sxs-lookup"><span data-stu-id="1e05b-106">This topic explains the modifications required to get the service to run.</span></span>  
  
 <span data-ttu-id="1e05b-107">下一個尋找 <`compilers`> 項目和變更的項目的 CompilerVersion 提供者選項的值為 4.0。</span><span class="sxs-lookup"><span data-stu-id="1e05b-107">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="1e05b-108">根據預設，有兩個 <`compiler`> 下的項目 <`compilers`> 項目。</span><span class="sxs-lookup"><span data-stu-id="1e05b-108">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="1e05b-109">您必須更新這兩個項目的 CompilerVersion 提供者選項，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e05b-109">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="1e05b-110">加入必要的 targetFramework 屬性</span><span class="sxs-lookup"><span data-stu-id="1e05b-110">Add the required targetFramework attribute</span></span>  
  
1.  <span data-ttu-id="1e05b-111">開啟服務的 Web.config 檔並尋找 <`compilation`> 項目。</span><span class="sxs-lookup"><span data-stu-id="1e05b-111">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2.  <span data-ttu-id="1e05b-112">新增`targetFramework`屬性加入 <`compilation`> 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e05b-112">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  <span data-ttu-id="1e05b-113">尋找 <`compilers`> 項目和變更的項目的 CompilerVersion 提供者選項的值為 4.0。</span><span class="sxs-lookup"><span data-stu-id="1e05b-113">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="1e05b-114">根據預設，有兩個 <`compiler`> 下的項目 <`compilers`> 項目。</span><span class="sxs-lookup"><span data-stu-id="1e05b-114">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="1e05b-115">您必須更新這兩個項目的 CompilerVersion 提供者選項，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1e05b-115">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
