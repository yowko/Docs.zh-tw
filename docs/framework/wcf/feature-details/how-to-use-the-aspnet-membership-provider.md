---
title: "HOW TO：使用 ASP.NET 成員資格提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF 及 ASP.NET"
  - "WCF, 授權"
  - "WCF, 安全性"
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# HOW TO：使用 ASP.NET 成員資格提供者
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者是能夠讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 程式開發人員建立網站的功能，而網站可以讓使用者建立專屬的使用者名稱和密碼組合。任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。相反的，任何使用者只要提供認證 \(使用者名稱\/密碼組合\) 都可以使用該網站與其服務。  
  
 如需範例應用程式，請參閱[成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。如需有關使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 角色提供者功能的資訊，請參閱 [HOW TO：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。  
  
 成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。這個功能也包含對忘記密碼的任何使用者提示問題的方法。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 程式開發人員可以針對安全性目的利用這些功能。當整合至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式時，使用者必須將使用者名稱\/密碼組合提供給 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式。若要將資料傳輸至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，請使用支援使用者名稱\/密碼認證的繫結，例如 <xref:System.ServiceModel.WSHttpBinding> \(在組態中，[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)\) 並且將用戶端認證類型設定為 `UserName`。在服務時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性會根據使用者名稱與密碼驗證使用者，並且也會指派 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 角色指定的角色。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不提供將使用者名稱\/密碼組合或其他使用者資訊填入資料庫的方法。  
  
### 設定成員資格提供者  
  
1.  在 Web.config 檔的 \<`system.web`\> 項目中，建立 \<`membership`\> 項目。  
  
2.  在 `<membership>``<providers> 項目之下建立`  項目。  
  
3.  加入 `<clear />` 項目當做 \<`providers`\> 項目的子系，以清除提供者的集合。  
  
4.  在 `<clear />` 項目中，使用下列已設定適當值的屬性建立 \<`add`\> 項目：`name`、`type`、`connectionStringName`、`applicationName`、`enablePasswordRetrieval`、`enablePasswordReset`、`requiresQuestionAndAnswer`、`requiresUniqueEmail` 以及 `passwordFormat`。`name` 屬性稍後會用來當做組態檔中的值。下列範例將它設定為 `SqlMembershipProvider`。  
  
     下列範例顯示其組態區段。  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### 設定安全性服務接受使用者名稱\/密碼組合  
  
1.  在組態檔的 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 項目中新增 [\<繫結\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 項目。  
  
2.  將 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 加入至繫結區段。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結項目的詳細資訊，請參閱 [HOW TO：指定組態中的服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
3.  將 `<security>` 項目的 `mode` 屬性設定為 `Message`。  
  
4.  將 \<`message`\> 項目的 `clientCredentialType` 屬性設定為 `UserName`。這會指定使用者名稱\/密碼組將用來當做用戶端的認證。  
  
     下列程式碼範例顯示繫結的組態程式碼。  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### 設定服務以使用成員資格提供者  
  
1.  新增 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 項目當做 `<system.serviceModel>` 項目的子系。  
  
2.  將 [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) 新增至 \<`behaviors`\> 項目。  
  
3.  新增 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)，然後將 `name` 屬性設定為適當的值。  
  
4.  將 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) 新增至 \<`behavior`\> 項目中。  
  
5.  將 [\<userNameAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) 新增至 `<serviceCredentials>` 項目中。  
  
6.  將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。  
  
    > [!IMPORTANT]
    >  如果沒有設定 `userNamePasswordValidationMode` 值，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 Windows 驗證而不是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者。  
  
7.  將 `membershipProviderName` 屬性設定為提供者的名稱 \(在此主題的第一個程序中新增提供者時已指定\)。下列範例顯示目前的 `<serviceCredentials>` 片段。  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
  
    ```  
  
## 範例  
 下列程式碼顯示了使用 ASP 成員資格功能之服務的組態。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
  
```  
  
## 請參閱  
 [HOW TO：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)