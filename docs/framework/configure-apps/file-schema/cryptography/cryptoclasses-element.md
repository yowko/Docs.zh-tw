---
title: <cryptoClasses> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: dbe46e0b36d247005f933c82ee83687886b283d1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659659"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="9bd90-102">\<cryptoClasses > 元素</span><span class="sxs-lookup"><span data-stu-id="9bd90-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="9bd90-103">包含密碼編譯類別清單，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="9bd90-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="9bd90-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9bd90-104">\<configuration></span></span>  
<span data-ttu-id="9bd90-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="9bd90-105">\<mscorlib></span></span>  
<span data-ttu-id="9bd90-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="9bd90-106">\<cryptographySettings></span></span>  
<span data-ttu-id="9bd90-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="9bd90-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="9bd90-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="9bd90-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd90-109">語法</span><span class="sxs-lookup"><span data-stu-id="9bd90-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bd90-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9bd90-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9bd90-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9bd90-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bd90-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9bd90-112">Attributes</span></span>  
 <span data-ttu-id="9bd90-113">無。</span><span class="sxs-lookup"><span data-stu-id="9bd90-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9bd90-114">子元素</span><span class="sxs-lookup"><span data-stu-id="9bd90-114">Child Elements</span></span>  
  
|<span data-ttu-id="9bd90-115">項目</span><span class="sxs-lookup"><span data-stu-id="9bd90-115">Element</span></span>|<span data-ttu-id="9bd90-116">描述</span><span class="sxs-lookup"><span data-stu-id="9bd90-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bd90-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="9bd90-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="9bd90-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="9bd90-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bd90-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9bd90-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9bd90-120">項目</span><span class="sxs-lookup"><span data-stu-id="9bd90-120">Element</span></span>|<span data-ttu-id="9bd90-121">描述</span><span class="sxs-lookup"><span data-stu-id="9bd90-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9bd90-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="9bd90-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="9bd90-123">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="9bd90-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="9bd90-124">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="9bd90-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="9bd90-125">`cryptographySettings`包含元素。</span><span class="sxs-lookup"><span data-stu-id="9bd90-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9bd90-126">範例</span><span class="sxs-lookup"><span data-stu-id="9bd90-126">Example</span></span>  
 <span data-ttu-id="9bd90-127">下列範例顯示如何使用 **\<cryptoClass >** 專案來參考密碼編譯類別, 以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="9bd90-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="9bd90-128">接著, 您可以將字串 "RSA" 傳遞給<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 並<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>使用方法來`MyCryptoRSAClass`傳回物件。</span><span class="sxs-lookup"><span data-stu-id="9bd90-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bd90-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bd90-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="9bd90-130">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="9bd90-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9bd90-131">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9bd90-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9bd90-132">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="9bd90-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="9bd90-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="9bd90-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="9bd90-134">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="9bd90-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
