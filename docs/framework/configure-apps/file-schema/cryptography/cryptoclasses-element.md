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
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155242"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="0d52b-102">\<加密類>元素</span><span class="sxs-lookup"><span data-stu-id="0d52b-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="0d52b-103">包含具有映射到[\<nameentry>](nameentry-element.md)元素中的易記名稱的加密類的清單。</span><span class="sxs-lookup"><span data-stu-id="0d52b-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="0d52b-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="0d52b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0d52b-105">&nbsp;&nbsp;[**\<姆斯科利布>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0d52b-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="0d52b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<密碼設置>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d52b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="0d52b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<加密名稱映射>**](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d52b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="0d52b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<加密類>**</span><span class="sxs-lookup"><span data-stu-id="0d52b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d52b-109">語法</span><span class="sxs-lookup"><span data-stu-id="0d52b-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d52b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d52b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0d52b-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0d52b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d52b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0d52b-112">Attributes</span></span>  
 <span data-ttu-id="0d52b-113">無。</span><span class="sxs-lookup"><span data-stu-id="0d52b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d52b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="0d52b-114">Child Elements</span></span>  
  
|<span data-ttu-id="0d52b-115">元素</span><span class="sxs-lookup"><span data-stu-id="0d52b-115">Element</span></span>|<span data-ttu-id="0d52b-116">描述</span><span class="sxs-lookup"><span data-stu-id="0d52b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d52b-117">\<加密類></span><span class="sxs-lookup"><span data-stu-id="0d52b-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="0d52b-118">包含一個加密類，該類具有與**\<nameentry>** 元素中的易記名稱的映射。</span><span class="sxs-lookup"><span data-stu-id="0d52b-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d52b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0d52b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0d52b-120">元素</span><span class="sxs-lookup"><span data-stu-id="0d52b-120">Element</span></span>|<span data-ttu-id="0d52b-121">描述</span><span class="sxs-lookup"><span data-stu-id="0d52b-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d52b-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0d52b-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0d52b-123">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="0d52b-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="0d52b-124">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="0d52b-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="0d52b-125">包含元素`cryptographySettings`。</span><span class="sxs-lookup"><span data-stu-id="0d52b-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0d52b-126">範例</span><span class="sxs-lookup"><span data-stu-id="0d52b-126">Example</span></span>  
 <span data-ttu-id="0d52b-127">下面的示例演示如何使用**\<cryptoclass>** 元素來引用加密類和配置運行時。</span><span class="sxs-lookup"><span data-stu-id="0d52b-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="0d52b-128">然後，可以將字串"RSA"傳遞給 方法，<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>並使用 方法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>返回物件`MyCryptoRSAClass`。</span><span class="sxs-lookup"><span data-stu-id="0d52b-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d52b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d52b-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="0d52b-130">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0d52b-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0d52b-131">加密設定架構</span><span class="sxs-lookup"><span data-stu-id="0d52b-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d52b-132">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="0d52b-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="0d52b-133">系統.安全.加密.加密配置.創建從名稱</span><span class="sxs-lookup"><span data-stu-id="0d52b-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="0d52b-134">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="0d52b-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
