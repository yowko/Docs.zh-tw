---
title: HOW TO：使用 ASP.NET 授權管理員角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184804"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>HOW TO：使用 ASP.NET 授權管理員角色提供者搭配服務
當ASP.NET託管 Web 服務時，可以將授權管理員集成到應用程式中，以向服務提供授權。 授權管理員可讓應用程式開發人員定義個別作業，以便將作業分組，進而形成工作。 接著，系統管理員可以授權角色來執行特定工作或個別作業。 授權管理員會以 Microsoft Management Console (MMC) 嵌入式管理單元的形式提供系統管理工具，以管理角色、工作、作業和使用者。 系統管理員會在 XML 檔案、Active Directory 或「Active Directory 應用程式模式」(ADAM) 存放區中設定授權管理員原則存放區。  
  
 授權管理員通過為託管 Web 服務ASP.NET應用程式佈建授權管理員ASP.NET角色提供程式集成到應用程式中。 與其他ASP.NET角色提供程式一樣，授權管理員ASP.NET角色提供程式使用<>`providers`元素進行配置。  
  
 下列程式碼範例是將授權管理員整合至應用程式之 Web 服務組態檔的一部分。  
  
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
  
 有關將ASP.NET角色提供程式與 WCF 應用程式集成的詳細資訊，請參閱[：將ASP.NET角色提供程式與服務一起](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)使用。 有關將授權管理員與ASP.NET一起使用的詳細資訊，請參閱[：將授權管理員 （AzMan） 與 2.0 ASP.NET 。](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
