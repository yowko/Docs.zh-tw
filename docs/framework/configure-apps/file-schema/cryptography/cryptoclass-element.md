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
ms.openlocfilehash: 4872fbd6fa043902e8c69f158bee5d0c915ec83a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088653"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="ad5cd-102">\<cryptoClass> 項目</span><span class="sxs-lookup"><span data-stu-id="ad5cd-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="ad5cd-103">包含在專案中具有易記名稱對應的密碼編譯類別 [\<nameEntry>](nameentry-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="ad5cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad5cd-104">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad5cd-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad5cd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ad5cd-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad5cd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ad5cd-107">Attributes</span></span>  
  
|<span data-ttu-id="ad5cd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ad5cd-108">Attribute</span></span>|<span data-ttu-id="ad5cd-109">描述</span><span class="sxs-lookup"><span data-stu-id="ad5cd-109">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="ad5cd-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad5cd-111">包含密碼編譯類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-111">Contains the information for the cryptography class.</span></span> <span data-ttu-id="ad5cd-112">使用此屬性來提供類別的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-112">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="ad5cd-113">您必須指定符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-113">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad5cd-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-114">Child Elements</span></span>  
 <span data-ttu-id="ad5cd-115">無。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad5cd-116">父項目</span><span class="sxs-lookup"><span data-stu-id="ad5cd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad5cd-117">元素</span><span class="sxs-lookup"><span data-stu-id="ad5cd-117">Element</span></span>|<span data-ttu-id="ad5cd-118">描述</span><span class="sxs-lookup"><span data-stu-id="ad5cd-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad5cd-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="ad5cd-120">包含在專案中有易記名稱對應的密碼編譯類別清單 [\<nameEntry>](nameentry-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-120">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ad5cd-121">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-121">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ad5cd-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-122">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ad5cd-123">包含 [\<cryptographySettings>](cryptographysettings-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-123">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ad5cd-124">範例</span><span class="sxs-lookup"><span data-stu-id="ad5cd-124">Example</span></span>  
 <span data-ttu-id="ad5cd-125">下列範例示範如何使用 **\<cryptoClass>** 元素來參考密碼編譯類別，以及如何設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-125">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ad5cd-126">接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="ad5cd-126">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad5cd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad5cd-127">See also</span></span>

- [<span data-ttu-id="ad5cd-128">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="ad5cd-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ad5cd-129">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ad5cd-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ad5cd-130">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="ad5cd-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ad5cd-131">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="ad5cd-131">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
