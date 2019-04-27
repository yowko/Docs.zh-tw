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
ms.openlocfilehash: c686d2b99ad66aec753a356b09fa3c7151193808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674742"
---
# <a name="oidentry-element"></a><span data-ttu-id="f224e-102">\<oidEntry > 項目</span><span class="sxs-lookup"><span data-stu-id="f224e-102">\<oidEntry> Element</span></span>
<span data-ttu-id="f224e-103">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f224e-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="f224e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f224e-104">\<configuration></span></span>  
<span data-ttu-id="f224e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="f224e-105">\<mscorlib></span></span>  
<span data-ttu-id="f224e-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="f224e-106">\<cryptographySettings></span></span>  
<span data-ttu-id="f224e-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="f224e-107">\<oidMap></span></span>  
<span data-ttu-id="f224e-108">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="f224e-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f224e-109">語法</span><span class="sxs-lookup"><span data-stu-id="f224e-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f224e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f224e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f224e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f224e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f224e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f224e-112">Attributes</span></span>  
  
|<span data-ttu-id="f224e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f224e-113">Attribute</span></span>|<span data-ttu-id="f224e-114">描述</span><span class="sxs-lookup"><span data-stu-id="f224e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f224e-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="f224e-115">**OID**</span></span>|<span data-ttu-id="f224e-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f224e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f224e-117">指定的 ASN.1 OID 對應至您的類別所實作的演算法。</span><span class="sxs-lookup"><span data-stu-id="f224e-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="f224e-118">**name**</span><span class="sxs-lookup"><span data-stu-id="f224e-118">**name**</span></span>|<span data-ttu-id="f224e-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f224e-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="f224e-120">指定的值**名稱**屬性中[ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)標記。</span><span class="sxs-lookup"><span data-stu-id="f224e-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f224e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="f224e-121">Child Elements</span></span>  
 <span data-ttu-id="f224e-122">無。</span><span class="sxs-lookup"><span data-stu-id="f224e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f224e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="f224e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f224e-124">項目</span><span class="sxs-lookup"><span data-stu-id="f224e-124">Element</span></span>|<span data-ttu-id="f224e-125">描述</span><span class="sxs-lookup"><span data-stu-id="f224e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f224e-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f224e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f224e-127">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="f224e-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="f224e-128">包含`cryptographySettings`項目。</span><span class="sxs-lookup"><span data-stu-id="f224e-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="f224e-129">包含類別的 ASN.1 物件識別碼 (OID) 對應。</span><span class="sxs-lookup"><span data-stu-id="f224e-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f224e-130">備註</span><span class="sxs-lookup"><span data-stu-id="f224e-130">Remarks</span></span>  
 <span data-ttu-id="f224e-131">ASN.1 物件識別碼會識別在部分密碼編譯的格式中的演算法。</span><span class="sxs-lookup"><span data-stu-id="f224e-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="f224e-132">將物件識別碼對應至您想要識別演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f224e-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f224e-133">範例</span><span class="sxs-lookup"><span data-stu-id="f224e-133">Example</span></span>  
 <span data-ttu-id="f224e-134">下列範例示範如何使用 **\<oidEntry >** 將 RIPEMD-160 雜湊演算法的物件識別項對應至該雜湊演算法的實作的項目。</span><span class="sxs-lookup"><span data-stu-id="f224e-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f224e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f224e-135">See also</span></span>

- [<span data-ttu-id="f224e-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f224e-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f224e-137">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f224e-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="f224e-138">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="f224e-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="f224e-139">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="f224e-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="f224e-140">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="f224e-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
