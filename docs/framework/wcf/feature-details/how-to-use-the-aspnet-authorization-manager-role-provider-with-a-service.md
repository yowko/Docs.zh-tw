---
title: HOW TO：使用 ASP.NET 授權管理員角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 7c1076671512b33f115950cad684fba0b514abe9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595332"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="e018a-102">HOW TO：使用 ASP.NET 授權管理員角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="e018a-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="e018a-103">當 ASP.NET 裝載 Web 服務時，您可以將授權管理員整合至應用程式，以提供服務的授權。</span><span class="sxs-lookup"><span data-stu-id="e018a-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="e018a-104">授權管理員可讓應用程式開發人員定義個別作業，以便將作業分組，進而形成工作。</span><span class="sxs-lookup"><span data-stu-id="e018a-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="e018a-105">接著，系統管理員可以授權角色來執行特定工作或個別作業。</span><span class="sxs-lookup"><span data-stu-id="e018a-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="e018a-106">授權管理員會以 Microsoft Management Console (MMC) 嵌入式管理單元的形式提供系統管理工具，以管理角色、工作、作業和使用者。</span><span class="sxs-lookup"><span data-stu-id="e018a-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="e018a-107">系統管理員會在 XML 檔案、Active Directory 或「Active Directory 應用程式模式」(ADAM) 存放區中設定授權管理員原則存放區。</span><span class="sxs-lookup"><span data-stu-id="e018a-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="e018a-108">授權管理員會藉由為裝載 Web 服務的 ASP.NET 應用程式設定授權管理員 ASP.NET 角色提供者，整合到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="e018a-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="e018a-109">就像其他 ASP.NET 角色提供者一樣，授權管理員 ASP.NET 角色提供者也是使用 <`providers`> 元素來設定。</span><span class="sxs-lookup"><span data-stu-id="e018a-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="e018a-110">下列程式碼範例是將授權管理員整合至應用程式之 Web 服務組態檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="e018a-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="e018a-111">如需整合 ASP.NET 角色提供者與 WCF 應用程式的詳細資訊，請參閱[如何：搭配服務使用 ASP.NET 角色提供者](how-to-use-the-aspnet-role-provider-with-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e018a-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="e018a-112">如需有關搭配 ASP.NET 使用授權管理員的詳細資訊，請參閱[如何：搭配 ASP.NET 2.0 使用授權管理員（AzMan）](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="e018a-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e018a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e018a-113">See also</span></span>

- [<span data-ttu-id="e018a-114">HOW TO：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="e018a-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
