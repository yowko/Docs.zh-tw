---
title: HOW TO：使用 ASP.NET 角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595293"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>HOW TO：使用 ASP.NET 角色提供者搭配服務

ASP.NET 角色提供者（結合 ASP.NET 成員資格提供者）是一項功能，可讓 ASP.NET 開發人員建立網站，讓使用者可以建立具有網站的帳戶，並獲指派角色供授權之用。 任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。 這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。 相反地，任何提供其認證（使用者名稱/密碼組合）的使用者都可以使用該網站與其服務。  
  
如需範例應用程式，請參閱[成員資格和角色提供者](../samples/membership-and-role-provider.md)。 如需 ASP.NET 成員資格提供者功能的詳細資訊，請參閱[如何：使用 ASP.NET 成員資格提供者](how-to-use-the-aspnet-membership-provider.md)。  
  
角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。 Windows Communication Foundation （WCF）開發人員可以基於安全性目的，利用這些功能。 當整合到 WCF 應用程式時，使用者必須提供使用者名稱/密碼組合給 WCF 用戶端應用程式。 若要讓 WCF 能夠使用資料庫，您必須建立類別的實例 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ，將其屬性設定 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> ，並將實例加入至裝載服務之的行為集合 <xref:System.ServiceModel.ServiceHost> 。  
  
## <a name="configure-the-role-provider"></a>設定角色提供者  
  
1. 在 web.config 檔案中，< `system.web` > 元素底下，新增 < > 專案， `roleManager` 並將其 `enabled` 屬性設定為 `true` 。  
  
2. 將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。  
  
3. 做為 <> 專案的子系 `roleManager` ，請新增 <`providers`> 元素。  
  
4. 做為 <> 元素的子系 `providers` ，請新增 <> 專案，並將 `add` 下列屬性設定為適當的值： `name` 、 `type` 、 `connectionStringName` 和 `applicationName` ，如下列範例所示。  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a>將服務設定為使用角色提供者  
  
1. 在 web.config 檔案中，新增 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 元素。  
  
2. 將 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素加入至 <`system.ServiceModel`> 專案。  
  
3. 將加入 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至 <`behaviors`> 元素。  
  
4. 新增 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 元素，並將 `name` 屬性設定為適當的值。  
  
5. 將加入 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 至 <`behavior`> 元素。  
  
6. 將 `principalPermissionMode` 屬性設定為 `UseAspNetRoles`。  
  
7. 將 `roleProviderName` 屬性設定為 `SqlRoleProvider`。 下列範例將說明組態片段。  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a>請參閱

- [成員資格和角色提供者](../samples/membership-and-role-provider.md)
- [如何：使用 ASP.NET 成員資格提供者](how-to-use-the-aspnet-membership-provider.md)
