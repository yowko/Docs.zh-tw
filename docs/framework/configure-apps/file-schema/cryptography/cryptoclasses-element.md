---
title: "&lt;cryptoClasses&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7ed25fa1a2bdedc410fccf48802742766287c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcryptoclassesgt-element"></a><span data-ttu-id="117f8-102">&lt;cryptoClasses&gt;項目</span><span class="sxs-lookup"><span data-stu-id="117f8-102">&lt;cryptoClasses&gt; Element</span></span>
<span data-ttu-id="117f8-103">包含密碼編譯類別清單，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="117f8-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="117f8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="117f8-104">\<configuration></span></span>  
<span data-ttu-id="117f8-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="117f8-105">\<mscorlib></span></span>  
<span data-ttu-id="117f8-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="117f8-106">\<cryptographySettings></span></span>  
<span data-ttu-id="117f8-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="117f8-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="117f8-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="117f8-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="117f8-109">語法</span><span class="sxs-lookup"><span data-stu-id="117f8-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="117f8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="117f8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="117f8-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="117f8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="117f8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="117f8-112">Attributes</span></span>  
 <span data-ttu-id="117f8-113">無。</span><span class="sxs-lookup"><span data-stu-id="117f8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="117f8-114">子項目</span><span class="sxs-lookup"><span data-stu-id="117f8-114">Child Elements</span></span>  
  
|<span data-ttu-id="117f8-115">項目</span><span class="sxs-lookup"><span data-stu-id="117f8-115">Element</span></span>|<span data-ttu-id="117f8-116">說明</span><span class="sxs-lookup"><span data-stu-id="117f8-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="117f8-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="117f8-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="117f8-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="117f8-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="117f8-119">父項目</span><span class="sxs-lookup"><span data-stu-id="117f8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="117f8-120">項目</span><span class="sxs-lookup"><span data-stu-id="117f8-120">Element</span></span>|<span data-ttu-id="117f8-121">描述</span><span class="sxs-lookup"><span data-stu-id="117f8-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="117f8-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="117f8-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="117f8-123">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="117f8-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="117f8-124">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="117f8-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="117f8-125">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="117f8-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="117f8-126">範例</span><span class="sxs-lookup"><span data-stu-id="117f8-126">Example</span></span>  
 <span data-ttu-id="117f8-127">下列範例示範如何使用 **\<cryptoClass >**項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="117f8-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="117f8-128">您接著可以將字串"RSA"至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法以傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="117f8-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="117f8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="117f8-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="117f8-130">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="117f8-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="117f8-131">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="117f8-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="117f8-132">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="117f8-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="117f8-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="117f8-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [<span data-ttu-id="117f8-134">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="117f8-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
