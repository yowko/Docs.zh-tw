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
ms.openlocfilehash: cbdf6150010ca2dace3f0610d9caa90c2bf52746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921049"
---
# <a name="oidentry-element"></a><span data-ttu-id="7b0ed-102">\<y > 元素</span><span class="sxs-lookup"><span data-stu-id="7b0ed-102">\<oidEntry> Element</span></span>
<span data-ttu-id="7b0ed-103">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="7b0ed-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7b0ed-104">\<configuration></span></span>  
<span data-ttu-id="7b0ed-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="7b0ed-105">\<mscorlib></span></span>  
<span data-ttu-id="7b0ed-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="7b0ed-106">\<cryptographySettings></span></span>  
<span data-ttu-id="7b0ed-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="7b0ed-107">\<oidMap></span></span>  
<span data-ttu-id="7b0ed-108">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="7b0ed-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b0ed-109">語法</span><span class="sxs-lookup"><span data-stu-id="7b0ed-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b0ed-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b0ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b0ed-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b0ed-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7b0ed-112">Attributes</span></span>  
  
|<span data-ttu-id="7b0ed-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7b0ed-113">Attribute</span></span>|<span data-ttu-id="7b0ed-114">描述</span><span class="sxs-lookup"><span data-stu-id="7b0ed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b0ed-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="7b0ed-115">**OID**</span></span>|<span data-ttu-id="7b0ed-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="7b0ed-117">指定對應至您的類別所實演算法的 asn.1 OID。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="7b0ed-118">**name**</span><span class="sxs-lookup"><span data-stu-id="7b0ed-118">**name**</span></span>|<span data-ttu-id="7b0ed-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="7b0ed-120">[指定\<y >](nameentry-element.md)標記中**name**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b0ed-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7b0ed-121">Child Elements</span></span>  
 <span data-ttu-id="7b0ed-122">無。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b0ed-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7b0ed-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7b0ed-124">項目</span><span class="sxs-lookup"><span data-stu-id="7b0ed-124">Element</span></span>|<span data-ttu-id="7b0ed-125">說明</span><span class="sxs-lookup"><span data-stu-id="7b0ed-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7b0ed-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="7b0ed-127">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="7b0ed-128">`cryptographySettings`包含元素。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="7b0ed-129">包含對類別的 asn.1 物件識別元 (OID) 對應。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b0ed-130">備註</span><span class="sxs-lookup"><span data-stu-id="7b0ed-130">Remarks</span></span>  
 <span data-ttu-id="7b0ed-131">Asn.1 物件識別碼會識別一些密碼編譯格式的演算法。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="7b0ed-132">將物件識別碼對應至您想要識別之演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b0ed-133">範例</span><span class="sxs-lookup"><span data-stu-id="7b0ed-133">Example</span></span>  
 <span data-ttu-id="7b0ed-134">下列範例示範如何使用 **\<y >** 元素, 將 RIPEMD-160 雜湊演算法的物件識別碼對應至該雜湊演算法的執行。</span><span class="sxs-lookup"><span data-stu-id="7b0ed-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b0ed-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b0ed-135">See also</span></span>

- [<span data-ttu-id="7b0ed-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7b0ed-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7b0ed-137">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7b0ed-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7b0ed-138">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="7b0ed-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7b0ed-139">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="7b0ed-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="7b0ed-140">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="7b0ed-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
