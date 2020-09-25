---
title: <oidEntry> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 2207c934f5864890d9b7a5e22c43a1d53e29aaa5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187104"
---
# <a name="oidentry-element"></a><span data-ttu-id="cefb0-102">\<oidEntry> 項目</span><span class="sxs-lookup"><span data-stu-id="cefb0-102">\<oidEntry> Element</span></span>

<span data-ttu-id="cefb0-103">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="cefb0-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="cefb0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cefb0-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cefb0-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cefb0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cefb0-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cefb0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cefb0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cefb0-107">Attributes</span></span>  
  
|<span data-ttu-id="cefb0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cefb0-108">Attribute</span></span>|<span data-ttu-id="cefb0-109">描述</span><span class="sxs-lookup"><span data-stu-id="cefb0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cefb0-110">**老**</span><span class="sxs-lookup"><span data-stu-id="cefb0-110">**OID**</span></span>|<span data-ttu-id="cefb0-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cefb0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="cefb0-112">指定對應至您的類別所執行之演算法的 asn.1 OID。</span><span class="sxs-lookup"><span data-stu-id="cefb0-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="cefb0-113">**name**</span><span class="sxs-lookup"><span data-stu-id="cefb0-113">**name**</span></span>|<span data-ttu-id="cefb0-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cefb0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="cefb0-115">指定標記中 **名稱** 屬性的值 [\<nameEntry>](nameentry-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="cefb0-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cefb0-116">子元素</span><span class="sxs-lookup"><span data-stu-id="cefb0-116">Child Elements</span></span>  

 <span data-ttu-id="cefb0-117">無。</span><span class="sxs-lookup"><span data-stu-id="cefb0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cefb0-118">父項目</span><span class="sxs-lookup"><span data-stu-id="cefb0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cefb0-119">項目</span><span class="sxs-lookup"><span data-stu-id="cefb0-119">Element</span></span>|<span data-ttu-id="cefb0-120">描述</span><span class="sxs-lookup"><span data-stu-id="cefb0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cefb0-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cefb0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="cefb0-122">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="cefb0-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="cefb0-123">包含 `cryptographySettings` 元素。</span><span class="sxs-lookup"><span data-stu-id="cefb0-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="cefb0-124">包含 (OID) 對應至類別的 asn.1 物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="cefb0-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cefb0-125">備註</span><span class="sxs-lookup"><span data-stu-id="cefb0-125">Remarks</span></span>  

 <span data-ttu-id="cefb0-126">ASN. 1 物件識別碼可識別某些密碼編譯格式的演算法。</span><span class="sxs-lookup"><span data-stu-id="cefb0-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="cefb0-127">將物件識別碼對應至您要識別之演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="cefb0-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cefb0-128">範例</span><span class="sxs-lookup"><span data-stu-id="cefb0-128">Example</span></span>  

 <span data-ttu-id="cefb0-129">下列範例示範如何使用專案，將 **\<oidEntry>** RIPEMD-160 雜湊演算法的物件識別碼對應至該雜湊演算法的實值。</span><span class="sxs-lookup"><span data-stu-id="cefb0-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cefb0-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cefb0-130">See also</span></span>

- [<span data-ttu-id="cefb0-131">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="cefb0-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cefb0-132">密碼編譯設定架構</span><span class="sxs-lookup"><span data-stu-id="cefb0-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cefb0-133">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="cefb0-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="cefb0-134">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="cefb0-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="cefb0-135">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="cefb0-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
