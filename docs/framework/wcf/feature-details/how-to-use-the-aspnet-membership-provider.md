---
title: HOW TO：使用 ASP.NET 成員資格提供者
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19fb83d21c77f3206c314a2e6c40562fcb75f151
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>HOW TO：使用 ASP.NET 成員資格提供者
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者是能夠讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 程式開發人員建立網站的功能，而網站可以讓使用者建立專屬的使用者名稱和密碼組合。 任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。 這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。 相反的，任何使用者只要提供認證 (使用者名稱/密碼組合) 都可以使用該網站與其服務。  
  
 範例應用程式，請參閱[成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。 如需使用[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]角色提供者功能，請參閱[How to： 使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。  
  
 成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。 這個功能也包含對忘記密碼的任何使用者提示問題的方法。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 程式開發人員可以針對安全性目的利用這些功能。 當整合至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式時，使用者必須將使用者名稱/密碼組合提供給 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式。 若要將資料傳送到[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務，請使用繫結，支援使用者名稱/密碼認證，例如<xref:System.ServiceModel.WSHttpBinding>(在組態中， [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) 並設定用戶端認證若要輸入`UserName`。 在服務時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性會根據使用者名稱與密碼驗證使用者，並且也會指派 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 角色指定的角色。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不提供將使用者名稱/密碼組合或其他使用者資訊填入資料庫的方法。  
  
### <a name="to-configure-the-membership-provider"></a>設定成員資格提供者  
  
1.  在 Web.config 檔案中，在 <`system.web`> 項目，建立 <`membership`> 項目。  
  
2.  在 `<membership>` 項目之下建立`<providers>`項目。  
  
3.  做為子項 <`providers`> 項目，加入`<clear />`排清的提供者集合的項目。  
  
4.  在下`<clear />`項目，建立 <`add`> 具有下列屬性項目設定為適當值： `name`， `type`， `connectionStringName`， `applicationName`， `enablePasswordRetrieval`， `enablePasswordReset`， `requiresQuestionAndAnswer``requiresUniqueEmail`，和`passwordFormat`。 `name` 屬性稍後會用來當做組態檔中的值。 下列範例將它設定為 `SqlMembershipProvider`。  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>若要設定安全性服務接受使用者名稱/密碼組合  
  
1.  在組態檔中，在[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，加入[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目。  
  
2.  新增[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)的繫結 」 一節。 如需有關建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]繫結項目，請參閱[How to： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
3.  將 `mode` 項目的 `<security>` 屬性設定為 `Message`。  
  
4.  設定`clientCredentialType`屬性 <`message`> 項目`UserName`。 這會指定使用者名稱/密碼組將用來當做用戶端的認證。  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>設定服務以使用成員資格提供者  
  
1.  做為子項`<system.serviceModel>`項目，加入[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目  
  
2.  新增[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)至 <`behaviors`> 項目。  
  
3.  新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)並設定`name`屬性設為適當值。  
  
4.  新增[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)至 <`behavior`> 項目。  
  
5.  新增[ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)至`<serviceCredentials>`項目。  
  
6.  將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。  
  
    > [!IMPORTANT]
    >  如果沒有設定 `userNamePasswordValidationMode` 值，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 Windows 驗證而不是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者。  
  
7.  將 `membershipProviderName` 屬性設定為提供者的名稱 (在此主題的第一個程序中新增提供者時已指定)。 下列範例顯示目前的 `<serviceCredentials>` 片段。  
  
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
  
## <a name="example"></a>範例  
 下列程式碼顯示了使用 ASP 成員資格功能之服務的組態。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱  
 [如何：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
