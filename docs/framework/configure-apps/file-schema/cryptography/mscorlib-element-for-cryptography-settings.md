---
title: '&lt;mscorlib&gt;密碼編譯設定的項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b5da49ff22cfa6bd1c3e4d574865eb5e61dc73fb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205956"
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="e3e3d-102">&lt;mscorlib&gt;密碼編譯設定的項目</span><span class="sxs-lookup"><span data-stu-id="e3e3d-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="e3e3d-103">包含[ \<cryptographySettings > 項目](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="e3e3d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e3e3d-104">\<configuration></span></span>  
<span data-ttu-id="e3e3d-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="e3e3d-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e3d-106">語法</span><span class="sxs-lookup"><span data-stu-id="e3e3d-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3e3d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e3e3d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e3e3d-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3e3d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e3e3d-109">Attributes</span></span>  
 <span data-ttu-id="e3e3d-110">無。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3e3d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e3e3d-111">Child Elements</span></span>  
  
|<span data-ttu-id="e3e3d-112">項目</span><span class="sxs-lookup"><span data-stu-id="e3e3d-112">Element</span></span>|<span data-ttu-id="e3e3d-113">描述</span><span class="sxs-lookup"><span data-stu-id="e3e3d-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="e3e3d-114">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3e3d-115">父項目</span><span class="sxs-lookup"><span data-stu-id="e3e3d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e3e3d-116">項目</span><span class="sxs-lookup"><span data-stu-id="e3e3d-116">Element</span></span>|<span data-ttu-id="e3e3d-117">描述</span><span class="sxs-lookup"><span data-stu-id="e3e3d-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e3e3d-118">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e3e3d-119">範例</span><span class="sxs-lookup"><span data-stu-id="e3e3d-119">Example</span></span>  
 <span data-ttu-id="e3e3d-120">下列範例示範如何使用 **\<mscorlib >** 項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e3e3d-121">然後，您可以將字串"RSA"傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法來傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="e3e3d-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3e3d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3e3d-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="e3e3d-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="e3e3d-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e3e3d-124">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e3e3d-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="e3e3d-125">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="e3e3d-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="e3e3d-126">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="e3e3d-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
