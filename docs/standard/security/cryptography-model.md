---
title: .NET Framework 密碼編譯模型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ced7ed2cb8d3ae3bb24211c6e7dafd1744fb9559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587452"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="c622a-102">.NET Framework 密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="c622a-102">.NET Framework Cryptography Model</span></span>
<span data-ttu-id="c622a-103">.NET Framework 提供許多標準密碼編譯演算法的實作。</span><span class="sxs-lookup"><span data-stu-id="c622a-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="c622a-104">這些演算法容易使用，並且具有最安全的可能預設屬性。</span><span class="sxs-lookup"><span data-stu-id="c622a-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="c622a-105">此外，.NET Framework 的物件繼承、資料流設計與組態的密碼編譯模型非常具可擴充性。</span><span class="sxs-lookup"><span data-stu-id="c622a-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>  
  
## <a name="object-inheritance"></a><span data-ttu-id="c622a-106">物件繼承</span><span class="sxs-lookup"><span data-stu-id="c622a-106">Object Inheritance</span></span>  
 <span data-ttu-id="c622a-107">.NET Framework 安全性系統會實作衍生類別繼承的可擴充模式。</span><span class="sxs-lookup"><span data-stu-id="c622a-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="c622a-108">階層如下所述：</span><span class="sxs-lookup"><span data-stu-id="c622a-108">The hierarchy is as follows:</span></span>  
  
-   <span data-ttu-id="c622a-109">演算法類型類別，例如 <xref:System.Security.Cryptography.SymmetricAlgorithm>、<xref:System.Security.Cryptography.AsymmetricAlgorithm> 或 <xref:System.Security.Cryptography.HashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="c622a-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="c622a-110">這個層級是抽象的。</span><span class="sxs-lookup"><span data-stu-id="c622a-110">This level is abstract.</span></span>  
  
-   <span data-ttu-id="c622a-111">繼承自演算法類型類別的演算法類別；例如，<xref:System.Security.Cryptography.Aes><xref:System.Security.Cryptography.RC2> 或 <xref:System.Security.Cryptography.ECDiffieHellman>。</span><span class="sxs-lookup"><span data-stu-id="c622a-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="c622a-112">這個層級是抽象的。</span><span class="sxs-lookup"><span data-stu-id="c622a-112">This level is abstract.</span></span>  
  
-   <span data-ttu-id="c622a-113">繼承自演算法類別的演算法類別實作；例如，<xref:System.Security.Cryptography.AesManaged><xref:System.Security.Cryptography.RC2CryptoServiceProvider> 或 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。</span><span class="sxs-lookup"><span data-stu-id="c622a-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="c622a-114">這個層級已完全實作。</span><span class="sxs-lookup"><span data-stu-id="c622a-114">This level is fully implemented.</span></span>  
  
 <span data-ttu-id="c622a-115">使用這種衍生類別的模式，就可以輕鬆地加入新的演算法或現有演算法的新實作。</span><span class="sxs-lookup"><span data-stu-id="c622a-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="c622a-116">例如，若要建立新的公開金鑰演算法，您會繼承自 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 類別。</span><span class="sxs-lookup"><span data-stu-id="c622a-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="c622a-117">若要建立特定演算法的新實作，您會建立該演算法的非抽象衍生類別。</span><span class="sxs-lookup"><span data-stu-id="c622a-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="c622a-118">.NET Framework 中的演算法實作方式</span><span class="sxs-lookup"><span data-stu-id="c622a-118">How Algorithms Are Implemented in the .NET Framework</span></span>  
 <span data-ttu-id="c622a-119">做為可供演算法使用的不同實作方式範例，請考慮對稱演算法。</span><span class="sxs-lookup"><span data-stu-id="c622a-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="c622a-120">所有對稱演算法的基礎是 <xref:System.Security.Cryptography.SymmetricAlgorithm>，它由下列演算法所繼承：</span><span class="sxs-lookup"><span data-stu-id="c622a-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <span data-ttu-id="c622a-121"><xref:System.Security.Cryptography.Aes> 會由兩個類別繼承：<xref:System.Security.Cryptography.AesCryptoServiceProvider> 和 <xref:System.Security.Cryptography.AesManaged>。</span><span class="sxs-lookup"><span data-stu-id="c622a-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="c622a-122"><xref:System.Security.Cryptography.AesCryptoServiceProvider> 類別是 Aes 的 Windows 密碼編譯 API (CAPI) 實作的包裝函式，而 <xref:System.Security.Cryptography.AesManaged> 類別完全以 managed 程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="c622a-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="c622a-123">除了 Managed 和 CAPI 實作，另外還有第三種類型的實作，Cryptography Next Generation (CNG)。</span><span class="sxs-lookup"><span data-stu-id="c622a-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="c622a-124">CNG 演算法的範例是 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。</span><span class="sxs-lookup"><span data-stu-id="c622a-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="c622a-125">CNG 演算法可用於 Windows Vista 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="c622a-125">CNG algorithms are available on Windows Vista and later.</span></span>  
  
 <span data-ttu-id="c622a-126">您可以選擇哪一個實作最適合您。</span><span class="sxs-lookup"><span data-stu-id="c622a-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="c622a-127">可支援 .NET Framework 的所有平台上都可使用 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="c622a-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="c622a-128">CAPI 實作可用於較舊的作業系統，並且不會再開發。</span><span class="sxs-lookup"><span data-stu-id="c622a-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="c622a-129">CNG 是最新的實作，將在這裡進行新的開發工作。</span><span class="sxs-lookup"><span data-stu-id="c622a-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="c622a-130">不過，Manged 實作未經美國聯邦資訊處理標準 (FIPS) 認證，而且可能比包裝函式類別慢。</span><span class="sxs-lookup"><span data-stu-id="c622a-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>  
  
