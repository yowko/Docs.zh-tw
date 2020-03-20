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
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155228"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="d3f29-102">\<密碼設置>元素</span><span class="sxs-lookup"><span data-stu-id="d3f29-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="d3f29-103">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="d3f29-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="d3f29-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3f29-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3f29-105">&nbsp;&nbsp;[**\<姆斯科利布>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d3f29-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="d3f29-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<密碼設置>**</span><span class="sxs-lookup"><span data-stu-id="d3f29-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d3f29-107">語法</span><span class="sxs-lookup"><span data-stu-id="d3f29-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3f29-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3f29-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d3f29-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d3f29-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3f29-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d3f29-110">Attributes</span></span>  
 <span data-ttu-id="d3f29-111">無。</span><span class="sxs-lookup"><span data-stu-id="d3f29-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3f29-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d3f29-112">Child Elements</span></span>  
  
|<span data-ttu-id="d3f29-113">元素</span><span class="sxs-lookup"><span data-stu-id="d3f29-113">Element</span></span>|<span data-ttu-id="d3f29-114">描述</span><span class="sxs-lookup"><span data-stu-id="d3f29-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3f29-115">\<加密名稱映射></span><span class="sxs-lookup"><span data-stu-id="d3f29-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="d3f29-116">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="d3f29-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="d3f29-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="d3f29-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="d3f29-118">包含 ASN.1 物件識別碼 （OID） 映射到類。</span><span class="sxs-lookup"><span data-stu-id="d3f29-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3f29-119">父項目</span><span class="sxs-lookup"><span data-stu-id="d3f29-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d3f29-120">元素</span><span class="sxs-lookup"><span data-stu-id="d3f29-120">Element</span></span>|<span data-ttu-id="d3f29-121">描述</span><span class="sxs-lookup"><span data-stu-id="d3f29-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d3f29-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d3f29-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="d3f29-123">包含元素`cryptographySettings`。</span><span class="sxs-lookup"><span data-stu-id="d3f29-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d3f29-124">範例</span><span class="sxs-lookup"><span data-stu-id="d3f29-124">Example</span></span>  
 <span data-ttu-id="d3f29-125">下面的示例演示如何使用**\<加密設定>** 元素來包含加密名稱映射和 OID 映射。</span><span class="sxs-lookup"><span data-stu-id="d3f29-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="d3f29-126">此示例配置運行時，<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>以便返回`MyHashClass`物件，`MyCryptoClass`並且類映射到物件識別碼 1.3.36.2.1。</span><span class="sxs-lookup"><span data-stu-id="d3f29-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3f29-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3f29-127">See also</span></span>

- [<span data-ttu-id="d3f29-128">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d3f29-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d3f29-129">加密設定架構</span><span class="sxs-lookup"><span data-stu-id="d3f29-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d3f29-130">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="d3f29-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
