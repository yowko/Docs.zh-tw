---
title: <secureConversationAuthentication> 的 <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399927"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="e6bda-102">\<n > 的\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e6bda-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="e6bda-103">指定安全對話服務的設定。</span><span class="sxs-lookup"><span data-stu-id="e6bda-103">Specifies the settings for a secure conversation service.</span></span>  
  
<span data-ttu-id="e6bda-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6bda-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6bda-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e6bda-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6bda-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6bda-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e6bda-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6bda-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="e6bda-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6bda-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="e6bda-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e6bda-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="e6bda-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<secureConversationAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="e6bda-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6bda-111">語法</span><span class="sxs-lookup"><span data-stu-id="e6bda-111">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6bda-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6bda-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e6bda-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e6bda-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6bda-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e6bda-114">Attributes</span></span>  
  
|<span data-ttu-id="e6bda-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e6bda-115">Attribute</span></span>|<span data-ttu-id="e6bda-116">描述</span><span class="sxs-lookup"><span data-stu-id="e6bda-116">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="e6bda-117">字串，指定要使用的 <xref:System.ServiceModel.Security.SecurityStateEncoder> 型別。</span><span class="sxs-lookup"><span data-stu-id="e6bda-117">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6bda-118">子元素</span><span class="sxs-lookup"><span data-stu-id="e6bda-118">Child Elements</span></span>  
 <span data-ttu-id="e6bda-119">無。</span><span class="sxs-lookup"><span data-stu-id="e6bda-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6bda-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e6bda-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e6bda-121">項目</span><span class="sxs-lookup"><span data-stu-id="e6bda-121">Element</span></span>|<span data-ttu-id="e6bda-122">描述</span><span class="sxs-lookup"><span data-stu-id="e6bda-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6bda-123">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e6bda-123">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="e6bda-124">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="e6bda-124">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6bda-125">備註</span><span class="sxs-lookup"><span data-stu-id="e6bda-125">Remarks</span></span>  
 <span data-ttu-id="e6bda-126">使用此組態項目指定安全性內容權杖 (SCT) Cookie 序列化的已知宣告型別清單，以及指定可編碼與確保 Cookie 資訊安全的編碼器。</span><span class="sxs-lookup"><span data-stu-id="e6bda-126">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="e6bda-127">如需 SCT 的詳細資訊，請參閱<xref:System.ServiceModel.Security.SecureConversationServiceCredential>。</span><span class="sxs-lookup"><span data-stu-id="e6bda-127">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6bda-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6bda-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
