---
title: HOW TO：建立自訂用戶端身分識別驗證器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: d8529929870b14611c136221f1eefe3eb4ba3d42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767256"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="328ec-102">HOW TO：建立自訂用戶端身分識別驗證器</span><span class="sxs-lookup"><span data-stu-id="328ec-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="328ec-103">*識別*功能的 Windows Communication Foundation (WCF) 可讓用戶端預先指定預期的身分識別的服務。</span><span class="sxs-lookup"><span data-stu-id="328ec-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="328ec-104">每當伺服器向用戶端驗證自身時，就會比對預期身分識別來檢查身分識別 </span><span class="sxs-lookup"><span data-stu-id="328ec-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="328ec-105">(如需身分識別及其運作方式的說明，請參閱 <<c0> [ 服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。)</span><span class="sxs-lookup"><span data-stu-id="328ec-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="328ec-106">必要時，可使用自訂身分識別驗證器來自訂驗證。</span><span class="sxs-lookup"><span data-stu-id="328ec-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="328ec-107">例如，您可以執行其他服務身分識別驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="328ec-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="328ec-108">在這個範例中，自訂身分識別驗證器會檢查從伺服器所傳回的 X.509 憑證中的其他宣告。</span><span class="sxs-lookup"><span data-stu-id="328ec-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="328ec-109">範例應用程式，請參閱[服務身分識別範例](../../../../docs/framework/wcf/samples/service-identity-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="328ec-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="328ec-110">若要擴充 EndpointIdentity 類別</span><span class="sxs-lookup"><span data-stu-id="328ec-110">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="328ec-111">定義衍生自 <xref:System.ServiceModel.EndpointIdentity> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="328ec-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="328ec-112">這個範例會將擴充功能命名為 `OrgEndpointIdentity`。</span><span class="sxs-lookup"><span data-stu-id="328ec-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="328ec-113">加入私用成員與擴充 <xref:System.ServiceModel.Security.IdentityVerifier> 類別將會使用的屬性，對服務所傳回安全性權杖中的宣告執行身分識別檢查。</span><span class="sxs-lookup"><span data-stu-id="328ec-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="328ec-114">這個範例會定義一個屬性：`OrganizationClaim` 屬性。</span><span class="sxs-lookup"><span data-stu-id="328ec-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="328ec-115">若要擴充 IdentityVerifier 類別</span><span class="sxs-lookup"><span data-stu-id="328ec-115">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="328ec-116">定義衍生自 <xref:System.ServiceModel.Security.IdentityVerifier> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="328ec-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="328ec-117">這個範例會將擴充功能命名為 `CustomIdentityVerifier`。</span><span class="sxs-lookup"><span data-stu-id="328ec-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="328ec-118">覆寫 <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="328ec-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="328ec-119">這個方法會判斷身分識別檢查是成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="328ec-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="328ec-120">`CheckAccess` 方法有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="328ec-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="328ec-121">第一個是 <xref:System.ServiceModel.EndpointIdentity> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="328ec-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="328ec-122">第二個是 <xref:System.IdentityModel.Policy.AuthorizationContext> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="328ec-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="328ec-123">在方法實作中，檢查 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 類別的 <xref:System.IdentityModel.Policy.AuthorizationContext> 屬性傳回的宣告集合，並執行必要的驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="328ec-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="328ec-124">這個範例會先尋找 "Distinguished Name" 型別的任何宣告，然後比較名稱與 <xref:System.ServiceModel.EndpointIdentity> 的擴充功能 (`OrgEndpointIdentity`)。</span><span class="sxs-lookup"><span data-stu-id="328ec-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="328ec-125">若要實作 TryGetIdentity 方法</span><span class="sxs-lookup"><span data-stu-id="328ec-125">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="328ec-126">實作 <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> 方法，可判斷 <xref:System.ServiceModel.EndpointIdentity> 類別的執行個體是否可由用戶端傳回。</span><span class="sxs-lookup"><span data-stu-id="328ec-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="328ec-127">WCF 基礎結構呼叫的實作`TryGetIdentity`方法第一次，以從訊息擷取服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="328ec-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="328ec-128">接著，基礎結構會使用所傳回的 `CheckAccess` 和 `EndpointIdentity` 來呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext> 實作。</span><span class="sxs-lookup"><span data-stu-id="328ec-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="328ec-129">在 `TryGetIdentity` 方法中，放入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="328ec-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="328ec-130">若要實作自訂繫結及設定自訂 IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="328ec-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="328ec-131">建立會傳回 <xref:System.ServiceModel.Channels.Binding> 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="328ec-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="328ec-132">這個範例會先建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將其安全性模式設定為 <xref:System.ServiceModel.SecurityMode.Message> 及其 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 設定為 <xref:System.ServiceModel.MessageCredentialType.None>。</span><span class="sxs-lookup"><span data-stu-id="328ec-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="328ec-133">使用 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法來建立 <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>。</span><span class="sxs-lookup"><span data-stu-id="328ec-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="328ec-134">從集合中傳回 <xref:System.ServiceModel.Channels.SecurityBindingElement> 並將其轉換為 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 變數。</span><span class="sxs-lookup"><span data-stu-id="328ec-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="328ec-135">將 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> 類別的 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> 屬性設定為先前新建立的 `CustomIdentityVerifier` 類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="328ec-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="328ec-136">所傳回的自訂繫結會用來建立用戶端和類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="328ec-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="328ec-137">然後，用戶端就可以對服務執行自訂身分識別驗證檢查，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="328ec-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="328ec-138">範例</span><span class="sxs-lookup"><span data-stu-id="328ec-138">Example</span></span>  
 <span data-ttu-id="328ec-139">下列範例會示範 <xref:System.ServiceModel.Security.IdentityVerifier> 類別的完整實作。</span><span class="sxs-lookup"><span data-stu-id="328ec-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="328ec-140">範例</span><span class="sxs-lookup"><span data-stu-id="328ec-140">Example</span></span>  
 <span data-ttu-id="328ec-141">下列範例會示範 <xref:System.ServiceModel.EndpointIdentity> 類別的完整實作。</span><span class="sxs-lookup"><span data-stu-id="328ec-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="328ec-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="328ec-142">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="328ec-143">服務身分識別範例</span><span class="sxs-lookup"><span data-stu-id="328ec-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [<span data-ttu-id="328ec-144">授權原則</span><span class="sxs-lookup"><span data-stu-id="328ec-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
