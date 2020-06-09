---
title: HOW TO：設定本機簽發者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601240"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="43696-102">HOW TO：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="43696-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="43696-103">本主題會說明如何將用戶端設定成使用已發行權杖的本機簽發者。</span><span class="sxs-lookup"><span data-stu-id="43696-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="43696-104">通常，當用戶端與聯合服務進行通訊時，服務都會指定特定安全性權杖服務的位址，該服務預期會發出用戶端要用來向聯合服務驗證自己的權杖。</span><span class="sxs-lookup"><span data-stu-id="43696-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="43696-105">在某些情況下，可能會將用戶端設定為使用*本機簽發者*。</span><span class="sxs-lookup"><span data-stu-id="43696-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="43696-106">在同盟系結的簽發者位址是或的情況下，Windows Communication Foundation （WCF）會使用本機簽發者 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 。</span><span class="sxs-lookup"><span data-stu-id="43696-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="43696-107">在這種情況下，您必須設定包含本機簽發者位址的 <xref:System.ServiceModel.Description.ClientCredentials>，以及用來與該簽發者進行通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="43696-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="43696-108">如果 <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> 類別的屬性 `ClientCredentials` 設定為，則 `true` 未指定本機簽發者位址，而或其他同盟系結所指定的簽發者位址 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 為 `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` 、或，則會 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 使用 Windows CardSpace 簽發者。</span><span class="sxs-lookup"><span data-stu-id="43696-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="43696-109">透過程式碼來設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="43696-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="43696-110">建立型別為 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 的變數</span><span class="sxs-lookup"><span data-stu-id="43696-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="43696-111">將此變數設為從 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 類別的 `ClientCredentials` 屬性傳回的執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="43696-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="43696-112">該執行個體會由用戶端 (繼承自 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>) 的 <xref:System.ServiceModel.ClientBase%601> 屬性，或是 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 的 <xref:System.ServiceModel.ChannelFactory> 屬性傳回：</span><span class="sxs-lookup"><span data-stu-id="43696-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="43696-113">將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> 屬性設定為 <xref:System.ServiceModel.EndpointAddress> 的新執行個體，其本機簽發者位址會當做建構函式 (Constructor) 的引數。</span><span class="sxs-lookup"><span data-stu-id="43696-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="43696-114">或者，建立新的 <xref:System.Uri> 執行個體做為該建構函式的引數。</span><span class="sxs-lookup"><span data-stu-id="43696-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="43696-115">`addressHeaders`參數是實例的陣列 <xref:System.ServiceModel.Channels.AddressHeader> ，如下所示。</span><span class="sxs-lookup"><span data-stu-id="43696-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="43696-116">使用屬性來設定本機簽發者的系結 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> 。</span><span class="sxs-lookup"><span data-stu-id="43696-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="43696-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="43696-117">Optional.</span></span> <span data-ttu-id="43696-118">將本機簽發者的已設定端點行為新增到 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> 屬性所傳回的集合，即可新增該行為。</span><span class="sxs-lookup"><span data-stu-id="43696-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="43696-119">透過組態來設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="43696-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="43696-120">建立專案 [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) 做為專案的子系 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) ，該專案本身就是 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 端點行為中元素的子系。</span><span class="sxs-lookup"><span data-stu-id="43696-120">Create a [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="43696-121">將 `address` 屬性設定為將接受權杖要求之本機簽發者的位址。</span><span class="sxs-lookup"><span data-stu-id="43696-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="43696-122">將 `binding` 和 `bindingConfiguration` 屬性設定為會參考當與本機簽發者端點進行通訊時所使用之適當繫結的值。</span><span class="sxs-lookup"><span data-stu-id="43696-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="43696-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="43696-123">Optional.</span></span> <span data-ttu-id="43696-124">將 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 元素設定為 <> 專案的子系 `localIssuer` ，並指定本機簽發者的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="43696-124">Set the [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="43696-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="43696-125">Optional.</span></span> <span data-ttu-id="43696-126">將 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 元素設定為 <> 專案的子系 `localIssuer` ，並指定必要的其他標頭，以便正確地定址本機簽發者。</span><span class="sxs-lookup"><span data-stu-id="43696-126">Set the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="43696-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="43696-127">.NET Framework Security</span></span>

<span data-ttu-id="43696-128">請注意，如果已指定特定繫結的簽發者位址和繫結，這時使用該繫結的端點就不會使用該本機簽發者。</span><span class="sxs-lookup"><span data-stu-id="43696-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="43696-129">預期一定要使用該本機簽發者的用戶端應該要確定自己沒有使用這類繫結，否則它們就會修改繫結，進而使得簽發者位址成為 `null`。</span><span class="sxs-lookup"><span data-stu-id="43696-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="43696-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="43696-130">See also</span></span>

- [<span data-ttu-id="43696-131">HOW TO：設定聯合服務的認證</span><span class="sxs-lookup"><span data-stu-id="43696-131">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="43696-132">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="43696-132">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="43696-133">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="43696-133">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)
