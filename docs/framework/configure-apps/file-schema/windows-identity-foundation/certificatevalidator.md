---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 30f81dd5948a7d366c1116cffd347c85a396f5ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252117"
---
# <a name="certificatevalidator"></a><span data-ttu-id="89955-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="89955-101">\<certificateValidator></span></span>
<span data-ttu-id="89955-102">指定憑證驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="89955-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="89955-103">只有當`certificateValidationMode` [ \<certificateValidation >](certificatevalidation.md)元素的屬性設定為 "Custom" 時，才會使用此類型。</span><span class="sxs-lookup"><span data-stu-id="89955-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="89955-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89955-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89955-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="89955-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="89955-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="89955-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="89955-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<certificateValidation >** ](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="89955-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="89955-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidator >**</span><span class="sxs-lookup"><span data-stu-id="89955-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89955-109">語法</span><span class="sxs-lookup"><span data-stu-id="89955-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89955-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89955-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89955-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="89955-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89955-112">屬性</span><span class="sxs-lookup"><span data-stu-id="89955-112">Attributes</span></span>  
  
|<span data-ttu-id="89955-113">屬性</span><span class="sxs-lookup"><span data-stu-id="89955-113">Attribute</span></span>|<span data-ttu-id="89955-114">說明</span><span class="sxs-lookup"><span data-stu-id="89955-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89955-115">型別</span><span class="sxs-lookup"><span data-stu-id="89955-115">type</span></span>|<span data-ttu-id="89955-116">指定衍生<xref:System.IdentityModel.Selectors.X509CertificateValidator>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="89955-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="89955-117">將 certificateValidation > 元素的`certificateValidationMode`屬性[設定為 "Custom"，以\<](certificatevalidation.md)使用此類型。</span><span class="sxs-lookup"><span data-stu-id="89955-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="89955-118">如需如何指定屬性的`type`詳細資訊，請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="89955-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="89955-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="89955-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89955-120">子元素</span><span class="sxs-lookup"><span data-stu-id="89955-120">Child Elements</span></span>  
 <span data-ttu-id="89955-121">無</span><span class="sxs-lookup"><span data-stu-id="89955-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89955-122">父項目</span><span class="sxs-lookup"><span data-stu-id="89955-122">Parent Elements</span></span>  
  
|<span data-ttu-id="89955-123">項目</span><span class="sxs-lookup"><span data-stu-id="89955-123">Element</span></span>|<span data-ttu-id="89955-124">描述</span><span class="sxs-lookup"><span data-stu-id="89955-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89955-125">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="89955-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="89955-126">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="89955-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89955-127">範例</span><span class="sxs-lookup"><span data-stu-id="89955-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
