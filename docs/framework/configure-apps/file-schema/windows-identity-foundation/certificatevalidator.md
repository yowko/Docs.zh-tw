---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152784"
---
# <a name="certificatevalidator"></a><span data-ttu-id="c74fc-101">\<證書驗證器></span><span class="sxs-lookup"><span data-stu-id="c74fc-101">\<certificateValidator></span></span>
<span data-ttu-id="c74fc-102">指定證書驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="c74fc-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="c74fc-103">`certificateValidationMode`[僅當\<證書驗證>](certificatevalidation.md)元素的屬性設置為"自訂"時，才使用此類型。</span><span class="sxs-lookup"><span data-stu-id="c74fc-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="c74fc-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c74fc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c74fc-105">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c74fc-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c74fc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c74fc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c74fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<證書驗證>**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="c74fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="c74fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<證書驗證器>**</span><span class="sxs-lookup"><span data-stu-id="c74fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c74fc-109">語法</span><span class="sxs-lookup"><span data-stu-id="c74fc-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c74fc-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c74fc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c74fc-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c74fc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c74fc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c74fc-112">Attributes</span></span>  
  
|<span data-ttu-id="c74fc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c74fc-113">Attribute</span></span>|<span data-ttu-id="c74fc-114">描述</span><span class="sxs-lookup"><span data-stu-id="c74fc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c74fc-115">type</span><span class="sxs-lookup"><span data-stu-id="c74fc-115">type</span></span>|<span data-ttu-id="c74fc-116">指定派生自類的<xref:System.IdentityModel.Selectors.X509CertificateValidator>自訂類型。</span><span class="sxs-lookup"><span data-stu-id="c74fc-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="c74fc-117">`certificateValidationMode`[將\<證書驗證>](certificatevalidation.md)元素的屬性設置為"自訂"以使用此類型。</span><span class="sxs-lookup"><span data-stu-id="c74fc-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="c74fc-118">有關如何指定屬性的詳細資訊，`type`請參閱[自訂類型引用](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c74fc-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="c74fc-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c74fc-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c74fc-120">子元素</span><span class="sxs-lookup"><span data-stu-id="c74fc-120">Child Elements</span></span>  
 <span data-ttu-id="c74fc-121">None</span><span class="sxs-lookup"><span data-stu-id="c74fc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c74fc-122">父項目</span><span class="sxs-lookup"><span data-stu-id="c74fc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c74fc-123">元素</span><span class="sxs-lookup"><span data-stu-id="c74fc-123">Element</span></span>|<span data-ttu-id="c74fc-124">描述</span><span class="sxs-lookup"><span data-stu-id="c74fc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c74fc-125">\<證書驗證></span><span class="sxs-lookup"><span data-stu-id="c74fc-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="c74fc-126">控制權杖處理常式用於驗證憑證的設置。</span><span class="sxs-lookup"><span data-stu-id="c74fc-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c74fc-127">範例</span><span class="sxs-lookup"><span data-stu-id="c74fc-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
