---
title: HOW TO：使用 ASP.NET 授權管理員角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880192"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>作法：使用 ASP.NET 授權管理員角色提供者搭配服務
當 ASP.NET 裝載的 Web 服務時，您可以授權管理員整合來提供授權給服務的應用程式。 授權管理員可讓應用程式開發人員定義個別作業，以便將作業分組，進而形成工作。 接著，系統管理員可以授權角色來執行特定工作或個別作業。 授權管理員會以 Microsoft Management Console (MMC) 嵌入式管理單元的形式提供系統管理工具，以管理角色、工作、作業和使用者。 系統管理員會在 XML 檔案、Active Directory 或「Active Directory 應用程式模式」(ADAM) 存放區中設定授權管理員原則存放區。  
  
 藉由設定 ASP.NET 應用程式裝載 Web 服務的授權管理員 ASP.NET 角色提供者，授權管理員會整合到應用程式。 類似其他 ASP.NET 角色提供者，授權管理員 ASP.NET 角色提供者已設定使用 <`providers`> 項目。  
  
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
  
 如需有關如何整合 WCF 應用程式中的 ASP.NET 角色提供者的詳細資訊，請參閱[How to:使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。 如需搭配 ASP.NET 使用授權管理員的詳細資訊，請參閱[How to:使用 ASP.NET 2.0 使用授權管理員 (AzMan)](https://go.microsoft.com/fwlink/?LinkId=71303)。  
  
## <a name="see-also"></a>另請參閱

- [如何：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
