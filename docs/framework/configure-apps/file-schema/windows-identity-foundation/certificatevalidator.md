---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849694"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="73061-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="73061-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="73061-103">指定自訂憑證驗證類型。</span><span class="sxs-lookup"><span data-stu-id="73061-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="73061-104">只有，會使用這個型別`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="73061-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="73061-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="73061-105">\<system.identityModel></span></span>  
<span data-ttu-id="73061-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="73061-106">\<identityConfiguration></span></span>  
<span data-ttu-id="73061-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="73061-107">\<certificateValidation></span></span>  
<span data-ttu-id="73061-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="73061-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73061-109">語法</span><span class="sxs-lookup"><span data-stu-id="73061-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73061-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73061-110">Attributes and Elements</span></span>  
 <span data-ttu-id="73061-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73061-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73061-112">屬性</span><span class="sxs-lookup"><span data-stu-id="73061-112">Attributes</span></span>  
  
|<span data-ttu-id="73061-113">屬性</span><span class="sxs-lookup"><span data-stu-id="73061-113">Attribute</span></span>|<span data-ttu-id="73061-114">描述</span><span class="sxs-lookup"><span data-stu-id="73061-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73061-115">類型</span><span class="sxs-lookup"><span data-stu-id="73061-115">type</span></span>|<span data-ttu-id="73061-116">指定自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>類別。</span><span class="sxs-lookup"><span data-stu-id="73061-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="73061-117">設定`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)為"Custom"，使用此類型的項目。</span><span class="sxs-lookup"><span data-stu-id="73061-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="73061-118">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="73061-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="73061-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="73061-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73061-120">子元素</span><span class="sxs-lookup"><span data-stu-id="73061-120">Child Elements</span></span>  
 <span data-ttu-id="73061-121">無</span><span class="sxs-lookup"><span data-stu-id="73061-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73061-122">父項目</span><span class="sxs-lookup"><span data-stu-id="73061-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73061-123">項目</span><span class="sxs-lookup"><span data-stu-id="73061-123">Element</span></span>|<span data-ttu-id="73061-124">描述</span><span class="sxs-lookup"><span data-stu-id="73061-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73061-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="73061-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="73061-126">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="73061-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73061-127">範例</span><span class="sxs-lookup"><span data-stu-id="73061-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
