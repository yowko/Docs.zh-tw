---
title: <windows> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 115e1822659c04ee37a7364f7b25616b52dc5efe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177822"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="539aa-102">\<windows> 項目的 \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="539aa-102">\<windows> of \<clientCredentials> Element</span></span>

<span data-ttu-id="539aa-103">指定要用於代表用戶端的 Windows 認證的設定。</span><span class="sxs-lookup"><span data-stu-id="539aa-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="539aa-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="539aa-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="539aa-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="539aa-105">Attributes and Elements</span></span>  

 <span data-ttu-id="539aa-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="539aa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="539aa-107">屬性</span><span class="sxs-lookup"><span data-stu-id="539aa-107">Attributes</span></span>  
  
|<span data-ttu-id="539aa-108">屬性</span><span class="sxs-lookup"><span data-stu-id="539aa-108">Attribute</span></span>|<span data-ttu-id="539aa-109">描述</span><span class="sxs-lookup"><span data-stu-id="539aa-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="539aa-110">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="539aa-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="539aa-111">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="539aa-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="539aa-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="539aa-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="539aa-113">-識別：伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="539aa-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="539aa-114">-模擬：伺服器可以在本機系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="539aa-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="539aa-115">-委派：伺服器可以在遠端系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="539aa-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="539aa-116">-Anonymous：伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="539aa-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="539aa-117">-無：未指派模擬等級。</span><span class="sxs-lookup"><span data-stu-id="539aa-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="539aa-118">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="539aa-118">The default is Identification.</span></span> <span data-ttu-id="539aa-119">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="539aa-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="539aa-120">將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。</span><span class="sxs-lookup"><span data-stu-id="539aa-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="539aa-121">將這個屬性設定為， `false` 會讓 Windows Communication Foundation (WCF) 在使用 NTLM 時，盡力擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="539aa-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="539aa-122">請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。</span><span class="sxs-lookup"><span data-stu-id="539aa-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="539aa-123">子元素</span><span class="sxs-lookup"><span data-stu-id="539aa-123">Child Elements</span></span>  

 <span data-ttu-id="539aa-124">無。</span><span class="sxs-lookup"><span data-stu-id="539aa-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="539aa-125">父項目</span><span class="sxs-lookup"><span data-stu-id="539aa-125">Parent Elements</span></span>  
  
|<span data-ttu-id="539aa-126">項目</span><span class="sxs-lookup"><span data-stu-id="539aa-126">Element</span></span>|<span data-ttu-id="539aa-127">描述</span><span class="sxs-lookup"><span data-stu-id="539aa-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="539aa-128">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="539aa-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="539aa-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="539aa-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="539aa-130">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="539aa-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="539aa-131">使用憑證</span><span class="sxs-lookup"><span data-stu-id="539aa-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="539aa-132">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="539aa-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
