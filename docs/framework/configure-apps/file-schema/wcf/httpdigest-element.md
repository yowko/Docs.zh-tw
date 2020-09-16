---
title: <httpDigest> 項目
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 0ffaba218d31a77407c598f8b7fa0260daa4e39c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556898"
---
# <a name="httpdigest-element"></a><span data-ttu-id="3a05b-102">\<httpDigest> 項目</span><span class="sxs-lookup"><span data-stu-id="3a05b-102">\<httpDigest> Element</span></span>
<span data-ttu-id="3a05b-103">指定對服務驗證用戶端時，所使用的摘要式類型認證。</span><span class="sxs-lookup"><span data-stu-id="3a05b-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="3a05b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a05b-104">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a05b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a05b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3a05b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3a05b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a05b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3a05b-107">Attributes</span></span>  
  
|<span data-ttu-id="3a05b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3a05b-108">Attribute</span></span>|<span data-ttu-id="3a05b-109">描述</span><span class="sxs-lookup"><span data-stu-id="3a05b-109">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="3a05b-110">設定用戶端與伺服器通訊的模擬喜好設定。</span><span class="sxs-lookup"><span data-stu-id="3a05b-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="3a05b-111">用戶端選取的模擬模式不會在伺服器上強制使用。</span><span class="sxs-lookup"><span data-stu-id="3a05b-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="3a05b-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3a05b-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3a05b-113">-識別：伺服器可以取得用戶端的身分識別和許可權，但無法模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="3a05b-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="3a05b-114">-模擬：伺服器可以在本機系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="3a05b-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="3a05b-115">-委派：伺服器可以在遠端系統上模擬用戶端的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="3a05b-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="3a05b-116">-Anonymous：伺服器無法模擬或識別用戶端。</span><span class="sxs-lookup"><span data-stu-id="3a05b-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="3a05b-117">-無：未指派模擬等級。</span><span class="sxs-lookup"><span data-stu-id="3a05b-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="3a05b-118">預設為 Identification。</span><span class="sxs-lookup"><span data-stu-id="3a05b-118">The default is Identification.</span></span> <span data-ttu-id="3a05b-119">此屬性的型別為 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="3a05b-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a05b-120">子元素</span><span class="sxs-lookup"><span data-stu-id="3a05b-120">Child Elements</span></span>  
 <span data-ttu-id="3a05b-121">None</span><span class="sxs-lookup"><span data-stu-id="3a05b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a05b-122">父項目</span><span class="sxs-lookup"><span data-stu-id="3a05b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3a05b-123">項目</span><span class="sxs-lookup"><span data-stu-id="3a05b-123">Element</span></span>|<span data-ttu-id="3a05b-124">描述</span><span class="sxs-lookup"><span data-stu-id="3a05b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="3a05b-125">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="3a05b-125">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a05b-126">備註</span><span class="sxs-lookup"><span data-stu-id="3a05b-126">Remarks</span></span>  
 <span data-ttu-id="3a05b-127">摘要是指使用演算法和一組輸入所決定的雜湊。</span><span class="sxs-lookup"><span data-stu-id="3a05b-127">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="3a05b-128">驗證者和被驗證者一致同意某個演算法，並交換做為輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="3a05b-128">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="3a05b-129">用戶端可計算雜湊，並將它傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="3a05b-129">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="3a05b-130">服務也會計算雜湊並比較兩者的值。</span><span class="sxs-lookup"><span data-stu-id="3a05b-130">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="3a05b-131">比對會驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="3a05b-131">A match validates the client.</span></span>  
  
 <span data-ttu-id="3a05b-132">此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。</span><span class="sxs-lookup"><span data-stu-id="3a05b-132">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="3a05b-133">如需詳細資訊，請參閱 [IIS 6.0 中的摘要式驗證](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="3a05b-133">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a05b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a05b-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="3a05b-135">安全性行為</span><span class="sxs-lookup"><span data-stu-id="3a05b-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3a05b-136">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="3a05b-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="3a05b-137">使用憑證</span><span class="sxs-lookup"><span data-stu-id="3a05b-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3a05b-138">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="3a05b-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
