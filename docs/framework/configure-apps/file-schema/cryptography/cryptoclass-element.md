---
title: '&lt;cryptoClass&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e74cc5fa99473562b158cd5068fb8bbaeb6a4a17
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196976"
---
# <a name="ltcryptoclassgt-element"></a><span data-ttu-id="5dee0-102">&lt;cryptoClass&gt;項目</span><span class="sxs-lookup"><span data-stu-id="5dee0-102">&lt;cryptoClass&gt; Element</span></span>
<span data-ttu-id="5dee0-103">包含密碼編譯類別，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="5dee0-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="5dee0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5dee0-104">\<configuration></span></span>  
<span data-ttu-id="5dee0-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="5dee0-105">\<mscorlib></span></span>  
<span data-ttu-id="5dee0-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="5dee0-106">\<cryptographySettings></span></span>  
<span data-ttu-id="5dee0-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="5dee0-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="5dee0-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="5dee0-108">\<cryptoClasses></span></span>  
<span data-ttu-id="5dee0-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="5dee0-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dee0-110">語法</span><span class="sxs-lookup"><span data-stu-id="5dee0-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dee0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5dee0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5dee0-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5dee0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dee0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5dee0-113">Attributes</span></span>  
  
|<span data-ttu-id="5dee0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5dee0-114">Attribute</span></span>|<span data-ttu-id="5dee0-115">描述</span><span class="sxs-lookup"><span data-stu-id="5dee0-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="5dee0-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5dee0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="5dee0-117">包含密碼編譯類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="5dee0-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="5dee0-118">您可以使用這個屬性來提供您的類別的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="5dee0-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="5dee0-119">您必須指定字串，符合指定的需求[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5dee0-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dee0-120">子元素</span><span class="sxs-lookup"><span data-stu-id="5dee0-120">Child Elements</span></span>  
 <span data-ttu-id="5dee0-121">無。</span><span class="sxs-lookup"><span data-stu-id="5dee0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5dee0-122">父項目</span><span class="sxs-lookup"><span data-stu-id="5dee0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5dee0-123">項目</span><span class="sxs-lookup"><span data-stu-id="5dee0-123">Element</span></span>|<span data-ttu-id="5dee0-124">描述</span><span class="sxs-lookup"><span data-stu-id="5dee0-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5dee0-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5dee0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="5dee0-126">包含密碼編譯類別清單，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="5dee0-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="5dee0-127">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="5dee0-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="5dee0-128">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="5dee0-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="5dee0-129">包含 [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="5dee0-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5dee0-130">範例</span><span class="sxs-lookup"><span data-stu-id="5dee0-130">Example</span></span>  
 <span data-ttu-id="5dee0-131">下列範例示範如何使用 **\<cryptoClass >** 項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="5dee0-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="5dee0-132">然後，您可以將字串"RSA"傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法來傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="5dee0-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5dee0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dee0-133">See Also</span></span>  
 [<span data-ttu-id="5dee0-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5dee0-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5dee0-135">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5dee0-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="5dee0-136">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="5dee0-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="5dee0-137">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="5dee0-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
