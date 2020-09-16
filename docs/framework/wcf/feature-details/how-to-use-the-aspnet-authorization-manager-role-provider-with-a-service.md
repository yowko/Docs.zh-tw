---
title: 作法：使用 ASP.NET 授權管理員角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 4a92c9db000b703f4fdab7c34e5359de74b0228d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545600"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>作法：使用 ASP.NET 授權管理員角色提供者搭配服務
當 ASP.NET 裝載 Web 服務時，您可以將授權管理員整合至應用程式，以提供服務的授權。 授權管理員可讓應用程式開發人員定義個別作業，以便將作業分組，進而形成工作。 接著，系統管理員可以授權角色來執行特定工作或個別作業。 授權管理員會以 Microsoft Management Console (MMC) 嵌入式管理單元的形式提供系統管理工具，以管理角色、工作、作業和使用者。 系統管理員會在 XML 檔案、Active Directory 或「Active Directory 應用程式模式」(ADAM) 存放區中設定授權管理員原則存放區。  
  
 授權管理員已整合至應用程式中，方法是為裝載 Web 服務的 ASP.NET 應用程式設定授權管理員 ASP.NET 角色提供者。 如同其他 ASP.NET 角色提供者，授權管理員 ASP.NET 角色提供者是使用 <> 專案來設定 `providers` 。  
  
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
  
 如需整合 ASP.NET 角色提供者與 WCF 應用程式的詳細資訊，請參閱 [如何：使用 ASP.NET 角色提供者搭配服務](how-to-use-the-aspnet-role-provider-with-a-service.md)。 如需搭配使用授權管理員與 ASP.NET 的詳細資訊，請參閱 [如何：使用授權管理員 (AzMan) 與 ASP.NET 2.0](/previous-versions/msp-n-p/ff649313(v=pandp.10))。  
  
## <a name="see-also"></a>另請參閱

- [作法：使用 ASP.NET 角色提供者搭配服務](how-to-use-the-aspnet-role-provider-with-a-service.md)
