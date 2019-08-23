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
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927776"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="6c1c7-102">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="6c1c7-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="6c1c7-103">此 Windows SDK 可讓電腦系統管理員設定 .NET Framework 和適當撰寫的應用程式所使用的預設密碼編譯演算法和演算法實現。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="6c1c7-104">例如, 擁有自己執行密碼編譯演算法的企業, 可以讓該執行成為預設值, 而不是在 Windows SDK 中隨附的執行。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="6c1c7-105">雖然使用密碼編譯的受控應用程式一律會選擇明確系結至特定的執行, 但建議使用加密設定系統來建立密碼編譯物件。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c1c7-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="6c1c7-106">In This Section</span></span>  
 [<span data-ttu-id="6c1c7-107">將演算法名稱對應至密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="6c1c7-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="6c1c7-108">說明如何將演算法名稱對應至密碼編譯類別。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="6c1c7-109">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="6c1c7-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="6c1c7-110">描述如何將物件識別碼對應至密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6c1c7-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="6c1c7-111">Related Sections</span></span>  
 [<span data-ttu-id="6c1c7-112">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="6c1c7-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="6c1c7-113">提供 Windows SDK 所提供的密碼編譯服務的總覽。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="6c1c7-114">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6c1c7-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="6c1c7-115">說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="6c1c7-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
