---
title: 作法：存取硬體加密裝置
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: 7cd3aab80a8388c1d4ce08e4ae94aae84cfff239
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557134"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="25c8f-102">作法：存取硬體加密裝置</span><span class="sxs-lookup"><span data-stu-id="25c8f-102">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="25c8f-103">本文適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="25c8f-103">This article applies to Windows.</span></span>

<span data-ttu-id="25c8f-104">您可以使用 <xref:System.Security.Cryptography.CspParameters> 類別來存取硬體加密裝置。</span><span class="sxs-lookup"><span data-stu-id="25c8f-104">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="25c8f-105">例如，您可以使用這個類別來整合應用程式與智慧卡、硬體亂數產生器或特定密碼編譯演算法的硬體實作。</span><span class="sxs-lookup"><span data-stu-id="25c8f-105">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="25c8f-106"><xref:System.Security.Cryptography.CspParameters> 類別會建立存取正確安裝之硬體加密裝置的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="25c8f-106">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="25c8f-107">您可以使用登錄編輯程式 (Regedit.exe) 檢查下列登錄機碼，以驗證 CSP 的可用性：HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider。</span><span class="sxs-lookup"><span data-stu-id="25c8f-107">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="25c8f-108">使用金鑰卡簽署資料</span><span class="sxs-lookup"><span data-stu-id="25c8f-108">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="25c8f-109">建立 <xref:System.Security.Cryptography.CspParameters> 類別的新執行個體，並將整數提供者類型和提供者名稱傳遞給建構函式。</span><span class="sxs-lookup"><span data-stu-id="25c8f-109">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="25c8f-110">將適當的旗標傳遞給新建立之 <xref:System.Security.Cryptography.CspParameters> 物件的 <xref:System.Security.Cryptography.CspParameters.Flags%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="25c8f-110">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="25c8f-111">例如，傳遞 <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> 旗標。</span><span class="sxs-lookup"><span data-stu-id="25c8f-111">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="25c8f-112">建立 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 類別的新執行個體 (例如，<xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別)，並傳遞 <xref:System.Security.Cryptography.CspParameters> 物件給建構函式。</span><span class="sxs-lookup"><span data-stu-id="25c8f-112">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="25c8f-113">使用其中一個 `Sign` 方法簽署資料，並使用其中一個 `Verify` 方法驗證資料。</span><span class="sxs-lookup"><span data-stu-id="25c8f-113">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="25c8f-114">使用硬體亂數產生器產生亂數</span><span class="sxs-lookup"><span data-stu-id="25c8f-114">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="25c8f-115">建立 <xref:System.Security.Cryptography.CspParameters> 類別的新執行個體，並將整數提供者類型和提供者名稱傳遞給建構函式。</span><span class="sxs-lookup"><span data-stu-id="25c8f-115">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="25c8f-116">建立 <xref:System.Security.Cryptography.RNGCryptoServiceProvider> 的新執行個體，並傳遞 <xref:System.Security.Cryptography.CspParameters> 物件給建構函式。</span><span class="sxs-lookup"><span data-stu-id="25c8f-116">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="25c8f-117">使用 <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> 或 <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> 方法建立亂數。</span><span class="sxs-lookup"><span data-stu-id="25c8f-117">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25c8f-118">範例</span><span class="sxs-lookup"><span data-stu-id="25c8f-118">Example</span></span>

<span data-ttu-id="25c8f-119">下列程式碼範例示範如何使用智慧卡簽署資料。</span><span class="sxs-lookup"><span data-stu-id="25c8f-119">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="25c8f-120">程式碼範例會建立公開智慧卡的 <xref:System.Security.Cryptography.CspParameters> 物件，然後使用 CSP 初始化 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件。</span><span class="sxs-lookup"><span data-stu-id="25c8f-120">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="25c8f-121">程式碼範例接著會簽署並驗證某些資料。</span><span class="sxs-lookup"><span data-stu-id="25c8f-121">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="25c8f-122">由於 SHA1 的衝突問題，我們建議 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="25c8f-122">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25c8f-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="25c8f-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="25c8f-124">包含 <xref:System> 和 <xref:System.Security.Cryptography> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="25c8f-124">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="25c8f-125">您的電腦上必須安裝智慧卡讀卡機和驅動程式。</span><span class="sxs-lookup"><span data-stu-id="25c8f-125">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="25c8f-126">您必須使用讀卡機的特定資訊初始化 <xref:System.Security.Cryptography.CspParameters> 物件。</span><span class="sxs-lookup"><span data-stu-id="25c8f-126">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="25c8f-127">如需詳細資訊，請參閱讀卡機的文件。</span><span class="sxs-lookup"><span data-stu-id="25c8f-127">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="25c8f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25c8f-128">See also</span></span>

- [<span data-ttu-id="25c8f-129">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="25c8f-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="25c8f-130">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="25c8f-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="25c8f-131">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="25c8f-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="25c8f-132">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="25c8f-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
