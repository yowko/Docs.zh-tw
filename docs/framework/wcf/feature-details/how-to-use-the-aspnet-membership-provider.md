---
title: HOW TO：使用 ASP.NET 成員資格提供者
description: 瞭解 ASP.NET 成員資格提供者如何支援網站，讓使用者建立使用者名稱和密碼以進行存取，而不需要 Windows 網域帳戶。
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246723"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="6d7b1-103">HOW TO：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="6d7b1-103">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="6d7b1-104">ASP.NET 成員資格提供者是一項功能，可讓 ASP.NET 開發人員建立網站，讓使用者能夠建立唯一的使用者名稱和密碼組合。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-104">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="6d7b1-105">任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-105">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="6d7b1-106">這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="6d7b1-107">相反地，任何提供其認證（使用者名稱/密碼組合）的使用者都可以使用該網站與其服務。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-107">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="6d7b1-108">如需範例應用程式，請參閱[成員資格和角色提供者](../samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="6d7b1-109">如需使用 ASP.NET 角色提供者功能的詳細資訊，請參閱[如何：搭配服務使用 ASP.NET 角色提供者](how-to-use-the-aspnet-role-provider-with-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-109">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="6d7b1-110">成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-110">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="6d7b1-111">這個功能也包含對忘記密碼的任何使用者提示問題的方法。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-111">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="6d7b1-112">Windows Communication Foundation （WCF）開發人員可以基於安全性目的，利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-112">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="6d7b1-113">當整合到 WCF 應用程式時，使用者必須提供使用者名稱/密碼組合給 WCF 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-113">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="6d7b1-114">若要將資料傳送至 WCF 服務，請使用支援使用者名稱/密碼認證的系結，例如 <xref:System.ServiceModel.WSHttpBinding> （在設定中）， [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 並將用戶端認證類型設定為 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-114">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="6d7b1-115">在服務上，WCF 安全性會根據使用者名稱和密碼來驗證使用者，也會指派 ASP.NET 角色所指定的角色。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-115">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="6d7b1-116">WCF 不會提供以使用者名稱/密碼組合或其他使用者資訊填入資料庫的方法。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-116">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="6d7b1-117">設定成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="6d7b1-117">To configure the membership provider</span></span>

1. <span data-ttu-id="6d7b1-118">在 Web.config 檔案中，<> 專案底下 `system.web` ，建立 <`membership`> 元素。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-118">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="6d7b1-119">在 `<membership>` 項目。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-119">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="6d7b1-120">做為 <> 專案的子系 `providers` ，請加入 `<clear />` 元素以排清提供者的集合。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-120">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="6d7b1-121">在 `<clear />` 元素底下，建立 <`add`> 元素，並將下列屬性設定為適當的值： `name` 、 `type` 、 `connectionStringName` 、、、、、 `applicationName` `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `requiresUniqueEmail` 和 `passwordFormat` 。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-121">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="6d7b1-122">`name` 屬性稍後會用來當做組態檔中的值。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-122">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="6d7b1-123">下列範例將它設定為 `SqlMembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-123">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="6d7b1-124">下列範例顯示其組態區段。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-124">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="6d7b1-125">若要設定安全性服務接受使用者名稱/密碼組合</span><span class="sxs-lookup"><span data-stu-id="6d7b1-125">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="6d7b1-126">在設定檔中的元素底下 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ，新增 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-126">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="6d7b1-127">將加入 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 至系結區段。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-127">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="6d7b1-128">如需建立 WCF 繫結項目的詳細資訊，請參閱 how [to：在 Configuration 中指定服務](../how-to-specify-a-service-binding-in-configuration.md)系結。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-128">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="6d7b1-129">將 `mode` 項目的 `<security>` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-129">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="6d7b1-130">將 `clientCredentialType` <> 元素的屬性設定 `message` 為 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-130">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="6d7b1-131">這會指定使用者名稱/密碼組將用來當做用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-131">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="6d7b1-132">下列程式碼範例顯示繫結的組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-132">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="6d7b1-133">設定服務以使用成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="6d7b1-133">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="6d7b1-134">`<system.serviceModel>`加入元素做為專案的子系 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6d7b1-134">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="6d7b1-135">將加入 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至 <`behaviors`> 元素。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-135">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="6d7b1-136">加入 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ，並將 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-136">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="6d7b1-137">將加入 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 至 <`behavior`> 元素。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-137">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="6d7b1-138">將加入 [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) 至 `<serviceCredentials>` 元素。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-138">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="6d7b1-139">將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-139">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6d7b1-140">如果 `userNamePasswordValidationMode` 未設定此值，WCF 會使用 Windows 驗證，而不是 ASP.NET 成員資格提供者。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-140">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="6d7b1-141">將 `membershipProviderName` 屬性設定為提供者的名稱 (在此主題的第一個程序中新增提供者時已指定)。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-141">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="6d7b1-142">下列範例顯示目前的 `<serviceCredentials>` 片段。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-142">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="6d7b1-143">範例</span><span class="sxs-lookup"><span data-stu-id="6d7b1-143">Example</span></span>

<span data-ttu-id="6d7b1-144">下列程式碼顯示了使用 ASP 成員資格功能之服務的組態。</span><span class="sxs-lookup"><span data-stu-id="6d7b1-144">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6d7b1-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d7b1-145">See also</span></span>

- [<span data-ttu-id="6d7b1-146">HOW TO：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="6d7b1-146">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="6d7b1-147">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="6d7b1-147">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