## <a name="stream-design"></a><span data-ttu-id="c622a-131">資料流設計</span><span class="sxs-lookup"><span data-stu-id="c622a-131">Stream Design</span></span>  
 <span data-ttu-id="c622a-132">Common Language Runtime 使用資料流為導向的設計來實作對稱演算法和雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="c622a-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="c622a-133">這項設計的核心是 <xref:System.Security.Cryptography.CryptoStream> 類別，它衍生自 <xref:System.IO.Stream> 類別。</span><span class="sxs-lookup"><span data-stu-id="c622a-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="c622a-134">資料流為基礎的密碼編譯物件支援單一標準介面 (`CryptoStream`)，以便處理物件的資料傳輸部分。</span><span class="sxs-lookup"><span data-stu-id="c622a-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="c622a-135">由於所有物件都建置在標準介面上，您可以將多個物件鏈結在一起 (例如雜湊物件其後跟著加密物件)，且您可以對資料執行多項作業，而不需要任何中繼儲存體。</span><span class="sxs-lookup"><span data-stu-id="c622a-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="c622a-136">資料流模型也可讓您從較小的物件建置物件。</span><span class="sxs-lookup"><span data-stu-id="c622a-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="c622a-137">例如，結合的加密和雜湊演算法可視為單一資料流物件，雖然這個物件可能是從一組資料流物件建置而來。</span><span class="sxs-lookup"><span data-stu-id="c622a-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>  
  
## <a name="cryptographic-configuration"></a><span data-ttu-id="c622a-138">密碼編譯組態</span><span class="sxs-lookup"><span data-stu-id="c622a-138">Cryptographic Configuration</span></span>  
 <span data-ttu-id="c622a-139">密碼編譯組態可讓您將演算法的特定實作，解析為演算法名稱，允許擴充 .NET Framework 密碼編譯類別。</span><span class="sxs-lookup"><span data-stu-id="c622a-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="c622a-140">您可以加入自己的演算法硬體或軟體實作，並將實作對應到您選擇的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="c622a-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="c622a-141">如果在組態檔中未指定演算法，會使用預設設定。</span><span class="sxs-lookup"><span data-stu-id="c622a-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="c622a-142">如需有關密碼編譯組態的詳細資訊，請參閱[設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="c622a-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>  
  
## <a name="choosing-an-algorithm"></a><span data-ttu-id="c622a-143">選擇演算法</span><span class="sxs-lookup"><span data-stu-id="c622a-143">Choosing an Algorithm</span></span>  
 <span data-ttu-id="c622a-144">您選取演算法時可能有不同的原因：例如，為了資料完整性、為了資料隱私權，或是為了產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="c622a-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="c622a-145">對稱和雜湊演算法是要用來出於完整性的原因 (防止變更) 或隱私權的原因 (防止檢視) 保護資料。</span><span class="sxs-lookup"><span data-stu-id="c622a-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="c622a-146">雜湊演算法主要用於資料完整性。</span><span class="sxs-lookup"><span data-stu-id="c622a-146">Hash algorithms are used primarily for data integrity.</span></span>  
  
 <span data-ttu-id="c622a-147">以下是依應用程式的建議演算法清單：</span><span class="sxs-lookup"><span data-stu-id="c622a-147">Here is a list of recommended algorithms by application:</span></span>  
  
-   <span data-ttu-id="c622a-148">資料隱私權：</span><span class="sxs-lookup"><span data-stu-id="c622a-148">Data privacy:</span></span>  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   <span data-ttu-id="c622a-149">資料完整性：</span><span class="sxs-lookup"><span data-stu-id="c622a-149">Data integrity:</span></span>  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   <span data-ttu-id="c622a-150">數位簽章：</span><span class="sxs-lookup"><span data-stu-id="c622a-150">Digital signature:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="c622a-151">金鑰交換：</span><span class="sxs-lookup"><span data-stu-id="c622a-151">Key exchange:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="c622a-152">亂數產生：</span><span class="sxs-lookup"><span data-stu-id="c622a-152">Random number generation:</span></span>  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   <span data-ttu-id="c622a-153">從密碼產生金鑰：</span><span class="sxs-lookup"><span data-stu-id="c622a-153">Generating a key from a password:</span></span>  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a><span data-ttu-id="c622a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c622a-154">See Also</span></span>  
 [<span data-ttu-id="c622a-155">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="c622a-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 
