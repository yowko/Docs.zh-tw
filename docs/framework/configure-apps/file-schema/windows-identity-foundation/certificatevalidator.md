---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74dd0827ee073d57c82729ec1e6a9a672aa1f404
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="0e354-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="0e354-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="0e354-103">指定自訂憑證驗證類型。</span><span class="sxs-lookup"><span data-stu-id="0e354-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="0e354-104">此類型只使用`certificateValidationMode`屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="0e354-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="0e354-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="0e354-105">\<system.identityModel></span></span>  
<span data-ttu-id="0e354-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0e354-106">\<identityConfiguration></span></span>  
<span data-ttu-id="0e354-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="0e354-107">\<certificateValidation></span></span>  
<span data-ttu-id="0e354-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="0e354-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e354-109">語法</span><span class="sxs-lookup"><span data-stu-id="0e354-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e354-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0e354-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e354-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0e354-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e354-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0e354-112">Attributes</span></span>  
  
|<span data-ttu-id="0e354-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0e354-113">Attribute</span></span>|<span data-ttu-id="0e354-114">描述</span><span class="sxs-lookup"><span data-stu-id="0e354-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e354-115">類型</span><span class="sxs-lookup"><span data-stu-id="0e354-115">type</span></span>|<span data-ttu-id="0e354-116">指定自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>類別。</span><span class="sxs-lookup"><span data-stu-id="0e354-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="0e354-117">設定`certificateValidationMode`屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)為"Custom"，使用此類型的項目。</span><span class="sxs-lookup"><span data-stu-id="0e354-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="0e354-118">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0e354-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="0e354-119">選擇項。</span><span class="sxs-lookup"><span data-stu-id="0e354-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e354-120">子元素</span><span class="sxs-lookup"><span data-stu-id="0e354-120">Child Elements</span></span>  
 <span data-ttu-id="0e354-121">無</span><span class="sxs-lookup"><span data-stu-id="0e354-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e354-122">父項目</span><span class="sxs-lookup"><span data-stu-id="0e354-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0e354-123">項目</span><span class="sxs-lookup"><span data-stu-id="0e354-123">Element</span></span>|<span data-ttu-id="0e354-124">說明</span><span class="sxs-lookup"><span data-stu-id="0e354-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e354-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="0e354-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="0e354-126">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="0e354-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e354-127">範例</span><span class="sxs-lookup"><span data-stu-id="0e354-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
