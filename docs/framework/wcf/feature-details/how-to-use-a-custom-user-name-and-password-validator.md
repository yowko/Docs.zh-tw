---
title: HOW TO：使用自訂使用者名稱與密碼驗證程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 98ffad7e717aac949509fa701c77d8ba2b80a695
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834699"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="15168-102">HOW TO：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="15168-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="15168-103">根據預設，當使用使用者名稱和密碼進行驗證時，Windows Communication Foundation （WCF）會使用 Windows 來驗證使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="15168-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="15168-104">不過，WCF 允許自訂的使用者名稱和密碼驗證配置，也稱為*驗證*程式。</span><span class="sxs-lookup"><span data-stu-id="15168-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="15168-105">若要納入自訂的使用者名稱和密碼驗證程式，請建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別，然後予以設定。</span><span class="sxs-lookup"><span data-stu-id="15168-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="15168-106">如需範例應用程式，請參閱[使用者名稱密碼驗證](../samples/user-name-password-validator.md)程式。</span><span class="sxs-lookup"><span data-stu-id="15168-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="15168-107">建立自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="15168-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="15168-108">建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別。</span><span class="sxs-lookup"><span data-stu-id="15168-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="15168-109">覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，實作自訂驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="15168-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="15168-110">請勿在實際執行環境使用下列範例中會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15168-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="15168-111">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="15168-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="15168-112">若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="15168-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="15168-113">將服務設定為使用自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="15168-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="15168-114">設定繫結，此繫結會在 HTTP(S) 上的任何傳輸或傳輸層級安全性使用訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="15168-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="15168-115">使用訊息安全性時，請新增其中一個系統提供的系結，例如[@no__t 1wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，或是支援訊息安全性和 `UserName` 認證類型的[@no__t 3customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="15168-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="15168-116">在 HTTP （S）上使用傳輸層級安全性時，請新增[\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md)或[\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md)、 [@no__t 5netTcpBinding >](../../configure-apps/file-schema/wcf/nettcpbinding.md)或使用 HTTP （s）的[@no__t 7customBinding >](../../configure-apps/file-schema/wcf/custombinding.md) ，以及@no__t 8 驗證配置。</span><span class="sxs-lookup"><span data-stu-id="15168-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="15168-117">使用 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (含) 以後版本時，您可以將自訂使用者名稱和密碼驗證器搭配訊息安全性和傳輸安全性使用。</span><span class="sxs-lookup"><span data-stu-id="15168-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="15168-118">有了 WinFX，自訂使用者名稱和密碼驗證程式只能搭配訊息安全性使用。</span><span class="sxs-lookup"><span data-stu-id="15168-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="15168-119">如需在此內容中使用 @no__t 0netTcpBinding > 的詳細資訊，請參閱[@no__t 2security >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="15168-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="15168-120">在設定檔中的[\<System system.servicemodel >](../../configure-apps/file-schema/wcf/system-servicemodel.md)元素底下，新增[@no__t 3bindings 的 >](../../configure-apps/file-schema/wcf/bindings.md)元素。</span><span class="sxs-lookup"><span data-stu-id="15168-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="15168-121">將[@no__t 1wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md)或[@no__t 3basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md)專案新增至 [系結] 區段。</span><span class="sxs-lookup"><span data-stu-id="15168-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="15168-122">如需建立 WCF 繫結項目的詳細資訊，請參閱 [How to：在設定中](../how-to-specify-a-service-binding-in-configuration.md)指定服務系結。</span><span class="sxs-lookup"><span data-stu-id="15168-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="15168-123">將[\<security >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)或[\<security >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)的 `mode` 屬性設定為 `Message`、`Transport` 或 `TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="15168-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="15168-124">設定[\<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)或[\<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)的 `clientCredentialType` 屬性。</span><span class="sxs-lookup"><span data-stu-id="15168-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="15168-125">當使用訊息安全性時，請將[@no__t 2message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)的 `clientCredentialType` 屬性設定為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="15168-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="15168-126">在 HTTP （S）上使用傳輸層級安全性時，請將[\<transport >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)的 `clientCredentialType` 屬性或[@no__t 4transport >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)設定為 `Basic`。</span><span class="sxs-lookup"><span data-stu-id="15168-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="15168-127">當 WCF 服務裝載于使用傳輸層級安全性的 Internet Information Services （IIS）中，而 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> 時，自訂驗證配置會使用 Windows 驗證的子集。</span><span class="sxs-lookup"><span data-stu-id="15168-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="15168-128">這是因為在此案例中，IIS 會在 WCF 叫用自訂驗證器之前執行 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="15168-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="15168-129">如需建立 WCF 繫結項目的詳細資訊，請參閱 [How to：在設定中](../how-to-specify-a-service-binding-in-configuration.md)指定服務系結。</span><span class="sxs-lookup"><span data-stu-id="15168-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="15168-130">下列範例顯示系結的設定程式碼：</span><span class="sxs-lookup"><span data-stu-id="15168-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="15168-131">設定行為，指定自訂使用者名稱和密碼驗證程式用來驗證傳入之 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全性權杖的使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="15168-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="15168-132">做為[\<system >](../../configure-apps/file-schema/wcf/system-servicemodel.md)元素的子系，請新增[@no__t 3behaviors >](../../configure-apps/file-schema/wcf/behaviors.md)專案。</span><span class="sxs-lookup"><span data-stu-id="15168-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="15168-133">將[@no__t 1serviceBehaviors >](../../configure-apps/file-schema/wcf/servicebehaviors.md)新增至[\<behaviors >](../../configure-apps/file-schema/wcf/behaviors.md)元素。</span><span class="sxs-lookup"><span data-stu-id="15168-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="15168-134">新增[@no__t 1behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)元素，並將 @no__t 2 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="15168-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="15168-135">將[@no__t 1serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md)新增至[\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)元素。</span><span class="sxs-lookup"><span data-stu-id="15168-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="15168-136">將[@no__t 1userNameAuthentication >](../../configure-apps/file-schema/wcf/usernameauthentication.md)新增至[@no__t 3serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="15168-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="15168-137">將 `userNamePasswordValidationMode` 設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="15168-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="15168-138">如果未設定 `userNamePasswordValidationMode` 值，WCF 會使用 Windows 驗證，而不是自訂使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="15168-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="15168-139">將 `customUserNamePasswordValidatorType` 設為代表自訂使用者名稱和密碼驗證程式的類型。</span><span class="sxs-lookup"><span data-stu-id="15168-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="15168-140">下列範例會顯示此點的 `<serviceCredentials>` 片段：</span><span class="sxs-lookup"><span data-stu-id="15168-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="15168-141">範例</span><span class="sxs-lookup"><span data-stu-id="15168-141">Example</span></span>

<span data-ttu-id="15168-142">以下程式碼範例將示範如何建立自訂的使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="15168-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="15168-143">請勿在實際執行環境使用會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15168-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="15168-144">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="15168-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="15168-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15168-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- <span data-ttu-id="15168-146">[如何：使用 ASP.NET 成員資格提供者 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="15168-146">[How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md)</span></span>
- [<span data-ttu-id="15168-147">驗證</span><span class="sxs-lookup"><span data-stu-id="15168-147">Authentication</span></span>](authentication-in-wcf.md)
