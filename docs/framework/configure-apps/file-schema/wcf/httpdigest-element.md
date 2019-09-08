---
title: <httpDigest> 項目
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 121df39c7e4ce4de5c1f0ef87921f6269d7cc1c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785822"
---
# <a name="httpdigest-element"></a><span data-ttu-id="a854d-102">\<HTTPDigest > 元素</span><span class="sxs-lookup"><span data-stu-id="a854d-102">\<httpDigest> Element</span></span>
<span data-ttu-id="a854d-103">指定對服務驗證用戶端時，所使用的摘要式類型認證。</span><span class="sxs-lookup"><span data-stu-id="a854d-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="a854d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a854d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a854d-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a854d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a854d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a854d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a854d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a854d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a854d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a854d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a854d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a854d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="a854d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<HTTPDigest >**</span><span class="sxs-lookup"><span data-stu-id="a854d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a854d-111">語法</span><span class="sxs-lookup"><span data-stu-id="a854d-111">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a854d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a854d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a854d-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a854d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a854d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a854d-114">Attributes</span></span>  
  
|<span data-ttu-id="a854d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="a854d-115">Attribute</span></span>|<span data-ttu-id="a854d-116">描述</span><span class="sxs-lookup"><span data-stu-id="a854d-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="a854d-117">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="a854d-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="a854d-118">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="a854d-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="a854d-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a854d-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a854d-120">發現伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="a854d-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="a854d-121">申請伺服器可以在本機系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="a854d-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="a854d-122">其它伺服器可以在遠端系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="a854d-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="a854d-123">匿名伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="a854d-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="a854d-124">無未指派模擬層級。</span><span class="sxs-lookup"><span data-stu-id="a854d-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="a854d-125">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="a854d-125">The default is Identification.</span></span> <span data-ttu-id="a854d-126">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="a854d-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a854d-127">子元素</span><span class="sxs-lookup"><span data-stu-id="a854d-127">Child Elements</span></span>  
 <span data-ttu-id="a854d-128">無</span><span class="sxs-lookup"><span data-stu-id="a854d-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a854d-129">父項目</span><span class="sxs-lookup"><span data-stu-id="a854d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a854d-130">項目</span><span class="sxs-lookup"><span data-stu-id="a854d-130">Element</span></span>|<span data-ttu-id="a854d-131">說明</span><span class="sxs-lookup"><span data-stu-id="a854d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a854d-132">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a854d-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="a854d-133">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="a854d-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a854d-134">備註</span><span class="sxs-lookup"><span data-stu-id="a854d-134">Remarks</span></span>  
 <span data-ttu-id="a854d-135">摘要是指使用演算法和一組輸入所決定的雜湊。</span><span class="sxs-lookup"><span data-stu-id="a854d-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="a854d-136">驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="a854d-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="a854d-137">用戶端可計算雜湊，並將它傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="a854d-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="a854d-138">服務也會計算雜湊並比較兩者的值。</span><span class="sxs-lookup"><span data-stu-id="a854d-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="a854d-139">比對會驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="a854d-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="a854d-140">此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。</span><span class="sxs-lookup"><span data-stu-id="a854d-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="a854d-141">如需詳細資訊，請參閱[IIS 6.0 中的摘要式驗證](https://go.microsoft.com/fwlink/?LinkId=88443)。</span><span class="sxs-lookup"><span data-stu-id="a854d-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a854d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a854d-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="a854d-143">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a854d-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a854d-144">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="a854d-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a854d-145">使用憑證</span><span class="sxs-lookup"><span data-stu-id="a854d-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a854d-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a854d-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
