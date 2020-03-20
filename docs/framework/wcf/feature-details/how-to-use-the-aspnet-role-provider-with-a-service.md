---
title: HOW TO：使用 ASP.NET 角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184762"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>HOW TO：使用 ASP.NET 角色提供者搭配服務

ASP.NET角色提供程式（與ASP.NET成員提供程式結合）是一項功能，它使ASP.NET開發人員能夠創建網站，允許使用者使用網站創建帳戶，並為授權目的分配角色。 任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。 這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。 相反，任何提供其憑據（使用者名/密碼組合）的使用者都可以使用該網站及其服務。  
  
有關應用程式範例，請參閱[成員資格和角色提供程式](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。 有關ASP.NET成員資格提供程式功能的詳細資訊，請參閱[：使用ASP.NET成員資格提供程式](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。  
  
角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。 出於安全目的，Windows 通信基礎 （WCF） 開發人員可以利用這些功能。 集成到 WCF 應用程式時，使用者必須向 WCF 用戶端應用程式提供使用者名和密碼組合。 要使 WCF 能夠使用資料庫，必須<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>創建類的實例，將其<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>屬性設置為<xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，並將實例添加到承載服務<xref:System.ServiceModel.ServiceHost>的行為集合中。  
  
## <a name="configure-the-role-provider"></a>配置角色提供程式  
  
1. 在 Web.config 檔中`system.web`，在<>元素下，添加<>`roleManager`元素並將其`enabled`屬性設置為 。 `true`  
  
2. 將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。  
  
3. 作為<>`roleManager`元素的子項目，添加<>`providers`元素。  
  
4. `providers`作為<>元素的子項目，添加一個<>`add`元素，其中將以下屬性設置為適當的值： `name` `type`、`connectionStringName`和`applicationName`， 如以下示例所示。  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>將服務配置為使用角色提供程式  
  
1. 在 Web.config 檔中，添加[\<一個系統.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)元素。  
  
2. 將[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)元素添加到<>`system.ServiceModel`元素。  
  
3. 向`behaviors`[\<<>元素添加服務行為>。](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)  
  
4. >元素添加[\<行為](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)並將`name`屬性設置為適當的值。  
  
5. 將[\<服務授權>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)添加到<>`behavior`元素。  
  
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
