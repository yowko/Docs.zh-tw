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
ms.openlocfilehash: 00b04cc2175f4bb4cc0b74602cd3c26f4a4e342f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184453"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="a2cef-102">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a2cef-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="a2cef-103">密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="a2cef-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="a2cef-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="a2cef-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="a2cef-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="a2cef-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="a2cef-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="a2cef-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="a2cef-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="a2cef-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="a2cef-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="a2cef-113">項目</span><span class="sxs-lookup"><span data-stu-id="a2cef-113">Element</span></span>|<span data-ttu-id="a2cef-114">描述</span><span class="sxs-lookup"><span data-stu-id="a2cef-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2cef-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="a2cef-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="a2cef-116">包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="a2cef-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="a2cef-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="a2cef-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="a2cef-118">包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。</span><span class="sxs-lookup"><span data-stu-id="a2cef-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="a2cef-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="a2cef-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="a2cef-120">包含密碼編譯設定。</span><span class="sxs-lookup"><span data-stu-id="a2cef-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="a2cef-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="a2cef-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="a2cef-122">包含易記名稱的類別對應。</span><span class="sxs-lookup"><span data-stu-id="a2cef-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="a2cef-123">密碼編譯設定的 **\<mscorlib>** 項目</span><span class="sxs-lookup"><span data-stu-id="a2cef-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="a2cef-124">包含 **\<cryptographySettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="a2cef-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="a2cef-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="a2cef-126">將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cef-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="a2cef-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="a2cef-128">將 ASN.1 物件識別碼 (OID) 對應至易記名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cef-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="a2cef-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="a2cef-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="a2cef-130">包含類別的 ASN.1 OID 對應。</span><span class="sxs-lookup"><span data-stu-id="a2cef-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2cef-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2cef-131">See also</span></span>

- [<span data-ttu-id="a2cef-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a2cef-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a2cef-133">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="a2cef-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
