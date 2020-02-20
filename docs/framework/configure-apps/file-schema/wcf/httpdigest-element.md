---
title: <httpDigest> 項目
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 328411a429cd42927a190c6805a1f5e2b3555ea1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448448"
---
# <a name="httpdigest-element"></a><span data-ttu-id="84f9f-102">\<HTTPDigest > 元素</span><span class="sxs-lookup"><span data-stu-id="84f9f-102">\<httpDigest> Element</span></span>
<span data-ttu-id="84f9f-103">指定對服務驗證用戶端時，所使用的摘要式類型認證。</span><span class="sxs-lookup"><span data-stu-id="84f9f-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="84f9f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84f9f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84f9f-105">&nbsp;&nbsp;[ **\<system.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="84f9f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="84f9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84f9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="84f9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84f9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="84f9f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84f9f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="84f9f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="84f9f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="84f9f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**HTTPDigest >**</span><span class="sxs-lookup"><span data-stu-id="84f9f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f9f-111">語法</span><span class="sxs-lookup"><span data-stu-id="84f9f-111">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84f9f-112">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="84f9f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="84f9f-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84f9f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84f9f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="84f9f-114">Attributes</span></span>  
  
|<span data-ttu-id="84f9f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="84f9f-115">Attribute</span></span>|<span data-ttu-id="84f9f-116">描述</span><span class="sxs-lookup"><span data-stu-id="84f9f-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="84f9f-117">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="84f9f-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="84f9f-118">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="84f9f-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="84f9f-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="84f9f-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="84f9f-120">-識別：伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="84f9f-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="84f9f-121">-模擬：伺服器可以在本機系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="84f9f-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="84f9f-122">-委派：伺服器可以在遠端系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="84f9f-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="84f9f-123">-Anonymous：伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="84f9f-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="84f9f-124">-None：未指派模擬層級。</span><span class="sxs-lookup"><span data-stu-id="84f9f-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="84f9f-125">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="84f9f-125">The default is Identification.</span></span> <span data-ttu-id="84f9f-126">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="84f9f-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84f9f-127">子元素</span><span class="sxs-lookup"><span data-stu-id="84f9f-127">Child Elements</span></span>  
 <span data-ttu-id="84f9f-128">None</span><span class="sxs-lookup"><span data-stu-id="84f9f-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84f9f-129">父項目</span><span class="sxs-lookup"><span data-stu-id="84f9f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="84f9f-130">元素</span><span class="sxs-lookup"><span data-stu-id="84f9f-130">Element</span></span>|<span data-ttu-id="84f9f-131">描述</span><span class="sxs-lookup"><span data-stu-id="84f9f-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84f9f-132">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="84f9f-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="84f9f-133">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="84f9f-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84f9f-134">備註</span><span class="sxs-lookup"><span data-stu-id="84f9f-134">Remarks</span></span>  
 <span data-ttu-id="84f9f-135">摘要是指使用演算法和一組輸入所決定的雜湊。</span><span class="sxs-lookup"><span data-stu-id="84f9f-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="84f9f-136">驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="84f9f-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="84f9f-137">用戶端可計算雜湊，並將它傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="84f9f-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="84f9f-138">服務也會計算雜湊並比較兩者的值。</span><span class="sxs-lookup"><span data-stu-id="84f9f-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="84f9f-139">比對會驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="84f9f-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="84f9f-140">此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。</span><span class="sxs-lookup"><span data-stu-id="84f9f-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="84f9f-141">如需詳細資訊，請參閱[IIS 6.0 中的摘要式驗證](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="84f9f-141">For more information, see [Digest Authentication in IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f9f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f9f-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="84f9f-143">安全性行為</span><span class="sxs-lookup"><span data-stu-id="84f9f-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="84f9f-144">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="84f9f-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="84f9f-145">使用憑證</span><span class="sxs-lookup"><span data-stu-id="84f9f-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="84f9f-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="84f9f-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
