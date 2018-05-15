---
title: '&lt;clientCredentials&gt; 的 &lt;windows&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 9badcfafff4bc09a16b0b9a565a9ea5c01e26bb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="cc1f0-102">&lt;clientCredentials&gt; 的 &lt;windows&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="cc1f0-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="cc1f0-103">指定要用於代表用戶端的 Windows 認證的設定。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="cc1f0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc1f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc1f0-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cc1f0-105">\<behaviors></span></span>  
<span data-ttu-id="cc1f0-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="cc1f0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="cc1f0-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cc1f0-107">\<behavior></span></span>  
<span data-ttu-id="cc1f0-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="cc1f0-108">\<clientCredentials></span></span>  
<span data-ttu-id="cc1f0-109">\<windows ></span><span class="sxs-lookup"><span data-stu-id="cc1f0-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1f0-110">語法</span><span class="sxs-lookup"><span data-stu-id="cc1f0-110">Syntax</span></span>  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc1f0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cc1f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc1f0-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc1f0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cc1f0-113">Attributes</span></span>  
  
|<span data-ttu-id="cc1f0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cc1f0-114">Attribute</span></span>|<span data-ttu-id="cc1f0-115">描述</span><span class="sxs-lookup"><span data-stu-id="cc1f0-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="cc1f0-116">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="cc1f0-117">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="cc1f0-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="cc1f0-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cc1f0-119">-Identification： 伺服器可取得的身分識別和權限的用戶端，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="cc1f0-120">模擬： 伺服器可以模擬用戶端的本機系統上的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="cc1f0-121">-Delegation： 伺服器可以模擬用戶端的安全性內容，在遠端系統上。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="cc1f0-122">匿名： 伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="cc1f0-123">-無： 模擬層級未指派。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="cc1f0-124">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-124">The default is Identification.</span></span> <span data-ttu-id="cc1f0-125">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="cc1f0-126">將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="cc1f0-127">此屬性設定為`false`會導致 Windows Communication Foundation (WCF) 進行盡力擲回例外狀況，如果使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="cc1f0-128">請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc1f0-129">子項目</span><span class="sxs-lookup"><span data-stu-id="cc1f0-129">Child Elements</span></span>  
 <span data-ttu-id="cc1f0-130">無。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc1f0-131">父項目</span><span class="sxs-lookup"><span data-stu-id="cc1f0-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cc1f0-132">項目</span><span class="sxs-lookup"><span data-stu-id="cc1f0-132">Element</span></span>|<span data-ttu-id="cc1f0-133">描述</span><span class="sxs-lookup"><span data-stu-id="cc1f0-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc1f0-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="cc1f0-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="cc1f0-135">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="cc1f0-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc1f0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc1f0-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="cc1f0-137">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="cc1f0-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cc1f0-138">使用憑證</span><span class="sxs-lookup"><span data-stu-id="cc1f0-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="cc1f0-139">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="cc1f0-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
