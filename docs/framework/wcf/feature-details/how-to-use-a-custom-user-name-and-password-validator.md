---
title: HOW TO：使用自訂使用者名稱與密碼驗證程式
description: 瞭解如何為 WFC 應用程式納入自訂密碼驗證器，以取代預設的 Windows 使用者名稱和密碼驗證。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7f69db7bf8248593b64cdae4378983c2460de597
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246788"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0f004-103">HOW TO：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="0f004-103">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="0f004-104">根據預設，當使用使用者名稱和密碼進行驗證時，Windows Communication Foundation （WCF）會使用 Windows 來驗證使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0f004-104">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="0f004-105">不過，WCF 允許自訂的使用者名稱和密碼驗證配置，也稱為*驗證*程式。</span><span class="sxs-lookup"><span data-stu-id="0f004-105">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="0f004-106">若要納入自訂的使用者名稱和密碼驗證程式，請建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別，然後予以設定。</span><span class="sxs-lookup"><span data-stu-id="0f004-106">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="0f004-107">如需範例應用程式，請參閱[使用者名稱密碼驗證](../samples/user-name-password-validator.md)程式。</span><span class="sxs-lookup"><span data-stu-id="0f004-107">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0f004-108">建立自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="0f004-108">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="0f004-109">建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別。</span><span class="sxs-lookup"><span data-stu-id="0f004-109">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="0f004-110">覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，實作自訂驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="0f004-110">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="0f004-111">請勿在實際執行環境使用下列範例中會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f004-111">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="0f004-112">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="0f004-112">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="0f004-113">若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="0f004-113">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0f004-114">將服務設定為使用自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="0f004-114">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="0f004-115">設定繫結，此繫結會在 HTTP(S) 上的任何傳輸或傳輸層級安全性使用訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="0f004-115">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="0f004-116">當使用訊息安全性時，請新增其中一個系統提供的系結，例如 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ，或 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 支援訊息安全性和 `UserName` 認證類型的。</span><span class="sxs-lookup"><span data-stu-id="0f004-116">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="0f004-117">在 HTTP （S）上使用傳輸層級安全性時，請新增 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 或 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ，或 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 使用 HTTP （s）和驗證配置的或 `Basic` 。</span><span class="sxs-lookup"><span data-stu-id="0f004-117">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f004-118">使用 .NET Framework 3.5 或更新版本時，您可以使用自訂使用者名稱和密碼驗證程式搭配訊息和傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="0f004-118">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="0f004-119">有了 WinFX，自訂使用者名稱和密碼驗證程式只能搭配訊息安全性使用。</span><span class="sxs-lookup"><span data-stu-id="0f004-119">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="0f004-120">如需在此內容中使用的詳細資訊 \<netTcpBinding> ，請參閱 [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f004-120">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="0f004-121">在設定檔中的元素底下 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) ，新增 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0f004-121">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="0f004-122">將或專案加入至系結 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 區段。</span><span class="sxs-lookup"><span data-stu-id="0f004-122">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="0f004-123">如需建立 WCF 繫結項目的詳細資訊，請參閱 how [to：在 Configuration 中指定服務](../how-to-specify-a-service-binding-in-configuration.md)系結。</span><span class="sxs-lookup"><span data-stu-id="0f004-123">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="0f004-124">將 `mode` 或的屬性設定 [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) 為 `Message` 、 `Transport` 或 `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="0f004-124">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="0f004-125">設定 `clientCredentialType` 或的屬性 [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f004-125">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="0f004-126">當使用訊息安全性時，請將的 `clientCredentialType` 屬性設定 [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) 為 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="0f004-126">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="0f004-127">在 HTTP （S）上使用傳輸層級安全性時，請將 `clientCredentialType` 或的屬性設定 [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) 為 `Basic` 。</span><span class="sxs-lookup"><span data-stu-id="0f004-127">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="0f004-128">當 WCF 服務裝載于使用傳輸層級安全性的 Internet Information Services （IIS）中，而且 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> 屬性設定為時 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> ，自訂驗證配置會使用 Windows 驗證的子集。</span><span class="sxs-lookup"><span data-stu-id="0f004-128">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="0f004-129">這是因為在此案例中，IIS 會在 WCF 叫用自訂驗證器之前執行 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="0f004-129">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="0f004-130">如需建立 WCF 繫結項目的詳細資訊，請參閱 how [to：在 Configuration 中指定服務](../how-to-specify-a-service-binding-in-configuration.md)系結。</span><span class="sxs-lookup"><span data-stu-id="0f004-130">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="0f004-131">下列範例顯示系結的設定程式碼：</span><span class="sxs-lookup"><span data-stu-id="0f004-131">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="0f004-132">設定行為，指定自訂使用者名稱和密碼驗證程式用來驗證傳入之 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全性權杖的使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="0f004-132">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="0f004-133">加入元素做為專案的子系 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f004-133">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="0f004-134">將加入 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0f004-134">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="0f004-135">新增 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 元素，並將 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="0f004-135">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="0f004-136">將加入 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 至 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="0f004-136">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="0f004-137">將加入 [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) 至 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f004-137">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="0f004-138">將 `userNamePasswordValidationMode` 設為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="0f004-138">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="0f004-139">如果 `userNamePasswordValidationMode` 未設定此值，WCF 會使用 Windows 驗證，而不是自訂使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="0f004-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="0f004-140">將 `customUserNamePasswordValidatorType` 設為代表自訂使用者名稱和密碼驗證程式的類型。</span><span class="sxs-lookup"><span data-stu-id="0f004-140">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="0f004-141">下列範例會顯示 `<serviceCredentials>` 此點的片段：</span><span class="sxs-lookup"><span data-stu-id="0f004-141">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="0f004-142">範例</span><span class="sxs-lookup"><span data-stu-id="0f004-142">Example</span></span>

<span data-ttu-id="0f004-143">以下程式碼範例將示範如何建立自訂的使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="0f004-143">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="0f004-144">請勿在實際執行環境使用會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f004-144">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="0f004-145">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="0f004-145">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0f004-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f004-146">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="0f004-147">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="0f004-147">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="0f004-148">驗證</span><span class="sxs-lookup"><span data-stu-id="0f004-148">Authentication</span></span>](authentication-in-wcf.md)
