---
title: "&lt;oidMap&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eab9be57b6f8fac5f208e39a6aaa8eb7be92558d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="c5725-102">&lt;oidMap&gt;項目</span><span class="sxs-lookup"><span data-stu-id="c5725-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="c5725-103">包含類別到 ASN.1 物件識別碼 (OID) 對應。</span><span class="sxs-lookup"><span data-stu-id="c5725-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="c5725-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c5725-104">\<configuration></span></span>  
<span data-ttu-id="c5725-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="c5725-105">\<mscorlib></span></span>  
<span data-ttu-id="c5725-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="c5725-106">\<cryptographySettings></span></span>  
<span data-ttu-id="c5725-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="c5725-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5725-108">語法</span><span class="sxs-lookup"><span data-stu-id="c5725-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5725-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5725-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c5725-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c5725-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5725-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c5725-111">Attributes</span></span>  
 <span data-ttu-id="c5725-112">無。</span><span class="sxs-lookup"><span data-stu-id="c5725-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5725-113">子項目</span><span class="sxs-lookup"><span data-stu-id="c5725-113">Child Elements</span></span>  
  
|<span data-ttu-id="c5725-114">項目</span><span class="sxs-lookup"><span data-stu-id="c5725-114">Element</span></span>|<span data-ttu-id="c5725-115">說明</span><span class="sxs-lookup"><span data-stu-id="c5725-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5725-116">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="c5725-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="c5725-117">對應 ASN.1 OID 為易記名稱。</span><span class="sxs-lookup"><span data-stu-id="c5725-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5725-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c5725-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c5725-119">項目</span><span class="sxs-lookup"><span data-stu-id="c5725-119">Element</span></span>|<span data-ttu-id="c5725-120">描述</span><span class="sxs-lookup"><span data-stu-id="c5725-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5725-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c5725-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c5725-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="c5725-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="c5725-123">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="c5725-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5725-124">範例</span><span class="sxs-lookup"><span data-stu-id="c5725-124">Example</span></span>  
 <span data-ttu-id="c5725-125">下列範例示範如何使用 **\<oidMap >** OID ripemd-160 雜湊演算法，該雜湊演算法的實作對應包含的項目。</span><span class="sxs-lookup"><span data-stu-id="c5725-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5725-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5725-126">See Also</span></span>  
 [<span data-ttu-id="c5725-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c5725-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c5725-128">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c5725-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="c5725-129">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="c5725-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="c5725-130">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="c5725-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="c5725-131">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="c5725-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
