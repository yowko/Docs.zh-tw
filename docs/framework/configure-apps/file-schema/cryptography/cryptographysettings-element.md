---
title: <cryptographySettings> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: 96a8c9accc56274b5cc13dc2a871165857b3a2d9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699815"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="64015-102">@no__t 0cryptographySettings > 元素</span><span class="sxs-lookup"><span data-stu-id="64015-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="64015-103">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="64015-103">Contains cryptography settings.</span></span>  
  
[<span data-ttu-id="64015-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="64015-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="64015-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="64015-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="64015-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="64015-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64015-107">語法</span><span class="sxs-lookup"><span data-stu-id="64015-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64015-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="64015-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64015-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="64015-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64015-110">屬性</span><span class="sxs-lookup"><span data-stu-id="64015-110">Attributes</span></span>  
 <span data-ttu-id="64015-111">無。</span><span class="sxs-lookup"><span data-stu-id="64015-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64015-112">子元素</span><span class="sxs-lookup"><span data-stu-id="64015-112">Child Elements</span></span>  
  
|<span data-ttu-id="64015-113">元素</span><span class="sxs-lookup"><span data-stu-id="64015-113">Element</span></span>|<span data-ttu-id="64015-114">描述</span><span class="sxs-lookup"><span data-stu-id="64015-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64015-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="64015-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="64015-116">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="64015-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="64015-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="64015-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="64015-118">包含對類別的 asn.1 物件識別元（OID）對應。</span><span class="sxs-lookup"><span data-stu-id="64015-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64015-119">父項目</span><span class="sxs-lookup"><span data-stu-id="64015-119">Parent Elements</span></span>  
  
|<span data-ttu-id="64015-120">項目</span><span class="sxs-lookup"><span data-stu-id="64015-120">Element</span></span>|<span data-ttu-id="64015-121">描述</span><span class="sxs-lookup"><span data-stu-id="64015-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="64015-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="64015-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="64015-123">`cryptographySettings`包含元素。</span><span class="sxs-lookup"><span data-stu-id="64015-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64015-124">範例</span><span class="sxs-lookup"><span data-stu-id="64015-124">Example</span></span>  
 <span data-ttu-id="64015-125">下列範例示範如何使用 **@no__t 1cryptographySettings >** 元素來包含密碼編譯名稱對應和 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="64015-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="64015-126">這個範例會設定執行時間，讓 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 會傳回 `MyHashClass` 物件，而 @no__t 2 類別則會對應至物件識別碼1.3.36.2.1。</span><span class="sxs-lookup"><span data-stu-id="64015-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64015-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64015-127">See also</span></span>

- [<span data-ttu-id="64015-128">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="64015-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="64015-129">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="64015-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="64015-130">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="64015-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
