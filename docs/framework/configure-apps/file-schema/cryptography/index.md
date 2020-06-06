---
title: 密碼編譯設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087998"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="05b1f-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="05b1f-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="05b1f-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="05b1f-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="05b1f-104">元素</span><span class="sxs-lookup"><span data-stu-id="05b1f-104">Element</span></span>|<span data-ttu-id="05b1f-105">描述</span><span class="sxs-lookup"><span data-stu-id="05b1f-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="05b1f-106">包含在專案中有易記名稱對應的密碼編譯類別清單 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="05b1f-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="05b1f-107">包含在專案中具有易記名稱對應的密碼編譯類別 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="05b1f-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="05b1f-108">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="05b1f-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="05b1f-109">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="05b1f-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="05b1f-110">**\<mscorlib>** 密碼編譯設定的元素</span><span class="sxs-lookup"><span data-stu-id="05b1f-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="05b1f-111">包含 **\<cryptographySettings>** 元素。</span><span class="sxs-lookup"><span data-stu-id="05b1f-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="05b1f-112">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="05b1f-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="05b1f-113">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="05b1f-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="05b1f-114">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="05b1f-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05b1f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05b1f-115">See also</span></span>

- [<span data-ttu-id="05b1f-116">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="05b1f-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="05b1f-117">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="05b1f-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
