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
ms.openlocfilehash: eec2c4745ad5a0492ccf04c8f23b901275f23c01
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698441"
---
# <a name="oidmap-element"></a><span data-ttu-id="5d9e1-102">@no__t 0oidMap > 元素</span><span class="sxs-lookup"><span data-stu-id="5d9e1-102">\<oidMap> Element</span></span>
<span data-ttu-id="5d9e1-103">包含對類別的 asn.1 物件識別元（OID）對應。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
[<span data-ttu-id="5d9e1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="5d9e1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5d9e1-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5d9e1-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="5d9e1-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d9e1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="5d9e1-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="5d9e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d9e1-108">語法</span><span class="sxs-lookup"><span data-stu-id="5d9e1-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d9e1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5d9e1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5d9e1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d9e1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5d9e1-111">Attributes</span></span>  
 <span data-ttu-id="5d9e1-112">無。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d9e1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="5d9e1-113">Child Elements</span></span>  
  
|<span data-ttu-id="5d9e1-114">元素</span><span class="sxs-lookup"><span data-stu-id="5d9e1-114">Element</span></span>|<span data-ttu-id="5d9e1-115">描述</span><span class="sxs-lookup"><span data-stu-id="5d9e1-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d9e1-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="5d9e1-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="5d9e1-117">將 asn.1 OID 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d9e1-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5d9e1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5d9e1-119">項目</span><span class="sxs-lookup"><span data-stu-id="5d9e1-119">Element</span></span>|<span data-ttu-id="5d9e1-120">描述</span><span class="sxs-lookup"><span data-stu-id="5d9e1-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5d9e1-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="5d9e1-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="5d9e1-123">`cryptographySettings`包含元素。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5d9e1-124">範例</span><span class="sxs-lookup"><span data-stu-id="5d9e1-124">Example</span></span>  
 <span data-ttu-id="5d9e1-125">下列範例示範如何使用 **\<oidMap >** 元素，以包含 RIPEMD-160 雜湊演算法的 OID 對應到該雜湊演算法的執行。</span><span class="sxs-lookup"><span data-stu-id="5d9e1-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d9e1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d9e1-126">See also</span></span>

- [<span data-ttu-id="5d9e1-127">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5d9e1-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5d9e1-128">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5d9e1-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d9e1-129">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="5d9e1-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="5d9e1-130">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="5d9e1-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="5d9e1-131">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="5d9e1-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
