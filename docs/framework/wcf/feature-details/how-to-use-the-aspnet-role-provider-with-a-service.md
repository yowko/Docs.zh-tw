---
title: "HOW TO：使用 ASP.NET 角色提供者搭配服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：使用 ASP.NET 角色提供者搭配服務
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 角色提供者 \(以及 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者\) 這項功能可讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開發人員建立網站，以允許使用者在網站中建立帳戶，並允許對使用者指派角色做為授權用途。任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。相反的，任何使用者只要提供認證 \(使用者名稱\/密碼組合\) 就可以使用該網站與其服務。  
  
 如需範例應用程式，請參閱[成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者功能的詳細資訊，請參閱 [HOW TO：使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。  
  
 角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 程式開發人員可以針對安全性目的利用這些功能。當整合至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式時，使用者必須將使用者名稱\/密碼組合提供給 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式。若要啟用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來使用資料庫，您必須建立 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 類別的執行個體，並將其 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 屬性設為 <xref:System.ServiceModel.Description.PrincipalPermissionMode>，然後將行為集合的執行個體新增至裝載服務的 <xref:System.ServiceModel.ServiceHost>。  
  
### 若要設定角色提供者  
  
1.  在 Web.config 檔的 \<`system.web`\> 項目底下，新增 \<`roleManager`\> 項目並將其 `enabled` 屬性設為 `true`。  
  
2.  將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。  
  
3.  新增 \<`providers`\> 項目做為 \<`roleManager`\> 項目的子系。  
  
4.  新增 \<`add`\> 項目 \(其中並將 `name`、`type`、`connectionStringName`，和 `applicationName` 屬性設為適當值，如下列範例所示\)，做為 \<`providers`\> 項目的子系。  
  
    ```  
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
  
### 若要設定服務使用角色提供者  
  
1.  在 Web.config 檔案中，新增 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 項目。  
  
2.  將 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 項目加入至 \<`system.ServiceModel`\> 項目。  
  
3.  將 [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) 新增至 \<`behaviors`\> 項目。  
  
4.  新增 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 項目，並將 `name` 屬性設為適當值。  
  
5.  將 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)加入至 \<`behavior`\> 項目。  
  
6.  將 `principalPermissionMode` 屬性設定為 `UseAspNetRoles`。  
  
7.  將 `roleProviderName` 屬性設定為 `SqlRoleProvider`。下列範例將說明組態片段。  
  
    ```  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## 請參閱  
 [成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)   
 [HOW TO：使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)