---
title: 設定密碼編譯類別
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b9153b4525063d6c52e22d754d68ffa42e914d00
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196943"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="676a0-102">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="676a0-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="676a0-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]可讓電腦系統管理員，若要設定的預設密碼編譯演算法和.NET Framework 和適當地撰寫的應用程式使用的演算法實作。</span><span class="sxs-lookup"><span data-stu-id="676a0-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="676a0-104">例如，企業有它自己的密碼編譯演算法的實作可以讓該實作的預設值，而不是隨附於實作[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="676a0-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="676a0-105">雖然永遠都可以選擇使用加密的受控應用程式，明確繫結至特定的實作，但建議他們使用密碼編譯組態系統建立密碼編譯物件。</span><span class="sxs-lookup"><span data-stu-id="676a0-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="676a0-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="676a0-106">In This Section</span></span>  
 [<span data-ttu-id="676a0-107">將演算法名稱對應至密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="676a0-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="676a0-108">描述如何將演算法名稱對應至密碼編譯類別。</span><span class="sxs-lookup"><span data-stu-id="676a0-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="676a0-109">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="676a0-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="676a0-110">描述如何將物件識別項對應至密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="676a0-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="676a0-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="676a0-111">Related Sections</span></span>  
 [<span data-ttu-id="676a0-112">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="676a0-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="676a0-113">提供的密碼編譯服務提供概觀[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="676a0-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="676a0-114">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="676a0-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="676a0-115">說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="676a0-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
