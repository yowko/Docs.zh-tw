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
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="880db-102">HOW TO：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="880db-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="880db-103">ASP.NET成員資格提供程式是一項功能，使ASP.NET開發人員能夠創建允許使用者創建唯一使用者名和密碼組合的網站。</span><span class="sxs-lookup"><span data-stu-id="880db-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="880db-104">任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="880db-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="880db-105">這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。</span><span class="sxs-lookup"><span data-stu-id="880db-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="880db-106">相反，任何提供其憑據（使用者名/密碼組合）的使用者都可以使用該網站及其服務。</span><span class="sxs-lookup"><span data-stu-id="880db-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="880db-107">有關應用程式範例，請參閱[成員資格和角色提供程式](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="880db-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="880db-108">有關使用ASP.NET角色提供程式功能的資訊，請參閱[：將ASP.NET角色提供程式與服務一起使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="880db-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="880db-109">成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="880db-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="880db-110">這個功能也包含對忘記密碼的任何使用者提示問題的方法。</span><span class="sxs-lookup"><span data-stu-id="880db-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="880db-111">出於安全目的，Windows 通信基礎 （WCF） 開發人員可以利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="880db-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="880db-112">集成到 WCF 應用程式時，使用者必須向 WCF 用戶端應用程式提供使用者名和密碼組合。</span><span class="sxs-lookup"><span data-stu-id="880db-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="880db-113">要將資料傳輸到 WCF 服務，請使用支援使用者名/密碼憑據的綁定，例如<xref:System.ServiceModel.WSHttpBinding>（在配置中[\<，wsHttpBinding>），](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)並將用戶端憑據類型設置為`UserName`。</span><span class="sxs-lookup"><span data-stu-id="880db-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="880db-114">在服務上，WCF 安全根據使用者名和密碼對使用者進行身份驗證，並分配ASP.NET角色指定的角色。</span><span class="sxs-lookup"><span data-stu-id="880db-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="880db-115">WCF 不提供使用使用者名/密碼組合或其他使用者資訊填充資料庫的方法。</span><span class="sxs-lookup"><span data-stu-id="880db-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="880db-116">設定成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="880db-116">To configure the membership provider</span></span>

1. <span data-ttu-id="880db-117">在 Web.config 檔中，在<>`system.web`元素下，創建<>`membership`元素。</span><span class="sxs-lookup"><span data-stu-id="880db-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="880db-118">在 `<membership>` 項目。</span><span class="sxs-lookup"><span data-stu-id="880db-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="880db-119">作為<>`providers`元素的子項目，添加一個`<clear />`元素來刷新提供程式的集合。</span><span class="sxs-lookup"><span data-stu-id="880db-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="880db-120">在`<clear />`元素下，創建一`add`個<>元素，其屬性設置為適當的值： `name` `type`、 `connectionStringName` `applicationName`、 `enablePasswordRetrieval` `enablePasswordReset`、 `requiresQuestionAndAnswer` `requiresUniqueEmail`、 `passwordFormat`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、</span><span class="sxs-lookup"><span data-stu-id="880db-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="880db-121">`name` 屬性稍後會用來當做組態檔中的值。</span><span class="sxs-lookup"><span data-stu-id="880db-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="880db-122">下列範例將它設定為 `SqlMembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="880db-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="880db-123">下列範例顯示其組態區段。</span><span class="sxs-lookup"><span data-stu-id="880db-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="880db-124">若要設定安全性服務接受使用者名稱/密碼組合</span><span class="sxs-lookup"><span data-stu-id="880db-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="880db-125">在設定檔中，在[\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)元素下，添加[\<綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)元素。</span><span class="sxs-lookup"><span data-stu-id="880db-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="880db-126">將[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)添加到綁定部分。</span><span class="sxs-lookup"><span data-stu-id="880db-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="880db-127">有關創建 WCF 繫結元素的詳細資訊，請參閱[如何：在配置 中指定服務綁定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="880db-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="880db-128">將 `mode` 項目的 `<security>` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="880db-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="880db-129">將`clientCredentialType`<>`message`元素的屬性設置為`UserName`。</span><span class="sxs-lookup"><span data-stu-id="880db-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="880db-130">這會指定使用者名稱/密碼組將用來當做用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="880db-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="880db-131">下列程式碼範例顯示繫結的組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="880db-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="880db-132">設定服務以使用成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="880db-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="880db-133">作為元素的子項目`<system.serviceModel>`，添加[\<>元素的行為](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="880db-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="880db-134">向`behaviors`[\<<>元素添加服務行為>。](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="880db-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="880db-135">>添加[\<行為](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)並將`name`屬性設置為適當的值。</span><span class="sxs-lookup"><span data-stu-id="880db-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="880db-136">將[\<服務憑據>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)添加到<>`behavior`元素。</span><span class="sxs-lookup"><span data-stu-id="880db-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="880db-137">向`<serviceCredentials>`元素添加[\<使用者名身份驗證>。](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)</span><span class="sxs-lookup"><span data-stu-id="880db-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="880db-138">將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="880db-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="880db-139">如果未設置`userNamePasswordValidationMode`該值，WCF 將使用 Windows 身份驗證而不是ASP.NET成員資格提供程式。</span><span class="sxs-lookup"><span data-stu-id="880db-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="880db-140">將 `membershipProviderName` 屬性設定為提供者的名稱 (在此主題的第一個程序中新增提供者時已指定)。</span><span class="sxs-lookup"><span data-stu-id="880db-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="880db-141">下列範例顯示目前的 `<serviceCredentials>` 片段。</span><span class="sxs-lookup"><span data-stu-id="880db-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="880db-142">範例</span><span class="sxs-lookup"><span data-stu-id="880db-142">Example</span></span>

<span data-ttu-id="880db-143">下列程式碼顯示了使用 ASP 成員資格功能之服務的組態。</span><span class="sxs-lookup"><span data-stu-id="880db-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="880db-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="880db-144">See also</span></span>

- [<span data-ttu-id="880db-145">HOW TO：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="880db-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="880db-146">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="880db-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
