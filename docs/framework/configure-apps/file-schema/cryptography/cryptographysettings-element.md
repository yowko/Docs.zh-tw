---
title: '&lt;cryptographySettings&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: e0ef409e119d4ccaba44b22d78959bf80117c80f
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084454"
---
# <a name="ltcryptographysettingsgt-element"></a><span data-ttu-id="43fd4-102">&lt;cryptographySettings&gt;項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-102">&lt;cryptographySettings&gt; Element</span></span>
<span data-ttu-id="43fd4-103">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="43fd4-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="43fd4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="43fd4-104">\<configuration></span></span>  
<span data-ttu-id="43fd4-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="43fd4-105">\<mscorlib></span></span>  
<span data-ttu-id="43fd4-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="43fd4-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43fd4-107">語法</span><span class="sxs-lookup"><span data-stu-id="43fd4-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43fd4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43fd4-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="43fd4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43fd4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="43fd4-110">Attributes</span></span>  
 <span data-ttu-id="43fd4-111">無。</span><span class="sxs-lookup"><span data-stu-id="43fd4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43fd4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="43fd4-112">Child Elements</span></span>  
  
|<span data-ttu-id="43fd4-113">項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-113">Element</span></span>|<span data-ttu-id="43fd4-114">描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43fd4-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="43fd4-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="43fd4-116">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="43fd4-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="43fd4-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="43fd4-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="43fd4-118">包含類別的 ASN.1 物件識別碼 (OID) 對應。</span><span class="sxs-lookup"><span data-stu-id="43fd4-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43fd4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="43fd4-120">項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-120">Element</span></span>|<span data-ttu-id="43fd4-121">描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43fd4-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="43fd4-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="43fd4-123">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="43fd4-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43fd4-124">範例</span><span class="sxs-lookup"><span data-stu-id="43fd4-124">Example</span></span>  
 <span data-ttu-id="43fd4-125">下列範例示範如何使用 **\<cryptographySettings >** 包含密碼編譯名稱對應和 OID 對應的項目。</span><span class="sxs-lookup"><span data-stu-id="43fd4-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="43fd4-126">這個範例會設定執行階段，讓<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>會傳回`MyHashClass`物件和`MyCryptoClass`類別會對應至物件識別元 1.3.36.2.1。</span><span class="sxs-lookup"><span data-stu-id="43fd4-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43fd4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43fd4-127">See also</span></span>
- [<span data-ttu-id="43fd4-128">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="43fd4-129">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="43fd4-130">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="43fd4-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
