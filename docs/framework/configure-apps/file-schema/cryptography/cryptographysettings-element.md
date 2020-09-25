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
ms.openlocfilehash: 3c3513c05485550202f2fc5bcae1faabb0e75d47
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201807"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="75039-102">\<cryptographySettings> 項目</span><span class="sxs-lookup"><span data-stu-id="75039-102">\<cryptographySettings> Element</span></span>

<span data-ttu-id="75039-103">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="75039-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="75039-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="75039-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75039-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="75039-105">Attributes and Elements</span></span>  

 <span data-ttu-id="75039-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="75039-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75039-107">屬性</span><span class="sxs-lookup"><span data-stu-id="75039-107">Attributes</span></span>  

 <span data-ttu-id="75039-108">無。</span><span class="sxs-lookup"><span data-stu-id="75039-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="75039-109">子元素</span><span class="sxs-lookup"><span data-stu-id="75039-109">Child Elements</span></span>  
  
|<span data-ttu-id="75039-110">項目</span><span class="sxs-lookup"><span data-stu-id="75039-110">Element</span></span>|<span data-ttu-id="75039-111">描述</span><span class="sxs-lookup"><span data-stu-id="75039-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="75039-112">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="75039-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="75039-113">包含 (OID) 對應至類別的 asn.1 物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="75039-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75039-114">父項目</span><span class="sxs-lookup"><span data-stu-id="75039-114">Parent Elements</span></span>  
  
|<span data-ttu-id="75039-115">項目</span><span class="sxs-lookup"><span data-stu-id="75039-115">Element</span></span>|<span data-ttu-id="75039-116">描述</span><span class="sxs-lookup"><span data-stu-id="75039-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="75039-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="75039-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="75039-118">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="75039-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="75039-119">範例</span><span class="sxs-lookup"><span data-stu-id="75039-119">Example</span></span>  

 <span data-ttu-id="75039-120">下列範例示範如何使用 **\<cryptographySettings>** 元素來包含密碼編譯名稱對應和 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="75039-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="75039-121">這個範例會設定執行時間，以便傳回 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> `MyHashClass` 物件，而 `MyCryptoClass` 類別會對應至物件識別碼1.3.36.2.1。</span><span class="sxs-lookup"><span data-stu-id="75039-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75039-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75039-122">See also</span></span>

- [<span data-ttu-id="75039-123">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="75039-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="75039-124">密碼編譯設定架構</span><span class="sxs-lookup"><span data-stu-id="75039-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="75039-125">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="75039-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
