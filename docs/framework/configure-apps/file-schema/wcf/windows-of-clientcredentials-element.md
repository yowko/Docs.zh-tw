---
title: <windows> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399122"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="dca25-102">\<windows> 項目的 \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="dca25-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="dca25-103">指定要用於代表用戶端的 Windows 認證的設定。</span><span class="sxs-lookup"><span data-stu-id="dca25-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="dca25-104">語法</span><span class="sxs-lookup"><span data-stu-id="dca25-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dca25-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dca25-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dca25-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dca25-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dca25-107">屬性</span><span class="sxs-lookup"><span data-stu-id="dca25-107">Attributes</span></span>  
  
|<span data-ttu-id="dca25-108">屬性</span><span class="sxs-lookup"><span data-stu-id="dca25-108">Attribute</span></span>|<span data-ttu-id="dca25-109">描述</span><span class="sxs-lookup"><span data-stu-id="dca25-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="dca25-110">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="dca25-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="dca25-111">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="dca25-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="dca25-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="dca25-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dca25-113">-識別：伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="dca25-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="dca25-114">-模擬：伺服器可以在本機系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="dca25-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="dca25-115">-委派：伺服器可以在遠端系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="dca25-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="dca25-116">-Anonymous：伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="dca25-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="dca25-117">-None：未指派模擬層級。</span><span class="sxs-lookup"><span data-stu-id="dca25-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="dca25-118">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="dca25-118">The default is Identification.</span></span> <span data-ttu-id="dca25-119">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="dca25-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="dca25-120">將這個屬性設定為 `true` 時，如果 Kerberos 無法使用，會允許驗證降級為 NTLM。</span><span class="sxs-lookup"><span data-stu-id="dca25-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="dca25-121">將此屬性設定為， `false` 會使 Windows Communication Foundation （WCF）在使用 NTLM 時能夠盡力擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dca25-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="dca25-122">請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。</span><span class="sxs-lookup"><span data-stu-id="dca25-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dca25-123">子元素</span><span class="sxs-lookup"><span data-stu-id="dca25-123">Child Elements</span></span>  
 <span data-ttu-id="dca25-124">無。</span><span class="sxs-lookup"><span data-stu-id="dca25-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dca25-125">父項目</span><span class="sxs-lookup"><span data-stu-id="dca25-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dca25-126">元素</span><span class="sxs-lookup"><span data-stu-id="dca25-126">Element</span></span>|<span data-ttu-id="dca25-127">描述</span><span class="sxs-lookup"><span data-stu-id="dca25-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="dca25-128">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="dca25-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dca25-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dca25-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="dca25-130">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="dca25-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="dca25-131">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="dca25-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dca25-132">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="dca25-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
