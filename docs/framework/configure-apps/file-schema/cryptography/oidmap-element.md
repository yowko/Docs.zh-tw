---
title: <oidMap> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 6c57810389acbd58e6d2e05277a6f26fa0aac8c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149513"
---
# <a name="oidmap-element"></a><span data-ttu-id="82c68-102">\<oidMap> 項目</span><span class="sxs-lookup"><span data-stu-id="82c68-102">\<oidMap> Element</span></span>

<span data-ttu-id="82c68-103">包含 (OID) 對應至類別的 asn.1 物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="82c68-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="82c68-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="82c68-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82c68-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="82c68-105">Attributes and Elements</span></span>  

 <span data-ttu-id="82c68-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="82c68-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82c68-107">屬性</span><span class="sxs-lookup"><span data-stu-id="82c68-107">Attributes</span></span>  

 <span data-ttu-id="82c68-108">無。</span><span class="sxs-lookup"><span data-stu-id="82c68-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="82c68-109">子元素</span><span class="sxs-lookup"><span data-stu-id="82c68-109">Child Elements</span></span>  
  
|<span data-ttu-id="82c68-110">項目</span><span class="sxs-lookup"><span data-stu-id="82c68-110">Element</span></span>|<span data-ttu-id="82c68-111">描述</span><span class="sxs-lookup"><span data-stu-id="82c68-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="82c68-112">將 asn.1 OID 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="82c68-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82c68-113">父項目</span><span class="sxs-lookup"><span data-stu-id="82c68-113">Parent Elements</span></span>  
  
|<span data-ttu-id="82c68-114">項目</span><span class="sxs-lookup"><span data-stu-id="82c68-114">Element</span></span>|<span data-ttu-id="82c68-115">描述</span><span class="sxs-lookup"><span data-stu-id="82c68-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="82c68-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="82c68-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="82c68-117">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="82c68-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="82c68-118">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="82c68-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82c68-119">範例</span><span class="sxs-lookup"><span data-stu-id="82c68-119">Example</span></span>  

 <span data-ttu-id="82c68-120">下列範例示範如何使用專案，將 **\<oidMap>** RIPEMD-160 雜湊演算法的 OID 對應至該雜湊演算法的執行。</span><span class="sxs-lookup"><span data-stu-id="82c68-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82c68-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82c68-121">See also</span></span>

- [<span data-ttu-id="82c68-122">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="82c68-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="82c68-123">密碼編譯設定架構</span><span class="sxs-lookup"><span data-stu-id="82c68-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="82c68-124">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="82c68-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="82c68-125">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="82c68-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="82c68-126">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="82c68-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
