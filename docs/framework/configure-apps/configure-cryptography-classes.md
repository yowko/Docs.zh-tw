---
title: 設定密碼編譯類別
description: 瞭解電腦系統管理員如何設定 .NET 和應用程式所使用的預設密碼編譯演算法和演算法實作為。
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5262dfca914fd5306297ea9535bcef3d2088d107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165204"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="8ed5d-103">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="8ed5d-103">Configuring Cryptography Classes</span></span>

<span data-ttu-id="8ed5d-104">Windows SDK 可讓電腦系統管理員設定 .NET Framework 和適當撰寫的應用程式所使用的預設密碼編譯演算法和演算法執行。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-104">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="8ed5d-105">例如，具有自己的密碼編譯演算法執行的企業，可以使該執行成為預設值，而不是 Windows SDK 中所附的實作為。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-105">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="8ed5d-106">雖然使用加密的受控應用程式一律可以選擇明確地系結至特定的執行，但建議使用加密設定系統建立密碼編譯物件。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-106">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ed5d-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="8ed5d-107">In This Section</span></span>  

 [<span data-ttu-id="8ed5d-108">將演算法名稱對應至密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="8ed5d-108">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="8ed5d-109">說明如何將演算法名稱對應至密碼編譯類別。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-109">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="8ed5d-110">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="8ed5d-110">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="8ed5d-111">描述如何將物件識別碼對應至密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-111">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ed5d-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="8ed5d-112">Related Sections</span></span>  

 [<span data-ttu-id="8ed5d-113">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="8ed5d-113">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="8ed5d-114">概要說明 Windows SDK 所提供的密碼編譯服務。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-114">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="8ed5d-115">密碼編譯設定架構</span><span class="sxs-lookup"><span data-stu-id="8ed5d-115">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="8ed5d-116">說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="8ed5d-116">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
