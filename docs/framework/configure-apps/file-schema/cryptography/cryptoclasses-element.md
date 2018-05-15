---
title: '&lt;cryptoClasses&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2706d2466bd7139d8a6c20802c32dd19f64abb40
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcryptoclassesgt-element"></a><span data-ttu-id="96902-102">&lt;cryptoClasses&gt;項目</span><span class="sxs-lookup"><span data-stu-id="96902-102">&lt;cryptoClasses&gt; Element</span></span>
<span data-ttu-id="96902-103">包含密碼編譯類別清單，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="96902-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="96902-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="96902-104">\<configuration></span></span>  
<span data-ttu-id="96902-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="96902-105">\<mscorlib></span></span>  
<span data-ttu-id="96902-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="96902-106">\<cryptographySettings></span></span>  
<span data-ttu-id="96902-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="96902-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="96902-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="96902-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96902-109">語法</span><span class="sxs-lookup"><span data-stu-id="96902-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96902-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96902-110">Attributes and Elements</span></span>  
 <span data-ttu-id="96902-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="96902-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96902-112">屬性</span><span class="sxs-lookup"><span data-stu-id="96902-112">Attributes</span></span>  
 <span data-ttu-id="96902-113">無。</span><span class="sxs-lookup"><span data-stu-id="96902-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96902-114">子項目</span><span class="sxs-lookup"><span data-stu-id="96902-114">Child Elements</span></span>  
  
|<span data-ttu-id="96902-115">項目</span><span class="sxs-lookup"><span data-stu-id="96902-115">Element</span></span>|<span data-ttu-id="96902-116">描述</span><span class="sxs-lookup"><span data-stu-id="96902-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96902-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="96902-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="96902-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="96902-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96902-119">父項目</span><span class="sxs-lookup"><span data-stu-id="96902-119">Parent Elements</span></span>  
  
|<span data-ttu-id="96902-120">項目</span><span class="sxs-lookup"><span data-stu-id="96902-120">Element</span></span>|<span data-ttu-id="96902-121">描述</span><span class="sxs-lookup"><span data-stu-id="96902-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="96902-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="96902-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="96902-123">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="96902-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="96902-124">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="96902-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="96902-125">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="96902-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96902-126">範例</span><span class="sxs-lookup"><span data-stu-id="96902-126">Example</span></span>  
 <span data-ttu-id="96902-127">下列範例示範如何使用 **\<cryptoClass >** 項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="96902-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="96902-128">您接著可以將字串"RSA"至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法以傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="96902-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96902-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96902-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="96902-130">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="96902-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="96902-131">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="96902-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="96902-132">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="96902-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="96902-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="96902-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [<span data-ttu-id="96902-134">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="96902-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
