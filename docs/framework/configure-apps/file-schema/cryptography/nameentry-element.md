---
title: "&lt;nameEntry&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 507c71b5c13deeb7c1a81b6a4dd9604c3bd919f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="6e694-102">&lt;nameEntry&gt;項目</span><span class="sxs-lookup"><span data-stu-id="6e694-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="6e694-103">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="6e694-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="6e694-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6e694-104">\<configuration></span></span>  
<span data-ttu-id="6e694-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="6e694-105">\<mscorlib></span></span>  
<span data-ttu-id="6e694-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="6e694-106">\<cryptographySettings></span></span>  
<span data-ttu-id="6e694-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="6e694-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="6e694-108">\<y ></span><span class="sxs-lookup"><span data-stu-id="6e694-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e694-109">語法</span><span class="sxs-lookup"><span data-stu-id="6e694-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e694-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6e694-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e694-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6e694-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e694-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6e694-112">Attributes</span></span>  
  
|<span data-ttu-id="6e694-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6e694-113">Attribute</span></span>|<span data-ttu-id="6e694-114">說明</span><span class="sxs-lookup"><span data-stu-id="6e694-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e694-115">**name**</span><span class="sxs-lookup"><span data-stu-id="6e694-115">**name**</span></span>|<span data-ttu-id="6e694-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6e694-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e694-117">指定密碼編譯類別實作的演算法的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="6e694-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="6e694-118">**class**</span><span class="sxs-lookup"><span data-stu-id="6e694-118">**class**</span></span>|<span data-ttu-id="6e694-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6e694-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e694-120">指定的值**名稱**屬性[ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="6e694-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e694-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6e694-121">Child Elements</span></span>  
 <span data-ttu-id="6e694-122">無。</span><span class="sxs-lookup"><span data-stu-id="6e694-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e694-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6e694-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e694-124">項目</span><span class="sxs-lookup"><span data-stu-id="6e694-124">Element</span></span>|<span data-ttu-id="6e694-125">描述</span><span class="sxs-lookup"><span data-stu-id="6e694-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6e694-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6e694-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="6e694-127">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="6e694-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e694-128">備註</span><span class="sxs-lookup"><span data-stu-id="6e694-128">Remarks</span></span>  
 <span data-ttu-id="6e694-129">**名稱**屬性可以是抽象類別中找到的其中一個名稱<xref:System.Security.Cryptography>命名空間。</span><span class="sxs-lookup"><span data-stu-id="6e694-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="6e694-130">當您呼叫**建立**抽象的密碼編譯類別上的方法，抽象類別名稱傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6e694-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="6e694-131">**CreateFromName**傳回所指定的類型的執行個體**類別**屬性。</span><span class="sxs-lookup"><span data-stu-id="6e694-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="6e694-132">如果**名稱**屬性是簡短名稱，例如 RSA，您可以使用該名稱呼叫時**CreateFromName**方法。</span><span class="sxs-lookup"><span data-stu-id="6e694-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e694-133">範例</span><span class="sxs-lookup"><span data-stu-id="6e694-133">Example</span></span>  
 <span data-ttu-id="6e694-134">下列範例示範如何使用 **\<nameEntry >**項目參考加密編譯類別及設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="6e694-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6e694-135">您接著可以將字串"RSA"至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法以傳回`MyCryptoRSAClass`物件。</span><span class="sxs-lookup"><span data-stu-id="6e694-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e694-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e694-136">See Also</span></span>  
 [<span data-ttu-id="6e694-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6e694-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6e694-138">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6e694-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="6e694-139">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="6e694-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="6e694-140">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="6e694-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
