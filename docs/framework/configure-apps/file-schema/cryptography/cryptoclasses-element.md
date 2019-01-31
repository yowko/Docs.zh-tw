---
title: <cryptoClasses> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: aa649a0ea83279a1b2bdb2dff33794002b8a6b7d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274062"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="39e1e-102">\<cryptoClasses > 項目</span><span class="sxs-lookup"><span data-stu-id="39e1e-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="39e1e-103">包含密碼編譯類別清單，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="39e1e-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="39e1e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="39e1e-104">\<configuration></span></span>  
<span data-ttu-id="39e1e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="39e1e-105">\<mscorlib></span></span>  
<span data-ttu-id="39e1e-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="39e1e-106">\<cryptographySettings></span></span>  
<span data-ttu-id="39e1e-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="39e1e-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="39e1e-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="39e1e-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e1e-109">語法</span><span class="sxs-lookup"><span data-stu-id="39e1e-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39e1e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="39e1e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39e1e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="39e1e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39e1e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="39e1e-112">Attributes</span></span>  
 <span data-ttu-id="39e1e-113">無。</span><span class="sxs-lookup"><span data-stu-id="39e1e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39e1e-114">子元素</span><span class="sxs-lookup"><span data-stu-id="39e1e-114">Child Elements</span></span>  
  
|<span data-ttu-id="39e1e-115">項目</span><span class="sxs-lookup"><span data-stu-id="39e1e-115">Element</span></span>|<span data-ttu-id="39e1e-116">描述</span><span class="sxs-lookup"><span data-stu-id="39e1e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39e1e-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="39e1e-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="39e1e-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="39e1e-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39e1e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="39e1e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="39e1e-120">項目</span><span class="sxs-lookup"><span data-stu-id="39e1e-120">Element</span></span>|<span data-ttu-id="39e1e-121">描述</span><span class="sxs-lookup"><span data-stu-id="39e1e-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39e1e-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="39e1e-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="39e1e-123">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="39e1e-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="39e1e-124">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="39e1e-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="39e1e-125">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="39e1e-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39e1e-126">範例</span><span class="sxs-lookup"><span data-stu-id="39e1e-126">Example</span></span>  
 <span data-ttu-id="39e1e-127">下列範例示範如何使用 **\<cryptoClass >** 項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="39e1e-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="39e1e-128">然後，您可以將字串"RSA"傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法來傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="39e1e-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39e1e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39e1e-129">See also</span></span>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="39e1e-130">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="39e1e-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="39e1e-131">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="39e1e-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="39e1e-132">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="39e1e-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="39e1e-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="39e1e-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="39e1e-134">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="39e1e-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
