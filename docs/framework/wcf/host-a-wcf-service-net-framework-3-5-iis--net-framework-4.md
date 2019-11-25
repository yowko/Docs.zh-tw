---
title: HOW TO：在 .NET Framework 4 下執行的 IIS 中，裝載以 .NET Framework 3.5 寫入的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: d827fe82e8b355c8818d96645b463c1840910a9c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283270"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="e837f-102">HOW TO：在 .NET Framework 4 下執行的 IIS 中，裝載以 .NET Framework 3.5 寫入的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="e837f-102">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>

<span data-ttu-id="e837f-103">在執行 .NET Framework 4 的電腦上裝載以 .NET Framework 3.5 撰寫的 Windows Communication Foundation （WCF）服務時，您可能會收到包含下列文字的 <xref:System.ServiceModel.ProtocolException>。</span><span class="sxs-lookup"><span data-stu-id="e837f-103">When hosting a Windows Communication Foundation (WCF) service written with .NET Framework 3.5 on a machine running .NET Framework 4, you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="e837f-104">或者，如果您嘗試瀏覽至服務的 .svc 檔，則可能會看到包含下列文字的錯誤網頁。</span><span class="sxs-lookup"><span data-stu-id="e837f-104">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="e837f-105">之所以發生這些錯誤，是因為 IIS 執行所在的應用程式域 .NET Framework 4，而 WCF 服務預期會在 .NET Framework 3.5 之下執行。</span><span class="sxs-lookup"><span data-stu-id="e837f-105">These errors occur because the application domain IIS is running within is running .NET Framework 4 and the WCF service is expecting to run under .NET Framework 3.5.</span></span> <span data-ttu-id="e837f-106">本主題說明要讓服務執行所需進行的修改。</span><span class="sxs-lookup"><span data-stu-id="e837f-106">This topic explains the modifications required to get the service to run.</span></span>
  
 <span data-ttu-id="e837f-107">接著，尋找 <`compilers`> 元素，並將 CompilerVersion 提供者選項變更為具有4.0 的值。</span><span class="sxs-lookup"><span data-stu-id="e837f-107">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="e837f-108">根據預設，<`compilers`> 元素下有兩個 <`compiler`> 元素。</span><span class="sxs-lookup"><span data-stu-id="e837f-108">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="e837f-109">您必須更新這兩個項目的 CompilerVersion 提供者選項，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e837f-109">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
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
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="e837f-110">加入必要的 targetFramework 屬性</span><span class="sxs-lookup"><span data-stu-id="e837f-110">Add the required targetFramework attribute</span></span>  
  
1. <span data-ttu-id="e837f-111">開啟服務的 Web.config 檔案，並尋找 <`compilation`> 元素。</span><span class="sxs-lookup"><span data-stu-id="e837f-111">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2. <span data-ttu-id="e837f-112">將 `targetFramework` 屬性加入至 <`compilation`> 元素，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e837f-112">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
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
  
3. <span data-ttu-id="e837f-113">尋找 <`compilers`> 元素，並將 CompilerVersion 提供者選項變更為具有4.0 的值。</span><span class="sxs-lookup"><span data-stu-id="e837f-113">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="e837f-114">根據預設，<`compilers`> 元素下有兩個 <`compiler`> 元素。</span><span class="sxs-lookup"><span data-stu-id="e837f-114">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="e837f-115">您必須更新這兩個項目的 CompilerVersion 提供者選項，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e837f-115">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
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
