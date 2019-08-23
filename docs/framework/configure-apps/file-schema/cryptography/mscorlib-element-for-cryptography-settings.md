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
ms.openlocfilehash: c780087246ea91846896037a245b82493251e538
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921058"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="bb363-102">\<用於密碼編譯設定的 mscorlib > 元素</span><span class="sxs-lookup"><span data-stu-id="bb363-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="bb363-103">包含 cryptographySettings [ >元素。\< ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb363-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="bb363-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bb363-104">\<configuration></span></span>  
<span data-ttu-id="bb363-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="bb363-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb363-106">語法</span><span class="sxs-lookup"><span data-stu-id="bb363-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb363-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bb363-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bb363-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bb363-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb363-109">屬性</span><span class="sxs-lookup"><span data-stu-id="bb363-109">Attributes</span></span>  
 <span data-ttu-id="bb363-110">無。</span><span class="sxs-lookup"><span data-stu-id="bb363-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb363-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bb363-111">Child Elements</span></span>  
  
|<span data-ttu-id="bb363-112">項目</span><span class="sxs-lookup"><span data-stu-id="bb363-112">Element</span></span>|<span data-ttu-id="bb363-113">說明</span><span class="sxs-lookup"><span data-stu-id="bb363-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="bb363-114">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="bb363-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb363-115">父項目</span><span class="sxs-lookup"><span data-stu-id="bb363-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bb363-116">項目</span><span class="sxs-lookup"><span data-stu-id="bb363-116">Element</span></span>|<span data-ttu-id="bb363-117">描述</span><span class="sxs-lookup"><span data-stu-id="bb363-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb363-118">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bb363-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bb363-119">範例</span><span class="sxs-lookup"><span data-stu-id="bb363-119">Example</span></span>  
 <span data-ttu-id="bb363-120">下列範例顯示如何使用 **\<mscorlib >** 專案來參考密碼編譯類別, 以及設定執行時間。</span><span class="sxs-lookup"><span data-stu-id="bb363-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="bb363-121">接著, 您可以將字串 "RSA" 傳遞給<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 並<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>使用方法來`MyCryptoRSAClass`傳回物件。</span><span class="sxs-lookup"><span data-stu-id="bb363-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb363-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb363-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="bb363-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="bb363-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bb363-124">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bb363-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bb363-125">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="bb363-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="bb363-126">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="bb363-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
