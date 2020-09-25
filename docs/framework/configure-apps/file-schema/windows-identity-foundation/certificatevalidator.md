---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 8476600769b6099bb885566de4c908c78a2dbbda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201367"
---
# \<certificateValidator>

<span data-ttu-id="c204f-101">指定憑證驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="c204f-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="c204f-102">只有當 `certificateValidationMode` 元素的屬性 [\<certificateValidation>](certificatevalidation.md) 設為 "Custom" 時，才會使用這個型別。</span><span class="sxs-lookup"><span data-stu-id="c204f-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="c204f-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c204f-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c204f-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c204f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c204f-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c204f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c204f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="c204f-106">Attributes</span></span>  
  
|<span data-ttu-id="c204f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c204f-107">Attribute</span></span>|<span data-ttu-id="c204f-108">描述</span><span class="sxs-lookup"><span data-stu-id="c204f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c204f-109">type</span><span class="sxs-lookup"><span data-stu-id="c204f-109">type</span></span>|<span data-ttu-id="c204f-110">指定衍生自類別的自訂型別 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="c204f-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="c204f-111">將專案的 `certificateValidationMode` 屬性設定 [\<certificateValidation>](certificatevalidation.md) 為 [自訂]，以使用此類型。</span><span class="sxs-lookup"><span data-stu-id="c204f-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="c204f-112">如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c204f-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="c204f-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c204f-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c204f-114">子元素</span><span class="sxs-lookup"><span data-stu-id="c204f-114">Child Elements</span></span>  

 <span data-ttu-id="c204f-115">無</span><span class="sxs-lookup"><span data-stu-id="c204f-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c204f-116">父項目</span><span class="sxs-lookup"><span data-stu-id="c204f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c204f-117">項目</span><span class="sxs-lookup"><span data-stu-id="c204f-117">Element</span></span>|<span data-ttu-id="c204f-118">描述</span><span class="sxs-lookup"><span data-stu-id="c204f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="c204f-119">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="c204f-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c204f-120">範例</span><span class="sxs-lookup"><span data-stu-id="c204f-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
