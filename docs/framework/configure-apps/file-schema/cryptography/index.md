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
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664288"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="7eecd-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7eecd-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="7eecd-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="7eecd-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="7eecd-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="7eecd-105"> **\<mscorlib>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="7eecd-106"> **\<cryptographySettings>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="7eecd-107"> **\<cryptoNameMapping>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="7eecd-108"> **\<cryptoClasses>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="7eecd-109"> **\<cryptoClass>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="7eecd-110"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="7eecd-111"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="7eecd-112"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="7eecd-113">項目</span><span class="sxs-lookup"><span data-stu-id="7eecd-113">Element</span></span>|<span data-ttu-id="7eecd-114">描述</span><span class="sxs-lookup"><span data-stu-id="7eecd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eecd-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="7eecd-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="7eecd-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="7eecd-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="7eecd-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="7eecd-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="7eecd-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="7eecd-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="7eecd-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="7eecd-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="7eecd-120">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="7eecd-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="7eecd-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="7eecd-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="7eecd-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="7eecd-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="7eecd-123">密碼編譯設定的 **\<mscorlib>** 項目</span><span class="sxs-lookup"><span data-stu-id="7eecd-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="7eecd-124">包含 **\<cryptographySettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="7eecd-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="7eecd-125"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="7eecd-126">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7eecd-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="7eecd-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="7eecd-128">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7eecd-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="7eecd-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="7eecd-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="7eecd-130">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="7eecd-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7eecd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eecd-131">See also</span></span>

- [<span data-ttu-id="7eecd-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7eecd-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7eecd-133">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="7eecd-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
