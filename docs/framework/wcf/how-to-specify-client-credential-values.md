---
title: HOW TO：指定用戶端認證值
description: 瞭解 WCF 服務如何指定用戶端驗證該服務的方式。 這個範例會指定 x.509 憑證和傳輸模式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244448"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="4d53c-104">HOW TO：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="4d53c-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="4d53c-105">使用 Windows Communication Foundation （WCF），服務可以指定如何向服務驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="4d53c-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="4d53c-106">例如，服務可以規定用戶端必須出示憑證交付驗證。</span><span class="sxs-lookup"><span data-stu-id="4d53c-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="4d53c-107">判斷用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="4d53c-107">To determine the client credential type</span></span>

1. <span data-ttu-id="4d53c-108">從服務的中繼資料端點擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4d53c-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="4d53c-109">中繼資料通常包含兩個檔案：以您所選程式語言 (預設為 Visual C#) 撰寫的用戶端程式碼，還有 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="4d53c-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="4d53c-110">擷取中繼資料的方法之一，是使用 Svcutil.exe 工具傳回用戶端程式碼和用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="4d53c-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="4d53c-111">如需詳細資訊，請參閱抓取[中繼資料](./feature-details/retrieving-metadata.md)和[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="4d53c-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="4d53c-112">開啟 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="4d53c-112">Open the XML configuration file.</span></span> <span data-ttu-id="4d53c-113">如果您是使用 Svcutil.exe 工具，檔案的預設名稱即為 Output.config。</span><span class="sxs-lookup"><span data-stu-id="4d53c-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="4d53c-114">尋找 **\<security>** 具有**mode**屬性的元素（ **\<security mode =**`MessageOrTransport`**>** 其中 `MessageOrTransport` 設定為其中一個安全性模式）。</span><span class="sxs-lookup"><span data-stu-id="4d53c-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="4d53c-115">找出符合模式值的子項目。</span><span class="sxs-lookup"><span data-stu-id="4d53c-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="4d53c-116">例如，如果 [模式] 設定為 [**訊息**]，請尋找 **\<message>** 元素中包含的專案 **\<security>** 。</span><span class="sxs-lookup"><span data-stu-id="4d53c-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="4d53c-117">請注意指派給**clientCredentialType**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4d53c-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="4d53c-118">實際值取決於使用的模式是傳輸還是訊息。</span><span class="sxs-lookup"><span data-stu-id="4d53c-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="4d53c-119">下列 XML 程式碼所示為使用訊息安全性，且用戶端驗證時需要憑證的用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="4d53c-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="4d53c-120">範例：TCP 傳輸模式結合用戶端認證的憑證</span><span class="sxs-lookup"><span data-stu-id="4d53c-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="4d53c-121">這個範例會將安全性模式設為傳輸模式，並將用戶端認證值設為 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="4d53c-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="4d53c-122">下列程序示範如何透過程式碼與組態，設定用戶端的用戶端認證值。</span><span class="sxs-lookup"><span data-stu-id="4d53c-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="4d53c-123">這會假設您已使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)來傳回服務的中繼資料（程式碼和設定）。</span><span class="sxs-lookup"><span data-stu-id="4d53c-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="4d53c-124">如需詳細資訊，請參閱[如何：建立用戶端](how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="4d53c-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="4d53c-125">若要透過程式碼指定用戶端的用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="4d53c-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="4d53c-126">使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md) ，從服務產生程式碼和設定。</span><span class="sxs-lookup"><span data-stu-id="4d53c-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="4d53c-127">使用產生的程式碼，建立 WCF 用戶端的實例。</span><span class="sxs-lookup"><span data-stu-id="4d53c-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="4d53c-128">在用戶端類別上，將 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="4d53c-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="4d53c-129">這個範例會使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法，將屬性設定為 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="4d53c-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="4d53c-130">您可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 類別的任何一種列舉。</span><span class="sxs-lookup"><span data-stu-id="4d53c-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="4d53c-131">此處將使用主旨名稱，以避免憑證因為到期日關係而變更。</span><span class="sxs-lookup"><span data-stu-id="4d53c-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="4d53c-132">使用主旨名稱可讓基礎結構重新找到憑證。</span><span class="sxs-lookup"><span data-stu-id="4d53c-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="4d53c-133">若要透過組態指定用戶端的用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="4d53c-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="4d53c-134">將 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 元素新增至專案 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="4d53c-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="4d53c-135">將 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 元素新增至專案 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="4d53c-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="4d53c-136">請務必將必要的 `name` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="4d53c-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="4d53c-137">將 [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) 元素新增至專案 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="4d53c-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="4d53c-138">將下列屬性設為適當的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4d53c-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="4d53c-139">如需憑證的詳細資訊，請參閱[使用憑證](./feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="4d53c-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. <span data-ttu-id="4d53c-140">設定用戶端時，設定 `behaviorConfiguration` 項目的 `<endpoint>` 屬性來指定行為，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4d53c-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="4d53c-141">端點元素是元素的子系 [\<client>](../configure-apps/file-schema/wcf/client.md) 。</span><span class="sxs-lookup"><span data-stu-id="4d53c-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="4d53c-142">同時，將 `bindingConfiguration` 屬性設定為用戶端的繫結，以指定繫結組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d53c-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="4d53c-143">如果您使用的是產生的組態檔，繫結名稱就會自動產生。</span><span class="sxs-lookup"><span data-stu-id="4d53c-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="4d53c-144">在此範例中，該名稱為 `"tcpBindingWithCredential"`。</span><span class="sxs-lookup"><span data-stu-id="4d53c-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="4d53c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d53c-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="4d53c-146">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="4d53c-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="4d53c-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="4d53c-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="4d53c-148">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="4d53c-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="4d53c-149">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="4d53c-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="4d53c-150">如何：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="4d53c-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
