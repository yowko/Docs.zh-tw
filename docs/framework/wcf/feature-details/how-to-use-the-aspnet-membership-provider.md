---
title: HOW TO：使用 ASP.NET 成員資格提供者
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 840e4a5d365f2adbaf335c1061a580665a39824d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595319"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>HOW TO：使用 ASP.NET 成員資格提供者

ASP.NET 成員資格提供者是一項功能，可讓 ASP.NET 開發人員建立網站，讓使用者能夠建立唯一的使用者名稱和密碼組合。 任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。 這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。 相反地，任何提供其認證（使用者名稱/密碼組合）的使用者都可以使用該網站與其服務。

如需範例應用程式，請參閱[成員資格和角色提供者](../samples/membership-and-role-provider.md)。 如需使用 ASP.NET 角色提供者功能的詳細資訊，請參閱[如何：搭配服務使用 ASP.NET 角色提供者](how-to-use-the-aspnet-role-provider-with-a-service.md)。

成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。 這個功能也包含對忘記密碼的任何使用者提示問題的方法。

Windows Communication Foundation （WCF）開發人員可以基於安全性目的，利用這些功能。 當整合到 WCF 應用程式時，使用者必須提供使用者名稱/密碼組合給 WCF 用戶端應用程式。 若要將資料傳送至 WCF 服務，請使用支援使用者名稱/密碼認證的系結，例如 <xref:System.ServiceModel.WSHttpBinding> （在設定中）， [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 並將用戶端認證類型設定為 `UserName` 。 在服務上，WCF 安全性會根據使用者名稱和密碼來驗證使用者，也會指派 ASP.NET 角色所指定的角色。

> [!NOTE]
> WCF 不會提供以使用者名稱/密碼組合或其他使用者資訊填入資料庫的方法。

### <a name="to-configure-the-membership-provider"></a>設定成員資格提供者

1. 在 web.config 檔案中，< `system.web` > 元素底下，建立 < `membership` > 專案。

2. 在 `<membership>` 項目。

3. 做為 <> 專案的子系 `providers` ，請加入 `<clear />` 元素以排清提供者的集合。

4. 在 `<clear />` 元素底下，建立 <`add`> 元素，並將下列屬性設定為適當的值： `name` 、 `type` 、 `connectionStringName` 、、、、、 `applicationName` `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `requiresUniqueEmail` 和 `passwordFormat` 。 `name` 屬性稍後會用來當做組態檔中的值。 下列範例將它設定為 `SqlMembershipProvider`。

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

1. 在設定檔中的元素底下 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ，新增 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 元素。

2. 將加入 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 至系結區段。 如需建立 WCF 繫結項目的詳細資訊，請參閱 how [to：在 Configuration 中指定服務](../how-to-specify-a-service-binding-in-configuration.md)系結。

3. 將 `mode` 項目的 `<security>` 屬性設定為 `Message`。

4. 將 `clientCredentialType` <> 元素的屬性設定 `message` 為 `UserName` 。 這會指定使用者名稱/密碼組將用來當做用戶端的認證。

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

1. `<system.serviceModel>`加入元素做為專案的子系 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)

2. 將加入 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至 <`behaviors`> 元素。

3. 加入 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ，並將 `name` 屬性設定為適當的值。

4. 將加入 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 至 <`behavior`> 元素。

5. 將加入 [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) 至 `<serviceCredentials>` 元素。

6. 將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。

    > [!IMPORTANT]
    > 如果 `userNamePasswordValidationMode` 未設定此值，WCF 會使用 Windows 驗證，而不是 ASP.NET 成員資格提供者。

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

## <a name="see-also"></a>請參閱

- [HOW TO：使用 ASP.NET 角色提供者搭配服務](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [成員資格和角色提供者](../samples/membership-and-role-provider.md)
