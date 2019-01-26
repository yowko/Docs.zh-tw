---
title: '&lt;oidMap&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 130e0d6184f24c5d26efa8497775955f8d602819
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083622"
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="f88fc-102">&lt;oidMap&gt;項目</span><span class="sxs-lookup"><span data-stu-id="f88fc-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="f88fc-103">包含類別的 ASN.1 物件識別碼 (OID) 對應。</span><span class="sxs-lookup"><span data-stu-id="f88fc-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="f88fc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f88fc-104">\<configuration></span></span>  
<span data-ttu-id="f88fc-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="f88fc-105">\<mscorlib></span></span>  
<span data-ttu-id="f88fc-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="f88fc-106">\<cryptographySettings></span></span>  
<span data-ttu-id="f88fc-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="f88fc-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88fc-108">語法</span><span class="sxs-lookup"><span data-stu-id="f88fc-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f88fc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f88fc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f88fc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f88fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f88fc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f88fc-111">Attributes</span></span>  
 <span data-ttu-id="f88fc-112">無。</span><span class="sxs-lookup"><span data-stu-id="f88fc-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f88fc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f88fc-113">Child Elements</span></span>  
  
|<span data-ttu-id="f88fc-114">項目</span><span class="sxs-lookup"><span data-stu-id="f88fc-114">Element</span></span>|<span data-ttu-id="f88fc-115">描述</span><span class="sxs-lookup"><span data-stu-id="f88fc-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f88fc-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="f88fc-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="f88fc-117">將 ASN.1 OID 對應易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="f88fc-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f88fc-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f88fc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f88fc-119">項目</span><span class="sxs-lookup"><span data-stu-id="f88fc-119">Element</span></span>|<span data-ttu-id="f88fc-120">描述</span><span class="sxs-lookup"><span data-stu-id="f88fc-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f88fc-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f88fc-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f88fc-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="f88fc-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="f88fc-123">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="f88fc-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f88fc-124">範例</span><span class="sxs-lookup"><span data-stu-id="f88fc-124">Example</span></span>  
 <span data-ttu-id="f88fc-125">下列範例示範如何使用 **\<oidMap >** 項目來包含該雜湊演算法的實作的 RIPEMD-160 雜湊演算法的 OID 的對應。</span><span class="sxs-lookup"><span data-stu-id="f88fc-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f88fc-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f88fc-126">See also</span></span>
- [<span data-ttu-id="f88fc-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f88fc-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f88fc-128">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f88fc-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="f88fc-129">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="f88fc-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="f88fc-130">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="f88fc-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="f88fc-131">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="f88fc-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
