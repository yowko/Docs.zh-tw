---
title: <windows> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399122"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="86e5f-102">\<clientCredentials > 元素\<的 windows ></span><span class="sxs-lookup"><span data-stu-id="86e5f-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="86e5f-103">指定要用於代表用戶端的 Windows 認證的設定。</span><span class="sxs-lookup"><span data-stu-id="86e5f-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
<span data-ttu-id="86e5f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86e5f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86e5f-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="86e5f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86e5f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="86e5f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="86e5f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="86e5f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="86e5f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="86e5f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="86e5f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="86e5f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="86e5f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windows >**</span><span class="sxs-lookup"><span data-stu-id="86e5f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e5f-111">語法</span><span class="sxs-lookup"><span data-stu-id="86e5f-111">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86e5f-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86e5f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86e5f-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="86e5f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86e5f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="86e5f-114">Attributes</span></span>  
  
|<span data-ttu-id="86e5f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="86e5f-115">Attribute</span></span>|<span data-ttu-id="86e5f-116">描述</span><span class="sxs-lookup"><span data-stu-id="86e5f-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="86e5f-117">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="86e5f-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="86e5f-118">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="86e5f-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="86e5f-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="86e5f-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86e5f-120">發現伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="86e5f-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="86e5f-121">申請伺服器可以在本機系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="86e5f-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="86e5f-122">其它伺服器可以在遠端系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="86e5f-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="86e5f-123">匿名伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="86e5f-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="86e5f-124">無未指派模擬層級。</span><span class="sxs-lookup"><span data-stu-id="86e5f-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="86e5f-125">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="86e5f-125">The default is Identification.</span></span> <span data-ttu-id="86e5f-126">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="86e5f-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="86e5f-127">將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。</span><span class="sxs-lookup"><span data-stu-id="86e5f-127">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="86e5f-128">將此屬性設定`false`為，會使 Windows Communication Foundation （WCF）在使用 NTLM 時能夠盡力擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86e5f-128">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="86e5f-129">請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。</span><span class="sxs-lookup"><span data-stu-id="86e5f-129">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86e5f-130">子元素</span><span class="sxs-lookup"><span data-stu-id="86e5f-130">Child Elements</span></span>  
 <span data-ttu-id="86e5f-131">無。</span><span class="sxs-lookup"><span data-stu-id="86e5f-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86e5f-132">父項目</span><span class="sxs-lookup"><span data-stu-id="86e5f-132">Parent Elements</span></span>  
  
|<span data-ttu-id="86e5f-133">項目</span><span class="sxs-lookup"><span data-stu-id="86e5f-133">Element</span></span>|<span data-ttu-id="86e5f-134">描述</span><span class="sxs-lookup"><span data-stu-id="86e5f-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86e5f-135">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="86e5f-135">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="86e5f-136">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="86e5f-136">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86e5f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86e5f-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="86e5f-138">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="86e5f-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="86e5f-139">使用憑證</span><span class="sxs-lookup"><span data-stu-id="86e5f-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="86e5f-140">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="86e5f-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
