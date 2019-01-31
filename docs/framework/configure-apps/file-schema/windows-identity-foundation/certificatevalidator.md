---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: df52212305e0865b8c03fdd49068cb7c7da4fa38
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277444"
---
# <a name="certificatevalidator"></a><span data-ttu-id="1acd2-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="1acd2-101">\<certificateValidator></span></span>
<span data-ttu-id="1acd2-102">指定自訂憑證驗證類型。</span><span class="sxs-lookup"><span data-stu-id="1acd2-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1acd2-103">只有，會使用這個型別`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="1acd2-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="1acd2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1acd2-104">\<system.identityModel></span></span>  
<span data-ttu-id="1acd2-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1acd2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1acd2-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="1acd2-106">\<certificateValidation></span></span>  
<span data-ttu-id="1acd2-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="1acd2-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1acd2-108">語法</span><span class="sxs-lookup"><span data-stu-id="1acd2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1acd2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1acd2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1acd2-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1acd2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1acd2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1acd2-111">Attributes</span></span>  
  
|<span data-ttu-id="1acd2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1acd2-112">Attribute</span></span>|<span data-ttu-id="1acd2-113">描述</span><span class="sxs-lookup"><span data-stu-id="1acd2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1acd2-114">類型</span><span class="sxs-lookup"><span data-stu-id="1acd2-114">type</span></span>|<span data-ttu-id="1acd2-115">指定自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>類別。</span><span class="sxs-lookup"><span data-stu-id="1acd2-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="1acd2-116">設定`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)為"Custom"，使用此類型的項目。</span><span class="sxs-lookup"><span data-stu-id="1acd2-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="1acd2-117">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1acd2-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="1acd2-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1acd2-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1acd2-119">子元素</span><span class="sxs-lookup"><span data-stu-id="1acd2-119">Child Elements</span></span>  
 <span data-ttu-id="1acd2-120">無</span><span class="sxs-lookup"><span data-stu-id="1acd2-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1acd2-121">父項目</span><span class="sxs-lookup"><span data-stu-id="1acd2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1acd2-122">項目</span><span class="sxs-lookup"><span data-stu-id="1acd2-122">Element</span></span>|<span data-ttu-id="1acd2-123">描述</span><span class="sxs-lookup"><span data-stu-id="1acd2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1acd2-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="1acd2-124">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="1acd2-125">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="1acd2-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1acd2-126">範例</span><span class="sxs-lookup"><span data-stu-id="1acd2-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
