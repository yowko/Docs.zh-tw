---
title: HOW TO：使用 ASP.NET 成員資格提供者
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184800"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>HOW TO：使用 ASP.NET 成員資格提供者

ASP.NET成員資格提供程式是一項功能，使ASP.NET開發人員能夠創建允許使用者創建唯一使用者名和密碼組合的網站。 任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。 這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。 相反，任何提供其憑據（使用者名/密碼組合）的使用者都可以使用該網站及其服務。

有關應用程式範例，請參閱[成員資格和角色提供程式](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。 有關使用ASP.NET角色提供程式功能的資訊，請參閱[：將ASP.NET角色提供程式與服務一起使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。

成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。 這個功能也包含對忘記密碼的任何使用者提示問題的方法。

出於安全目的，Windows 通信基礎 （WCF） 開發人員可以利用這些功能。 集成到 WCF 應用程式時，使用者必須向 WCF 用戶端應用程式提供使用者名和密碼組合。 要將資料傳輸到 WCF 服務，請使用支援使用者名/密碼憑據的綁定，例如<xref:System.ServiceModel.WSHttpBinding>（在配置中[\<，wsHttpBinding>），](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)並將用戶端憑據類型設置為`UserName`。 在服務上，WCF 安全根據使用者名和密碼對使用者進行身份驗證，並分配ASP.NET角色指定的角色。

> [!NOTE]
> WCF 不提供使用使用者名/密碼組合或其他使用者資訊填充資料庫的方法。

### <a name="to-configure-the-membership-provider"></a>設定成員資格提供者

1. 在 Web.config 檔中，在<>`system.web`元素下，創建<>`membership`元素。

2. 在 `<membership>` 項目。

3. 作為<>`providers`元素的子項目，添加一個`<clear />`元素來刷新提供程式的集合。

4. 在`<clear />`元素下，創建一`add`個<>元素，其屬性設置為適當的值： `name` `type`、 `connectionStringName` `applicationName`、 `enablePasswordRetrieval` `enablePasswordReset`、 `requiresQuestionAndAnswer` `requiresUniqueEmail`、 `passwordFormat`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 `name` 屬性稍後會用來當做組態檔中的值。 下列範例將它設定為 `SqlMembershipProvider`。

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

1. 在設定檔中，在[\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)元素下，添加[\<綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)元素。

2. 將[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)添加到綁定部分。 有關創建 WCF 繫結元素的詳細資訊，請參閱[如何：在配置 中指定服務綁定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。

3. 將 `mode` 項目的 `<security>` 屬性設定為 `Message`。

4. 將`clientCredentialType`<>`message`元素的屬性設置為`UserName`。 這會指定使用者名稱/密碼組將用來當做用戶端的認證。

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

1. 作為元素的子項目`<system.serviceModel>`，添加[\<>元素的行為](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

2. 向`behaviors`[\<<>元素添加服務行為>。](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)

3. >添加[\<行為](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)並將`name`屬性設置為適當的值。

4. 將[\<服務憑據>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)添加到<>`behavior`元素。

5. 向`<serviceCredentials>`元素添加[\<使用者名身份驗證>。](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)

6. 將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。

    > [!IMPORTANT]
    > 如果未設置`userNamePasswordValidationMode`該值，WCF 將使用 Windows 身份驗證而不是ASP.NET成員資格提供程式。

7. 將 `membershipProviderName` 屬性設定為提供者的名稱 (在此主題的第一個程序中新增提供者時已指定)。 下列範例顯示目前的 `<serviceCredentials>` 片段。

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

- [HOW TO：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
