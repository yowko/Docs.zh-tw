---
title: '&lt;httpDigest&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2211c593090d697ae07350fcf7ac491b9d23e2d0
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150135"
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="e533e-102">&lt;httpDigest&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="e533e-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="e533e-103">指定對服務驗證用戶端時，所使用的摘要式類型認證。</span><span class="sxs-lookup"><span data-stu-id="e533e-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="e533e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e533e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e533e-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e533e-105">\<behaviors></span></span>  
<span data-ttu-id="e533e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e533e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e533e-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e533e-107">\<behavior></span></span>  
<span data-ttu-id="e533e-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e533e-108">\<clientCredentials></span></span>  
<span data-ttu-id="e533e-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="e533e-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e533e-110">語法</span><span class="sxs-lookup"><span data-stu-id="e533e-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e533e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e533e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e533e-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e533e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e533e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e533e-113">Attributes</span></span>  
  
|<span data-ttu-id="e533e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e533e-114">Attribute</span></span>|<span data-ttu-id="e533e-115">描述</span><span class="sxs-lookup"><span data-stu-id="e533e-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="e533e-116">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="e533e-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="e533e-117">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="e533e-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="e533e-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="e533e-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e533e-119">識別：伺服器可以取得身分識別和權限的用戶端，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="e533e-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="e533e-120">模擬：伺服器可以模擬用戶端的本機系統上的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="e533e-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="e533e-121">-委派：伺服器可以模擬用戶端的安全性內容，在遠端系統上。</span><span class="sxs-lookup"><span data-stu-id="e533e-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="e533e-122">匿名：伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="e533e-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="e533e-123">-None:未指派模擬等級。</span><span class="sxs-lookup"><span data-stu-id="e533e-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="e533e-124">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="e533e-124">The default is Identification.</span></span> <span data-ttu-id="e533e-125">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="e533e-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e533e-126">子元素</span><span class="sxs-lookup"><span data-stu-id="e533e-126">Child Elements</span></span>  
 <span data-ttu-id="e533e-127">無</span><span class="sxs-lookup"><span data-stu-id="e533e-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e533e-128">父項目</span><span class="sxs-lookup"><span data-stu-id="e533e-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e533e-129">項目</span><span class="sxs-lookup"><span data-stu-id="e533e-129">Element</span></span>|<span data-ttu-id="e533e-130">描述</span><span class="sxs-lookup"><span data-stu-id="e533e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e533e-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e533e-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="e533e-132">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="e533e-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e533e-133">備註</span><span class="sxs-lookup"><span data-stu-id="e533e-133">Remarks</span></span>  
 <span data-ttu-id="e533e-134">摘要是指使用演算法和一組輸入所決定的雜湊。</span><span class="sxs-lookup"><span data-stu-id="e533e-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="e533e-135">驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="e533e-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="e533e-136">用戶端可計算雜湊，並將它傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="e533e-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="e533e-137">服務也會計算雜湊並比較兩者的值。</span><span class="sxs-lookup"><span data-stu-id="e533e-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="e533e-138">比對會驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="e533e-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="e533e-139">此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。</span><span class="sxs-lookup"><span data-stu-id="e533e-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="e533e-140">如需詳細資訊，請參閱 <<c0> [ 在 IIS 6.0 中的摘要式驗證](https://go.microsoft.com/fwlink/?LinkId=88443)。</span><span class="sxs-lookup"><span data-stu-id="e533e-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e533e-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e533e-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="e533e-142">安全性行為</span><span class="sxs-lookup"><span data-stu-id="e533e-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="e533e-143">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="e533e-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="e533e-144">使用憑證</span><span class="sxs-lookup"><span data-stu-id="e533e-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="e533e-145">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="e533e-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
