---
title: HOW TO：指定用戶端認證值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: ecb8f7ef74f1f0625454eb2d6cebf9d282a5ece3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327096"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="c023b-102">HOW TO：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="c023b-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="c023b-103">使用 Windows Communication Foundation (WCF)，服務可以指定用戶端驗證服務的方式。</span><span class="sxs-lookup"><span data-stu-id="c023b-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="c023b-104">例如，服務可以規定用戶端必須出示憑證交付驗證。</span><span class="sxs-lookup"><span data-stu-id="c023b-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="c023b-105">判斷用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="c023b-105">To determine the client credential type</span></span>  
  
1. <span data-ttu-id="c023b-106">從服務的中繼資料端點擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c023b-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="c023b-107">中繼資料通常包含兩個檔案：以您所選程式語言 (預設為 Visual C#) 撰寫的用戶端程式碼，還有 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="c023b-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="c023b-108">擷取中繼資料的方法之一，是使用 Svcutil.exe 工具傳回用戶端程式碼和用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="c023b-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="c023b-109">如需詳細資訊，請參閱 <<c0> [ 擷取的中繼資料](../../../docs/framework/wcf/feature-details/retrieving-metadata.md)並[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="c023b-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2. <span data-ttu-id="c023b-110">開啟 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="c023b-110">Open the XML configuration file.</span></span> <span data-ttu-id="c023b-111">如果您是使用 Svcutil.exe 工具，檔案的預設名稱即為 Output.config。</span><span class="sxs-lookup"><span data-stu-id="c023b-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3. <span data-ttu-id="c023b-112">尋找**\<安全性 >** 項目**模式**屬性 (**< 安全性模式 =** `MessageOrTransport` **>** 其中`MessageOrTransport`設為其中一種安全性模式。</span><span class="sxs-lookup"><span data-stu-id="c023b-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4. <span data-ttu-id="c023b-113">找出符合模式值的子項目。</span><span class="sxs-lookup"><span data-stu-id="c023b-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="c023b-114">例如，如果模式設定為**訊息**，尋找**\<訊息 >** 中所包含的項目**\<安全性 >** 項目。</span><span class="sxs-lookup"><span data-stu-id="c023b-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5. <span data-ttu-id="c023b-115">記下值指派給**clientCredentialType**屬性。</span><span class="sxs-lookup"><span data-stu-id="c023b-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="c023b-116">實際值取決於使用的模式是傳輸還是訊息。</span><span class="sxs-lookup"><span data-stu-id="c023b-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="c023b-117">下列 XML 程式碼所示為使用訊息安全性，且用戶端驗證時需要憑證的用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="c023b-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="c023b-118">範例：TCP 傳輸模式結合用戶端認證的憑證</span><span class="sxs-lookup"><span data-stu-id="c023b-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="c023b-119">這個範例會將安全性模式設為傳輸模式，並將用戶端認證值設為 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c023b-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="c023b-120">下列程序示範如何透過程式碼與組態，設定用戶端的用戶端認證值。</span><span class="sxs-lookup"><span data-stu-id="c023b-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="c023b-121">這是假設您已使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務傳回中繼資料 （程式碼和組態）。</span><span class="sxs-lookup"><span data-stu-id="c023b-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="c023b-122">如需詳細資訊，請參閱[如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="c023b-122">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="c023b-123">若要透過程式碼指定用戶端的用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="c023b-123">To specify the client credential value on the client in code</span></span>  
  
1. <span data-ttu-id="c023b-124">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務產生程式碼和組態。</span><span class="sxs-lookup"><span data-stu-id="c023b-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2. <span data-ttu-id="c023b-125">建立 WCF 用戶端會使用產生的程式碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c023b-125">Create an instance of the WCF client using the generated code.</span></span>  
  
3. <span data-ttu-id="c023b-126">在用戶端類別上，將 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="c023b-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="c023b-127">這個範例會使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法，將屬性設定為 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c023b-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="c023b-128">您可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 類別的任何一種列舉。</span><span class="sxs-lookup"><span data-stu-id="c023b-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="c023b-129">此處將使用主旨名稱，以避免憑證因為到期日關係而變更。</span><span class="sxs-lookup"><span data-stu-id="c023b-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="c023b-130">使用主旨名稱可讓基礎結構重新找到憑證。</span><span class="sxs-lookup"><span data-stu-id="c023b-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="c023b-131">若要透過組態指定用戶端的用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="c023b-131">To specify the client credential value on the client in configuration</span></span>  
  
1. <span data-ttu-id="c023b-132">新增[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)項目[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c023b-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2. <span data-ttu-id="c023b-133">新增[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c023b-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="c023b-134">請務必將必要的 `name` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="c023b-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="c023b-135">新增[ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)項目[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c023b-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4. <span data-ttu-id="c023b-136">將下列屬性設為適當的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c023b-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="c023b-137">如需憑證的詳細資訊，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="c023b-137">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
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
  
5. <span data-ttu-id="c023b-138">設定用戶端時，設定 `behaviorConfiguration` 項目的 `<endpoint>` 屬性來指定行為，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c023b-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="c023b-139">端點元素是子系[\<用戶端 >](../../../docs/framework/configure-apps/file-schema/wcf/client.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c023b-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="c023b-140">同時，將 `bindingConfiguration` 屬性設定為用戶端的繫結，以指定繫結組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="c023b-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="c023b-141">如果您使用的是產生的組態檔，繫結名稱就會自動產生。</span><span class="sxs-lookup"><span data-stu-id="c023b-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="c023b-142">在這個範例中，名稱為 `"tcpBindingWithCredential"`。</span><span class="sxs-lookup"><span data-stu-id="c023b-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c023b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c023b-143">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="c023b-144">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="c023b-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="c023b-145">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="c023b-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c023b-146">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c023b-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="c023b-147">使用憑證</span><span class="sxs-lookup"><span data-stu-id="c023b-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c023b-148">HOW TO：建立用戶端</span><span class="sxs-lookup"><span data-stu-id="c023b-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="c023b-149">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="c023b-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="c023b-150">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="c023b-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="c023b-151">\<message></span><span class="sxs-lookup"><span data-stu-id="c023b-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="c023b-152">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c023b-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="c023b-153">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c023b-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="c023b-154">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="c023b-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="c023b-155">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c023b-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
