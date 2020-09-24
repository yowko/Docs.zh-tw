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
ms.openlocfilehash: 0215851f83a13ee48547144f08c5c693ec2d90bf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149526"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="774a5-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="774a5-102">Cryptography Settings Schema</span></span>

<span data-ttu-id="774a5-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="774a5-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="774a5-104">項目</span><span class="sxs-lookup"><span data-stu-id="774a5-104">Element</span></span>|<span data-ttu-id="774a5-105">描述</span><span class="sxs-lookup"><span data-stu-id="774a5-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="774a5-106">包含密碼編譯類別的清單，這些類別在專案中具有易記名稱的對應 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="774a5-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="774a5-107">包含密碼編譯類別，該類別在專案中具有易記名稱的對應 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="774a5-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="774a5-108">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="774a5-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="774a5-109">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="774a5-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="774a5-110">**\<mscorlib>** 密碼編譯設定的元素</span><span class="sxs-lookup"><span data-stu-id="774a5-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="774a5-111">包含 **\<cryptographySettings>** 元素。</span><span class="sxs-lookup"><span data-stu-id="774a5-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="774a5-112">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="774a5-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="774a5-113">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="774a5-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="774a5-114">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="774a5-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="774a5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="774a5-115">See also</span></span>

- [<span data-ttu-id="774a5-116">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="774a5-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="774a5-117">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="774a5-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
