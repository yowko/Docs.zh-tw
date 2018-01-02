---
title: "&lt;cryptoClass&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 69e844532ab7b9979687e54d7ad4076cd3f51f46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptoclassgt-element"></a><span data-ttu-id="1e9e5-102">&lt;cryptoClass&gt;項目</span><span class="sxs-lookup"><span data-stu-id="1e9e5-102">&lt;cryptoClass&gt; Element</span></span>
<span data-ttu-id="1e9e5-103">包含密碼編譯類別，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="1e9e5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1e9e5-104">\<configuration></span></span>  
<span data-ttu-id="1e9e5-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="1e9e5-105">\<mscorlib></span></span>  
<span data-ttu-id="1e9e5-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="1e9e5-106">\<cryptographySettings></span></span>  
<span data-ttu-id="1e9e5-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="1e9e5-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="1e9e5-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="1e9e5-108">\<cryptoClasses></span></span>  
<span data-ttu-id="1e9e5-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="1e9e5-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9e5-110">語法</span><span class="sxs-lookup"><span data-stu-id="1e9e5-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e9e5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e9e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1e9e5-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e9e5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1e9e5-113">Attributes</span></span>  
  
|<span data-ttu-id="1e9e5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1e9e5-114">Attribute</span></span>|<span data-ttu-id="1e9e5-115">描述</span><span class="sxs-lookup"><span data-stu-id="1e9e5-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="1e9e5-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1e9e5-117">包含密碼編譯類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="1e9e5-118">您可以使用這個屬性來提供您的類別的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="1e9e5-119">您必須指定符合的需求中所指定的字串[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e9e5-120">子元素</span><span class="sxs-lookup"><span data-stu-id="1e9e5-120">Child Elements</span></span>  
 <span data-ttu-id="1e9e5-121">無。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e9e5-122">父項目</span><span class="sxs-lookup"><span data-stu-id="1e9e5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1e9e5-123">項目</span><span class="sxs-lookup"><span data-stu-id="1e9e5-123">Element</span></span>|<span data-ttu-id="1e9e5-124">描述</span><span class="sxs-lookup"><span data-stu-id="1e9e5-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1e9e5-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="1e9e5-126">包含密碼編譯類別清單，其具有 [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="1e9e5-127">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="1e9e5-128">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="1e9e5-129">包含 [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e9e5-130">範例</span><span class="sxs-lookup"><span data-stu-id="1e9e5-130">Example</span></span>  
 <span data-ttu-id="1e9e5-131">下列範例示範如何使用 **\<cryptoClass >**項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="1e9e5-132">您接著可以將字串"RSA"至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法以傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="1e9e5-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e9e5-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9e5-133">See Also</span></span>  
 [<span data-ttu-id="1e9e5-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="1e9e5-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1e9e5-135">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1e9e5-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="1e9e5-136">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="1e9e5-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="1e9e5-137">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="1e9e5-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
