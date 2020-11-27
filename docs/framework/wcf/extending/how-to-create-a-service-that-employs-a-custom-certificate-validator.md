---
title: 作法：建立使用自訂憑證驗證程式的服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 31918ca2d96b63911130d22476a6e5a6d48999ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249237"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="650e4-102">作法：建立使用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="650e4-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>

<span data-ttu-id="650e4-103">這個主題將示範如何實作自訂憑證驗證程式，以及如何設定用戶端或服務認證，以使用自訂憑證驗證程式來取代預設的憑證驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="650e4-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="650e4-104">如果使用 x.509 憑證來驗證用戶端或服務，Windows Communication Foundation (WCF) 預設會使用 Windows 憑證存放區和密碼編譯 API 來驗證憑證，並確定它是受信任的。</span><span class="sxs-lookup"><span data-stu-id="650e4-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="650e4-105">有時內建的憑證驗證功能不足，必須變更。</span><span class="sxs-lookup"><span data-stu-id="650e4-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="650e4-106">WCF 提供了一種簡單的方式，可讓使用者新增自訂憑證驗證程式，藉此變更驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="650e4-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="650e4-107">如果指定了自訂憑證驗證程式，WCF 不會使用內建的憑證驗證邏輯，而會改為依賴自訂驗證程式。</span><span class="sxs-lookup"><span data-stu-id="650e4-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="650e4-108">程序</span><span class="sxs-lookup"><span data-stu-id="650e4-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="650e4-109">建立自訂憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="650e4-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="650e4-110">定義衍生自 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="650e4-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="650e4-111">實作抽象的 <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="650e4-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="650e4-112">必須驗證的憑證會傳遞為方法的引數。</span><span class="sxs-lookup"><span data-stu-id="650e4-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="650e4-113">如果根據驗證邏輯，傳遞的憑證是無效的，這個方法會擲回 <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>。</span><span class="sxs-lookup"><span data-stu-id="650e4-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="650e4-114">如果憑證是有效的，方法會傳回至呼叫者。</span><span class="sxs-lookup"><span data-stu-id="650e4-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="650e4-115">若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="650e4-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="650e4-116">在服務組態中指定自訂憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="650e4-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="650e4-117">將 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素和新增 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至專案 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 。</span><span class="sxs-lookup"><span data-stu-id="650e4-117">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="650e4-118">新增 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ，並將 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="650e4-118">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="650e4-119">將加入 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 至 `<behavior>` 元素。</span><span class="sxs-lookup"><span data-stu-id="650e4-119">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="650e4-120">將 `<clientCertificate>` 項目加入至 `<serviceCredentials>` 項目。</span><span class="sxs-lookup"><span data-stu-id="650e4-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="650e4-121">將加入 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) 至 `<clientCertificate>` 元素。</span><span class="sxs-lookup"><span data-stu-id="650e4-121">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="650e4-122">將 `customCertificateValidatorType` 屬性設定為驗證程式類型。</span><span class="sxs-lookup"><span data-stu-id="650e4-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="650e4-123">下列範例會將屬性設定為類型的命名空間和名稱。</span><span class="sxs-lookup"><span data-stu-id="650e4-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="650e4-124">將 `certificateValidationMode` 屬性設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="650e4-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="650e4-125">使用用戶端上的組態來指定自訂憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="650e4-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="650e4-126">將 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素和新增 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至專案 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 。</span><span class="sxs-lookup"><span data-stu-id="650e4-126">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="650e4-127">新增 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="650e4-127">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="650e4-128">加入 `<behavior>` 項目，並將 `name` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="650e4-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="650e4-129">新增 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="650e4-129">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="650e4-130">加入 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="650e4-130">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="650e4-131">加入， [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="650e4-131">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="650e4-132">將 `customCertificateValidatorType` 屬性設定為驗證程式類型。</span><span class="sxs-lookup"><span data-stu-id="650e4-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="650e4-133">將 `certificateValidationMode` 屬性設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="650e4-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="650e4-134">下列範例會將屬性設定為類型的命名空間和名稱。</span><span class="sxs-lookup"><span data-stu-id="650e4-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="650e4-135">使用服務上的程式碼來指定自訂憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="650e4-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="650e4-136">請在 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> 屬性上指定自訂憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="650e4-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="650e4-137">您可以使用 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性來存取服務認證。</span><span class="sxs-lookup"><span data-stu-id="650e4-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="650e4-138">將 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="650e4-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="650e4-139">使用用戶端上的程式碼來指定自訂憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="650e4-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="650e4-140">請使用 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> 屬性來指定自訂憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="650e4-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="650e4-141">您可以使用 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性來存取用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="650e4-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="650e4-142"> ([System.servicemodel 中繼資料公用程式工具 ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 產生的用戶端類別 ( # A0) 一律衍生自 <xref:System.ServiceModel.ClientBase%601> 類別。 ) </span><span class="sxs-lookup"><span data-stu-id="650e4-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="650e4-143">將 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="650e4-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="650e4-144">範例</span><span class="sxs-lookup"><span data-stu-id="650e4-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="650e4-145">描述</span><span class="sxs-lookup"><span data-stu-id="650e4-145">Description</span></span>  

 <span data-ttu-id="650e4-146">下列範例將示範在服務上實作自訂憑證驗證程式及其使用方式。</span><span class="sxs-lookup"><span data-stu-id="650e4-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="650e4-147">程式碼</span><span class="sxs-lookup"><span data-stu-id="650e4-147">Code</span></span>  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="650e4-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="650e4-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
