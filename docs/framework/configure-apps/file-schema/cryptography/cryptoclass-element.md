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
ms.openlocfilehash: db3681ea141bb7e3905f6a470f5c74ce05f6ef4b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699793"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="ce796-102">@no__t 0cryptoClass > 元素</span><span class="sxs-lookup"><span data-stu-id="ce796-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="ce796-103">包含密碼編譯類別，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="ce796-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="ce796-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="ce796-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ce796-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ce796-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="ce796-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce796-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="ce796-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce796-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="ce796-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce796-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>  
<span data-ttu-id="ce796-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="ce796-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce796-110">語法</span><span class="sxs-lookup"><span data-stu-id="ce796-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce796-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce796-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ce796-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ce796-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce796-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ce796-113">Attributes</span></span>  
  
|<span data-ttu-id="ce796-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ce796-114">Attribute</span></span>|<span data-ttu-id="ce796-115">描述</span><span class="sxs-lookup"><span data-stu-id="ce796-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="ce796-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ce796-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce796-117">包含密碼編譯類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="ce796-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="ce796-118">使用此屬性來提供類別的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="ce796-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="ce796-119">您必須指定符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="ce796-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce796-120">子元素</span><span class="sxs-lookup"><span data-stu-id="ce796-120">Child Elements</span></span>  
 <span data-ttu-id="ce796-121">無。</span><span class="sxs-lookup"><span data-stu-id="ce796-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce796-122">父項目</span><span class="sxs-lookup"><span data-stu-id="ce796-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ce796-123">項目</span><span class="sxs-lookup"><span data-stu-id="ce796-123">Element</span></span>|<span data-ttu-id="ce796-124">描述</span><span class="sxs-lookup"><span data-stu-id="ce796-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce796-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ce796-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="ce796-126">包含密碼編譯類別清單，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="ce796-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ce796-127">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="ce796-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ce796-128">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="ce796-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ce796-129">包含 [\<cryptographySettings>](cryptographysettings-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="ce796-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ce796-130">範例</span><span class="sxs-lookup"><span data-stu-id="ce796-130">Example</span></span>  
 <span data-ttu-id="ce796-131">下列範例示範如何使用 **@no__t 1cryptoClass >** 元素來參考密碼編譯類別，以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="ce796-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ce796-132">接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，然後使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法傳回 @no__t 2 物件。</span><span class="sxs-lookup"><span data-stu-id="ce796-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ce796-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce796-133">See also</span></span>

- [<span data-ttu-id="ce796-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ce796-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ce796-135">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ce796-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce796-136">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="ce796-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ce796-137">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="ce796-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
