---
title: HOW TO：使用自訂使用者名稱與密碼驗證程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: a7573e14d224e2ec861b301816d6d886fd147180
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401025"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="4a4e4-102">HOW TO：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="4a4e4-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="4a4e4-103">根據預設，使用者名稱和密碼是用來進行驗證，Windows Communication Foundation (WCF) 會使用 Windows 驗證的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="4a4e4-104">不過，WCF 可讓自訂使用者名稱和密碼驗證配置，也稱為*驗證*。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="4a4e4-105">若要納入自訂的使用者名稱和密碼驗證程式，請建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別，然後予以設定。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="4a4e4-106">範例應用程式，請參閱[使用者名稱密碼驗證程式](../../../../docs/framework/wcf/samples/user-name-password-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="4a4e4-107">建立自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="4a4e4-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="4a4e4-108">建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="4a4e4-109">覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，實作自訂驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="4a4e4-110">請勿在實際執行環境使用下列範例中會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="4a4e4-111">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="4a4e4-112">若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="4a4e4-113">將服務設定為使用自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="4a4e4-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="4a4e4-114">設定繫結，此繫結會在 HTTP(S) 上的任何傳輸或傳輸層級安全性使用訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="4a4e4-115">使用訊息安全性時，將其中一個系統提供的繫結，例如[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，或有[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)支援訊息安全性，`UserName`認證類型。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="4a4e4-116">使用傳輸層級安全性時透過 HTTP (S)，新增[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)或是[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)，則[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)或是[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)使用 HTTP (S) 和`Basic`驗證配置。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a4e4-117">使用 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (含) 以後版本時，您可以將自訂使用者名稱和密碼驗證器搭配訊息安全性和傳輸安全性使用。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="4a4e4-118">透過 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]，自訂使用者名稱和密碼驗證器只能與訊息安全性配合使用。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="4a4e4-119">如需有關使用\<netTcpBinding > 在此情況下，請參閱[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4a4e4-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="4a4e4-120">在組態檔底下[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，新增[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="4a4e4-121">新增[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)或是[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)項目加入繫結區段。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="4a4e4-122">如需建立 WCF 繫結元素的詳細資訊，請參閱[如何： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="4a4e4-123">設定`mode`的屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)或是[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)至`Message`， `Transport`，或`TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="4a4e4-124">設定`clientCredentialType`的屬性[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)或是[\<傳輸 >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="4a4e4-125">使用訊息安全性時，設定`clientCredentialType`的屬性[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)到`UserName`。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="4a4e4-126">使用傳輸層級安全性時透過 HTTP (S)，設定`clientCredentialType`的屬性[\<傳輸 >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)或是[\<傳輸 >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)至`Basic`。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4a4e4-127">當 WCF 服務裝載在網際網路資訊服務 (IIS) 使用傳輸層級安全性和<xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A>屬性設定為<xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>，自訂驗證配置會使用 Windows 驗證的子集。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="4a4e4-128">這是因為在此案例中，IIS 會執行 Windows 驗證，才能叫用自訂驗證器的 WCF。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>  
  
     <span data-ttu-id="4a4e4-129">如需建立 WCF 繫結元素的詳細資訊，請參閱[如何： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="4a4e4-130">下列程式碼範例顯示繫結的組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-130">The following example shows the configuration code for the binding.</span></span>  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="4a4e4-131">設定行為，指定自訂使用者名稱和密碼驗證程式用來驗證傳入之 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全性權杖的使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="4a4e4-132">做為子項[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="4a4e4-133">新增[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)要[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="4a4e4-134">新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目並將`name`屬性設為適當的值。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="4a4e4-135">新增[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)要[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="4a4e4-136">新增[ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)要[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="4a4e4-137">將 `userNamePasswordValidationMode` 設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="4a4e4-138">如果`userNamePasswordValidationMode`未設定值，WCF 會使用 Windows 驗證，而不是自訂的使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="4a4e4-139">將 `customUserNamePasswordValidatorType` 設為代表自訂使用者名稱和密碼驗證程式的類型。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="4a4e4-140">下列範例顯示目前的 `<serviceCredentials>` 片段。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="4a4e4-141">範例</span><span class="sxs-lookup"><span data-stu-id="4a4e4-141">Example</span></span>  
 <span data-ttu-id="4a4e4-142">以下程式碼範例將示範如何建立自訂的使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="4a4e4-143">請勿在實際執行環境使用會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="4a4e4-144">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="4a4e4-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4a4e4-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a4e4-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="4a4e4-146">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="4a4e4-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="4a4e4-147">驗證</span><span class="sxs-lookup"><span data-stu-id="4a4e4-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
