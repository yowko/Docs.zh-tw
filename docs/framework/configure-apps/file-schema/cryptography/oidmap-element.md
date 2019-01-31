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
ms.openlocfilehash: d726965a921a11be1ff9c11d4fb348068b2ec0a3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262513"
---
# <a name="oidmap-element"></a><span data-ttu-id="70ea8-102">\<oidMap > 項目</span><span class="sxs-lookup"><span data-stu-id="70ea8-102">\<oidMap> Element</span></span>
<span data-ttu-id="70ea8-103">包含類別的 ASN.1 物件識別碼 (OID) 對應。</span><span class="sxs-lookup"><span data-stu-id="70ea8-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="70ea8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="70ea8-104">\<configuration></span></span>  
<span data-ttu-id="70ea8-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="70ea8-105">\<mscorlib></span></span>  
<span data-ttu-id="70ea8-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="70ea8-106">\<cryptographySettings></span></span>  
<span data-ttu-id="70ea8-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="70ea8-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70ea8-108">語法</span><span class="sxs-lookup"><span data-stu-id="70ea8-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70ea8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70ea8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70ea8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="70ea8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70ea8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="70ea8-111">Attributes</span></span>  
 <span data-ttu-id="70ea8-112">無。</span><span class="sxs-lookup"><span data-stu-id="70ea8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70ea8-113">子元素</span><span class="sxs-lookup"><span data-stu-id="70ea8-113">Child Elements</span></span>  
  
|<span data-ttu-id="70ea8-114">項目</span><span class="sxs-lookup"><span data-stu-id="70ea8-114">Element</span></span>|<span data-ttu-id="70ea8-115">描述</span><span class="sxs-lookup"><span data-stu-id="70ea8-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70ea8-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="70ea8-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="70ea8-117">將 ASN.1 OID 對應易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="70ea8-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70ea8-118">父項目</span><span class="sxs-lookup"><span data-stu-id="70ea8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="70ea8-119">項目</span><span class="sxs-lookup"><span data-stu-id="70ea8-119">Element</span></span>|<span data-ttu-id="70ea8-120">描述</span><span class="sxs-lookup"><span data-stu-id="70ea8-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="70ea8-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="70ea8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="70ea8-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="70ea8-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="70ea8-123">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="70ea8-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70ea8-124">範例</span><span class="sxs-lookup"><span data-stu-id="70ea8-124">Example</span></span>  
 <span data-ttu-id="70ea8-125">下列範例示範如何使用 **\<oidMap >** 項目來包含該雜湊演算法的實作的 RIPEMD-160 雜湊演算法的 OID 的對應。</span><span class="sxs-lookup"><span data-stu-id="70ea8-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70ea8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ea8-126">See also</span></span>
- [<span data-ttu-id="70ea8-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="70ea8-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="70ea8-128">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="70ea8-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="70ea8-129">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="70ea8-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="70ea8-130">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="70ea8-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="70ea8-131">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="70ea8-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
