---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941909"
---
# <a name="certificatevalidator"></a><span data-ttu-id="93d26-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="93d26-101">\<certificateValidator></span></span>
<span data-ttu-id="93d26-102">指定憑證驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="93d26-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="93d26-103">只有當`certificateValidationMode` [ \<certificateValidation >](certificatevalidation.md)元素的屬性設定為 "Custom" 時, 才會使用此類型。</span><span class="sxs-lookup"><span data-stu-id="93d26-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="93d26-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="93d26-104">\<system.identityModel></span></span>  
<span data-ttu-id="93d26-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="93d26-105">\<identityConfiguration></span></span>  
<span data-ttu-id="93d26-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="93d26-106">\<certificateValidation></span></span>  
<span data-ttu-id="93d26-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="93d26-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d26-108">語法</span><span class="sxs-lookup"><span data-stu-id="93d26-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93d26-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93d26-109">Attributes and Elements</span></span>  
 <span data-ttu-id="93d26-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="93d26-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93d26-111">屬性</span><span class="sxs-lookup"><span data-stu-id="93d26-111">Attributes</span></span>  
  
|<span data-ttu-id="93d26-112">屬性</span><span class="sxs-lookup"><span data-stu-id="93d26-112">Attribute</span></span>|<span data-ttu-id="93d26-113">說明</span><span class="sxs-lookup"><span data-stu-id="93d26-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93d26-114">型別</span><span class="sxs-lookup"><span data-stu-id="93d26-114">type</span></span>|<span data-ttu-id="93d26-115">指定衍生<xref:System.IdentityModel.Selectors.X509CertificateValidator>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="93d26-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="93d26-116">將 certificateValidation > 元素的`certificateValidationMode`屬性[設定為 "Custom", 以\<](certificatevalidation.md)使用此類型。</span><span class="sxs-lookup"><span data-stu-id="93d26-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="93d26-117">如需如何指定屬性的`type`詳細資訊, 請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="93d26-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="93d26-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="93d26-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93d26-119">子元素</span><span class="sxs-lookup"><span data-stu-id="93d26-119">Child Elements</span></span>  
 <span data-ttu-id="93d26-120">無</span><span class="sxs-lookup"><span data-stu-id="93d26-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93d26-121">父項目</span><span class="sxs-lookup"><span data-stu-id="93d26-121">Parent Elements</span></span>  
  
|<span data-ttu-id="93d26-122">項目</span><span class="sxs-lookup"><span data-stu-id="93d26-122">Element</span></span>|<span data-ttu-id="93d26-123">描述</span><span class="sxs-lookup"><span data-stu-id="93d26-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93d26-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="93d26-124">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="93d26-125">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="93d26-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="93d26-126">範例</span><span class="sxs-lookup"><span data-stu-id="93d26-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
