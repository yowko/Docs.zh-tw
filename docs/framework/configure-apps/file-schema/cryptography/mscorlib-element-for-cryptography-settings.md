---
title: 密碼編譯設定的 <mscorlib> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 4e2159cda5f35b5795804dede09ec17d07d71b23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699737"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="c918e-102">\<mscorlib > 元素進行密碼編譯設定</span><span class="sxs-lookup"><span data-stu-id="c918e-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="c918e-103">包含[\<的 cryptographySettings > 元素](cryptographysettings-element.md)。</span><span class="sxs-lookup"><span data-stu-id="c918e-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="c918e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="c918e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c918e-105">&nbsp;&nbsp; **\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="c918e-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c918e-106">語法</span><span class="sxs-lookup"><span data-stu-id="c918e-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c918e-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c918e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c918e-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c918e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c918e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c918e-109">Attributes</span></span>  
 <span data-ttu-id="c918e-110">None。</span><span class="sxs-lookup"><span data-stu-id="c918e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c918e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c918e-111">Child Elements</span></span>  
  
|<span data-ttu-id="c918e-112">項目</span><span class="sxs-lookup"><span data-stu-id="c918e-112">Element</span></span>|<span data-ttu-id="c918e-113">描述</span><span class="sxs-lookup"><span data-stu-id="c918e-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="c918e-114">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="c918e-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c918e-115">父項目</span><span class="sxs-lookup"><span data-stu-id="c918e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c918e-116">項目</span><span class="sxs-lookup"><span data-stu-id="c918e-116">Element</span></span>|<span data-ttu-id="c918e-117">描述</span><span class="sxs-lookup"><span data-stu-id="c918e-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c918e-118">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c918e-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c918e-119">範例</span><span class="sxs-lookup"><span data-stu-id="c918e-119">Example</span></span>  
 <span data-ttu-id="c918e-120">下列範例示範如何使用 **\<的 mscorlib >** 元素來參考密碼編譯類別，以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="c918e-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c918e-121">接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，然後使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="c918e-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c918e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c918e-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="c918e-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c918e-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c918e-124">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c918e-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c918e-125">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="c918e-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c918e-126">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="c918e-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
