---
title: <secureConversationAuthentication> 的 <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399927"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="34b81-102">\<secureConversationAuthentication> 的 \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="34b81-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="34b81-103">指定安全對話服務的設定。</span><span class="sxs-lookup"><span data-stu-id="34b81-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="34b81-104">語法</span><span class="sxs-lookup"><span data-stu-id="34b81-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34b81-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="34b81-105">Attributes and Elements</span></span>  
 <span data-ttu-id="34b81-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="34b81-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34b81-107">屬性</span><span class="sxs-lookup"><span data-stu-id="34b81-107">Attributes</span></span>  
  
|<span data-ttu-id="34b81-108">屬性</span><span class="sxs-lookup"><span data-stu-id="34b81-108">Attribute</span></span>|<span data-ttu-id="34b81-109">描述</span><span class="sxs-lookup"><span data-stu-id="34b81-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="34b81-110">字串，指定要使用的 <xref:System.ServiceModel.Security.SecurityStateEncoder> 型別。</span><span class="sxs-lookup"><span data-stu-id="34b81-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34b81-111">子元素</span><span class="sxs-lookup"><span data-stu-id="34b81-111">Child Elements</span></span>  
 <span data-ttu-id="34b81-112">無。</span><span class="sxs-lookup"><span data-stu-id="34b81-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34b81-113">父項目</span><span class="sxs-lookup"><span data-stu-id="34b81-113">Parent Elements</span></span>  
  
|<span data-ttu-id="34b81-114">元素</span><span class="sxs-lookup"><span data-stu-id="34b81-114">Element</span></span>|<span data-ttu-id="34b81-115">描述</span><span class="sxs-lookup"><span data-stu-id="34b81-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="34b81-116">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="34b81-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34b81-117">備註</span><span class="sxs-lookup"><span data-stu-id="34b81-117">Remarks</span></span>  
 <span data-ttu-id="34b81-118">使用此組態項目指定安全性內容權杖 (SCT) Cookie 序列化的已知宣告型別清單，以及指定可編碼與確保 Cookie 資訊安全的編碼器。</span><span class="sxs-lookup"><span data-stu-id="34b81-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="34b81-119">如需 SCT 的詳細資訊，請參閱<xref:System.ServiceModel.Security.SecureConversationServiceCredential>。</span><span class="sxs-lookup"><span data-stu-id="34b81-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b81-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b81-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
