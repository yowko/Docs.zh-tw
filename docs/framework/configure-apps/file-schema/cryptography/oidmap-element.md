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
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155163"
---
# <a name="oidmap-element"></a><span data-ttu-id="d437e-102">\<oidMap>元素</span><span class="sxs-lookup"><span data-stu-id="d437e-102">\<oidMap> Element</span></span>
<span data-ttu-id="d437e-103">包含 ASN.1 物件識別碼 （OID） 映射到類。</span><span class="sxs-lookup"><span data-stu-id="d437e-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

<span data-ttu-id="d437e-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d437e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d437e-105">&nbsp;&nbsp;[**\<姆斯科利布>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d437e-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="d437e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<密碼設置>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="d437e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="d437e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="d437e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d437e-108">語法</span><span class="sxs-lookup"><span data-stu-id="d437e-108">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d437e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d437e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d437e-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d437e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d437e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d437e-111">Attributes</span></span>  
 <span data-ttu-id="d437e-112">無。</span><span class="sxs-lookup"><span data-stu-id="d437e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d437e-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d437e-113">Child Elements</span></span>  
  
|<span data-ttu-id="d437e-114">元素</span><span class="sxs-lookup"><span data-stu-id="d437e-114">Element</span></span>|<span data-ttu-id="d437e-115">描述</span><span class="sxs-lookup"><span data-stu-id="d437e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d437e-116">\<oidentry></span><span class="sxs-lookup"><span data-stu-id="d437e-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="d437e-117">將 ASN.1 OID 映射到易記名稱。</span><span class="sxs-lookup"><span data-stu-id="d437e-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d437e-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d437e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d437e-119">元素</span><span class="sxs-lookup"><span data-stu-id="d437e-119">Element</span></span>|<span data-ttu-id="d437e-120">描述</span><span class="sxs-lookup"><span data-stu-id="d437e-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d437e-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d437e-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="d437e-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="d437e-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="d437e-123">包含元素`cryptographySettings`。</span><span class="sxs-lookup"><span data-stu-id="d437e-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d437e-124">範例</span><span class="sxs-lookup"><span data-stu-id="d437e-124">Example</span></span>  
 <span data-ttu-id="d437e-125">下面的示例演示如何使用**\<oidMap>** 元素將 RIPEMD-160 雜湊演算法的 OID 映射到該雜湊演算法的實現。</span><span class="sxs-lookup"><span data-stu-id="d437e-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d437e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d437e-126">See also</span></span>

- [<span data-ttu-id="d437e-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d437e-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d437e-128">加密設定架構</span><span class="sxs-lookup"><span data-stu-id="d437e-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d437e-129">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="d437e-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="d437e-130">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="d437e-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="d437e-131">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="d437e-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
