---
title: <cryptoClass> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 6a868f62c6a327012a6225b86bf0103d178d6ab7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921175"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="1ef0e-102">\<cryptoClass > 元素</span><span class="sxs-lookup"><span data-stu-id="1ef0e-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="1ef0e-103">包含密碼編譯類別，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="1ef0e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1ef0e-104">\<configuration></span></span>  
<span data-ttu-id="1ef0e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="1ef0e-105">\<mscorlib></span></span>  
<span data-ttu-id="1ef0e-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="1ef0e-106">\<cryptographySettings></span></span>  
<span data-ttu-id="1ef0e-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="1ef0e-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="1ef0e-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="1ef0e-108">\<cryptoClasses></span></span>  
<span data-ttu-id="1ef0e-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="1ef0e-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef0e-110">語法</span><span class="sxs-lookup"><span data-stu-id="1ef0e-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ef0e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ef0e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1ef0e-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ef0e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1ef0e-113">Attributes</span></span>  
  
|<span data-ttu-id="1ef0e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1ef0e-114">Attribute</span></span>|<span data-ttu-id="1ef0e-115">描述</span><span class="sxs-lookup"><span data-stu-id="1ef0e-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="1ef0e-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1ef0e-117">包含密碼編譯類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="1ef0e-118">使用此屬性來提供類別的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="1ef0e-119">您必須指定符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ef0e-120">子元素</span><span class="sxs-lookup"><span data-stu-id="1ef0e-120">Child Elements</span></span>  
 <span data-ttu-id="1ef0e-121">無。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ef0e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="1ef0e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1ef0e-123">項目</span><span class="sxs-lookup"><span data-stu-id="1ef0e-123">Element</span></span>|<span data-ttu-id="1ef0e-124">說明</span><span class="sxs-lookup"><span data-stu-id="1ef0e-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1ef0e-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="1ef0e-126">包含密碼編譯類別清單，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="1ef0e-127">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="1ef0e-128">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="1ef0e-129">包含 [\<cryptographySettings>](cryptographysettings-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1ef0e-130">範例</span><span class="sxs-lookup"><span data-stu-id="1ef0e-130">Example</span></span>  
 <span data-ttu-id="1ef0e-131">下列範例顯示如何使用 **\<cryptoClass >** 專案來參考密碼編譯類別, 以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="1ef0e-132">接著, 您可以將字串 "RSA" 傳遞給<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 並<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>使用方法來`MyCryptoRSAClass`傳回物件。</span><span class="sxs-lookup"><span data-stu-id="1ef0e-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ef0e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ef0e-133">See also</span></span>

- [<span data-ttu-id="1ef0e-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="1ef0e-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1ef0e-135">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1ef0e-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1ef0e-136">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="1ef0e-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="1ef0e-137">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="1ef0e-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
