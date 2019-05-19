---
title: HOW TO：使用 ASP.NET 成員資格提供者
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 61324bbc5ea07dd19e23589bfc90f9ea44a6b331
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880191"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="5167d-102">作法：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="5167d-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="5167d-103">ASP.NET 成員資格提供者是一項功能，可讓 ASP.NET 開發人員建立網站，可讓使用者建立唯一的使用者名稱和密碼的組合。</span><span class="sxs-lookup"><span data-stu-id="5167d-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="5167d-104">任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="5167d-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="5167d-105">這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5167d-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="5167d-106">相反的，任何使用者只要提供認證 (使用者名稱/密碼組合) 都可以使用該網站與其服務。</span><span class="sxs-lookup"><span data-stu-id="5167d-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="5167d-107">範例應用程式，請參閱[Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="5167d-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="5167d-108">使用 ASP.NET 角色提供者功能的相關資訊，請參閱[How to:使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5167d-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="5167d-109">成員資格功能需要使用 SQL Server 資料庫儲存使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="5167d-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="5167d-110">這個功能也包含對忘記密碼的任何使用者提示問題的方法。</span><span class="sxs-lookup"><span data-stu-id="5167d-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="5167d-111">Windows Communication Foundation (WCF) 開發人員可以利用這些功能，基於安全性考量。</span><span class="sxs-lookup"><span data-stu-id="5167d-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="5167d-112">當整合至 WCF 應用程式，使用者必須提供 WCF 用戶端應用程式的使用者名稱/密碼組合。</span><span class="sxs-lookup"><span data-stu-id="5167d-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="5167d-113">若要將資料傳送至 WCF 服務，使用 支援的使用者名稱/密碼認證，例如繫結<xref:System.ServiceModel.WSHttpBinding>(在組態中， [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) 和用戶端認證類型設為`UserName`.</span><span class="sxs-lookup"><span data-stu-id="5167d-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="5167d-114">在服務上，WCF 安全性會驗證使用者的使用者名稱和密碼為基礎，並也會將 ASP.NET 角色所指定的角色指派。</span><span class="sxs-lookup"><span data-stu-id="5167d-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5167d-115">WCF 不提供方法來填入資料庫的使用者名稱/密碼組合或其他使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="5167d-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="5167d-116">設定成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="5167d-116">To configure the membership provider</span></span>  
  
1. <span data-ttu-id="5167d-117">在 Web.config 檔案中，在 <`system.web`> 項目，建立 <`membership`> 項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2. <span data-ttu-id="5167d-118">在 `<membership>`<providers> 項目之下建立`<providers>` 項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3. <span data-ttu-id="5167d-119">為子系 <`providers`> 元素中，新增`<clear />`排清的提供者集合的項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4. <span data-ttu-id="5167d-120">底下`<clear />`項目，建立 <`add`> 項目具有下列屬性設定為適當的值： `name`， `type`， `connectionStringName`， `applicationName`， `enablePasswordRetrieval`， `enablePasswordReset`， `requiresQuestionAndAnswer``requiresUniqueEmail`，和`passwordFormat`。</span><span class="sxs-lookup"><span data-stu-id="5167d-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="5167d-121">`name` 屬性稍後會用來當做組態檔中的值。</span><span class="sxs-lookup"><span data-stu-id="5167d-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="5167d-122">下列範例將它設定為 `SqlMembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="5167d-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="5167d-123">下列範例顯示其組態區段。</span><span class="sxs-lookup"><span data-stu-id="5167d-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="5167d-124">若要設定安全性服務接受使用者名稱/密碼組合</span><span class="sxs-lookup"><span data-stu-id="5167d-124">To configure service security to accept the user name/password combination</span></span>  
  
1. <span data-ttu-id="5167d-125">在組態檔底下[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，新增[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2. <span data-ttu-id="5167d-126">新增[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)來繫結區段。</span><span class="sxs-lookup"><span data-stu-id="5167d-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="5167d-127">如需建立 WCF 繫結元素的詳細資訊，請參閱[How to:在組態中指定的服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="5167d-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3. <span data-ttu-id="5167d-128">將 `mode` 項目的 `<security>` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="5167d-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4. <span data-ttu-id="5167d-129">設定`clientCredentialType`屬性的 <`message`> 項目`UserName`。</span><span class="sxs-lookup"><span data-stu-id="5167d-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="5167d-130">這會指定使用者名稱/密碼組將用來當做用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="5167d-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="5167d-131">下列程式碼範例顯示繫結的組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="5167d-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="5167d-132">設定服務以使用成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="5167d-132">To configure a service to use the membership provider</span></span>  
  
1. <span data-ttu-id="5167d-133">做為子項`<system.serviceModel>`項目，新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目</span><span class="sxs-lookup"><span data-stu-id="5167d-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2. <span data-ttu-id="5167d-134">新增[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)至 <`behaviors`> 項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3. <span data-ttu-id="5167d-135">新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ，並設定`name`屬性設為適當的值。</span><span class="sxs-lookup"><span data-stu-id="5167d-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="5167d-136">新增[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)至 <`behavior`> 項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5. <span data-ttu-id="5167d-137">新增[ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)到`<serviceCredentials>`項目。</span><span class="sxs-lookup"><span data-stu-id="5167d-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6. <span data-ttu-id="5167d-138">將 `userNamePasswordValidationMode` 屬性設定為 `MembershipProvider`。</span><span class="sxs-lookup"><span data-stu-id="5167d-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5167d-139">如果`userNamePasswordValidationMode`未設定值，WCF 會使用 Windows 驗證，而不是 ASP.NET 成員資格提供者。</span><span class="sxs-lookup"><span data-stu-id="5167d-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>  
  
7. <span data-ttu-id="5167d-140">將 `membershipProviderName` 屬性設定為提供者的名稱 (在此主題的第一個程序中新增提供者時已指定)。</span><span class="sxs-lookup"><span data-stu-id="5167d-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="5167d-141">下列範例顯示目前的 `<serviceCredentials>` 片段。</span><span class="sxs-lookup"><span data-stu-id="5167d-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5167d-142">範例</span><span class="sxs-lookup"><span data-stu-id="5167d-142">Example</span></span>  
 <span data-ttu-id="5167d-143">下列程式碼顯示了使用 ASP 成員資格功能之服務的組態。</span><span class="sxs-lookup"><span data-stu-id="5167d-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5167d-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5167d-144">See also</span></span>

- [<span data-ttu-id="5167d-145">如何：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="5167d-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="5167d-146">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="5167d-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
