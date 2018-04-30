---
title: HOW TO：使用自訂使用者名稱與密碼驗證程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ea4f4d7021f02d239b9e2e93a85b5baaf5a0317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="a43c0-102">HOW TO：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="a43c0-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="a43c0-103">根據預設，使用使用者名稱和密碼進行驗證時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會使用 Windows 驗證使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a43c0-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="a43c0-104">不過，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]可讓自訂使用者名稱和密碼驗證配置，也稱為*驗證*。</span><span class="sxs-lookup"><span data-stu-id="a43c0-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="a43c0-105">若要納入自訂的使用者名稱和密碼驗證程式，請建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別，然後予以設定。</span><span class="sxs-lookup"><span data-stu-id="a43c0-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="a43c0-106">範例應用程式，請參閱[使用者名稱密碼驗證程式](../../../../docs/framework/wcf/samples/user-name-password-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="a43c0-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="a43c0-107">建立自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="a43c0-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="a43c0-108">建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別。</span><span class="sxs-lookup"><span data-stu-id="a43c0-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="a43c0-109">覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，實作自訂驗證結構描述。</span><span class="sxs-lookup"><span data-stu-id="a43c0-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="a43c0-110">請勿在實際執行環境使用下列範例中會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a43c0-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="a43c0-111">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="a43c0-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="a43c0-112">若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="a43c0-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="a43c0-113">將服務設定為使用自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="a43c0-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="a43c0-114">設定繫結，此繫結會在 HTTP(S) 上的任何傳輸或傳輸層級安全性使用訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="a43c0-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="a43c0-115">使用訊息安全性時，將其中一個系統提供繫結，例如[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，或[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)支援訊息安全性和`UserName`認證類型。</span><span class="sxs-lookup"><span data-stu-id="a43c0-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="a43c0-116">使用傳輸層級安全性時透過 HTTP (S)，將[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)或[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)或[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)使用 HTTP (S) 和`Basic`驗證配置。</span><span class="sxs-lookup"><span data-stu-id="a43c0-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a43c0-117">使用 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (含) 以後版本時，您可以將自訂使用者名稱和密碼驗證器搭配訊息安全性和傳輸安全性使用。</span><span class="sxs-lookup"><span data-stu-id="a43c0-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="a43c0-118">透過 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]，自訂使用者名稱和密碼驗證器只能與訊息安全性配合使用。</span><span class="sxs-lookup"><span data-stu-id="a43c0-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="a43c0-119">如需有關使用\<netTcpBinding > 在此內容中，請參閱[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a43c0-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="a43c0-120">在組態檔中，在[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，加入[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a43c0-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="a43c0-121">新增[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)或[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)要繫結區段項目。</span><span class="sxs-lookup"><span data-stu-id="a43c0-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="a43c0-122">如需有關建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]繫結項目，請參閱[How to： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a43c0-122">For more information about creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="a43c0-123">設定`mode`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)或[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)至`Message`， `Transport`， `or``TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="a43c0-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="a43c0-124">設定`clientCredentialType`屬性[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)或[\<傳輸 >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="a43c0-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="a43c0-125">使用訊息安全性時，設定`clientCredentialType`屬性[\<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)至`UserName`。</span><span class="sxs-lookup"><span data-stu-id="a43c0-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="a43c0-126">使用傳輸層級安全性時透過 HTTP (S)，設定`clientCredentialType`屬性[\<傳輸 >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)或[\<傳輸 >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)至`Basic`。</span><span class="sxs-lookup"><span data-stu-id="a43c0-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a43c0-127">當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務使用傳輸層級安全性裝載在網際網路資訊服務 (IIS) 中，並且 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> 時，自訂驗證配置會使用 Windows 驗證的子集。</span><span class="sxs-lookup"><span data-stu-id="a43c0-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="a43c0-128">這是因為在這種情況中，IIS 會在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 叫用自訂驗證器之前，先執行 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a43c0-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     <span data-ttu-id="a43c0-129">如需有關建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]繫結項目，請參閱[How to： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a43c0-129">For more information about creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="a43c0-130">下列程式碼範例顯示繫結的組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="a43c0-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2.  <span data-ttu-id="a43c0-131">設定行為，指定自訂使用者名稱和密碼驗證程式用來驗證傳入之 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全性權杖的使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="a43c0-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="a43c0-132">做為子項[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目，加入[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a43c0-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="a43c0-133">新增[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)至[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a43c0-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="a43c0-134">新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目並設定`name`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="a43c0-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="a43c0-135">新增[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)至[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a43c0-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="a43c0-136">新增[ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)至[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="a43c0-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="a43c0-137">將 `userNamePasswordValidationMode` 設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="a43c0-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="a43c0-138">如果沒有設定 `userNamePasswordValidationMode` 值，則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 Windows 驗證，而不會使用自訂的使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="a43c0-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="a43c0-139">將 `customUserNamePasswordValidatorType` 設為代表自訂使用者名稱和密碼驗證程式的類型。</span><span class="sxs-lookup"><span data-stu-id="a43c0-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="a43c0-140">下列範例顯示目前的 `<serviceCredentials>` 片段。</span><span class="sxs-lookup"><span data-stu-id="a43c0-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="a43c0-141">範例</span><span class="sxs-lookup"><span data-stu-id="a43c0-141">Example</span></span>  
 <span data-ttu-id="a43c0-142">以下程式碼範例將示範如何建立自訂的使用者名稱和密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="a43c0-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="a43c0-143">請勿在實際執行環境使用會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a43c0-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="a43c0-144">將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="a43c0-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a43c0-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a43c0-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="a43c0-146">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="a43c0-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="a43c0-147">驗證</span><span class="sxs-lookup"><span data-stu-id="a43c0-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
