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
ms.openlocfilehash: b5c1178519601d7dcb7c5b3014f413b6436746fb
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816168"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="a1fc3-102">設定密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="a1fc3-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="a1fc3-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]可讓電腦系統管理員，若要設定的預設密碼編譯演算法和.NET Framework 和適當地撰寫的應用程式使用的演算法實作。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="a1fc3-104">比方說，企業有它自己的密碼編譯演算法的實作可以在 Windows SDK 中進行而不是實作的預設值隨附該實作。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="a1fc3-105">雖然永遠都可以選擇使用加密的受控應用程式，明確繫結至特定的實作，但建議他們使用密碼編譯組態系統建立密碼編譯物件。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1fc3-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="a1fc3-106">In This Section</span></span>  
 [<span data-ttu-id="a1fc3-107">將演算法名稱對應至密碼編譯類別</span><span class="sxs-lookup"><span data-stu-id="a1fc3-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="a1fc3-108">描述如何將演算法名稱對應至密碼編譯類別。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="a1fc3-109">對應物件識別項至密碼編譯演算法</span><span class="sxs-lookup"><span data-stu-id="a1fc3-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="a1fc3-110">描述如何將物件識別項對應至密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1fc3-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="a1fc3-111">Related Sections</span></span>  
 [<span data-ttu-id="a1fc3-112">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="a1fc3-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="a1fc3-113">提供 Windows SDK 所提供的密碼編譯服務的概觀。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="a1fc3-114">密碼編譯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a1fc3-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="a1fc3-115">說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。</span><span class="sxs-lookup"><span data-stu-id="a1fc3-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
