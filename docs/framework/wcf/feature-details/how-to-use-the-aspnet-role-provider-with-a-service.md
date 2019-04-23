---
title: HOW TO：使用 ASP.NET 角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 8f3fadc60645ef81d2683c63fda0ddd5bf24c982
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301135"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>HOW TO：使用 ASP.NET 角色提供者搭配服務
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 角色提供者 (以及 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者) 這項功能可讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開發人員建立網站，以允許使用者在網站中建立帳戶，並允許對使用者指派角色做為授權用途。 任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。 這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。 相反的，任何使用者只要提供認證 (使用者名稱/密碼組合) 就可以使用該網站與其服務。  
  
 範例應用程式，請參閱[Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。 如需詳細資訊[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]成員資格提供者功能，請參閱[How to:使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。  
  
 角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。 Windows Communication Foundation (WCF) 開發人員可以利用這些功能，基於安全性考量。 當整合到 WCF 應用程式，使用者必須提供 WCF 用戶端應用程式的使用者名稱/密碼組合。 若要啟用 WCF 使用的資料庫，您必須建立的執行個體<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>類別中，將其<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>屬性設<xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，並將執行個體新增至行為集合<xref:System.ServiceModel.ServiceHost>裝載服務。  
  
### <a name="to-configure-the-role-provider"></a>若要設定角色提供者  
  
1. 在 Web.config 檔案中，在 <`system.web`> 項目，新增 <`roleManager`> 項目並將其`enabled`屬性設定為`true`。  
  
2. 將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。  
  
3. 為子系 <`roleManager`> 元素中，新增 <`providers`> 項目。  
  
4. 為子系 <`providers`> 項目，新增 <`add`> 項目具有下列屬性設定為適當的值： `name`， `type`， `connectionStringName`，和`applicationName`，如下列範例所示。  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>若要設定服務使用角色提供者  
  
1. 在 Web.config 檔案中，加入[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目。  
  
2. 新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目 <`system.ServiceModel`> 項目。  
  
3. 新增[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)至 <`behaviors`> 項目。  
  
4. 新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)項目並將`name`屬性設為適當的值。  
  
5. 新增[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)至 <`behavior`> 項目。  
  
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
  
## <a name="see-also"></a>另請參閱

- [成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [如何：使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
