---
title: 作法：使用資料保護
description: 瞭解如何藉由存取 .NET 中的資料保護 API (DPAPI) 來使用資料保護。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: ed1b18e2c6456b53559e8fb7e989f148fefd35c7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820094"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="3041a-103">作法：使用資料保護</span><span class="sxs-lookup"><span data-stu-id="3041a-103">How to: Use Data Protection</span></span>

> [!NOTE]
> <span data-ttu-id="3041a-104">本文適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="3041a-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="3041a-105">如需 ASP.NET Core 的詳細資訊，請參閱 [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)。</span><span class="sxs-lookup"><span data-stu-id="3041a-105">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="3041a-106">.NET 提供資料保護 API (DPAPI) 的存取權，讓您可以使用目前使用者帳戶或電腦的資訊來加密資料。</span><span class="sxs-lookup"><span data-stu-id="3041a-106">.NET provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="3041a-107">當您使用 DPAPI 時，會減少明確產生並儲存密碼編譯金鑰的困難問題。</span><span class="sxs-lookup"><span data-stu-id="3041a-107">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
<span data-ttu-id="3041a-108">使用 <xref:System.Security.Cryptography.ProtectedData> 類別來加密位元組陣列的複本。</span><span class="sxs-lookup"><span data-stu-id="3041a-108">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="3041a-109">這項功能在 .NET Framework、.NET Core 和 .NET 5 中都有提供。</span><span class="sxs-lookup"><span data-stu-id="3041a-109">This functionality is available in .NET Framework, .NET Core, and .NET 5.</span></span>  <span data-ttu-id="3041a-110">您可以指定由目前使用者帳戶加密的資料只能由相同的使用者帳戶解密，或是您可以指定目前使用者帳戶加密的資料可以由電腦上的任何帳戶解密。</span><span class="sxs-lookup"><span data-stu-id="3041a-110">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="3041a-111">請參閱 <xref:System.Security.Cryptography.DataProtectionScope> 列舉，以取得 <xref:System.Security.Cryptography.ProtectedData> 選項的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="3041a-111">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
## <a name="encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="3041a-112">使用資料保護將資料加密至檔案或資料流程</span><span class="sxs-lookup"><span data-stu-id="3041a-112">Encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="3041a-113">建立隨機的 entropy。</span><span class="sxs-lookup"><span data-stu-id="3041a-113">Create random entropy.</span></span>  
  
2. <span data-ttu-id="3041a-114">呼叫靜態 <xref:System.Security.Cryptography.ProtectedData.Protect%2A> 方法並傳遞要加密的位元組陣列、entropy 及資料保護範圍。</span><span class="sxs-lookup"><span data-stu-id="3041a-114">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="3041a-115">將加密的資料寫入檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="3041a-115">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="3041a-116">使用資料保護從檔案或資料流解密資料</span><span class="sxs-lookup"><span data-stu-id="3041a-116">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="3041a-117">從檔案或資料流讀取加密的資料。</span><span class="sxs-lookup"><span data-stu-id="3041a-117">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="3041a-118">呼叫靜態 <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> 方法並傳遞要解密的位元組陣列及資料保護範圍。</span><span class="sxs-lookup"><span data-stu-id="3041a-118">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3041a-119">範例</span><span class="sxs-lookup"><span data-stu-id="3041a-119">Example</span></span>

<span data-ttu-id="3041a-120">下列程式碼範例示範兩種形式的加密和解密。</span><span class="sxs-lookup"><span data-stu-id="3041a-120">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="3041a-121">首先，程式碼範例會加密，然後再解密記憶體中的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3041a-121">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="3041a-122">接下來，程式碼範例會加密位元組陣列的複本、將它儲存至檔案、從檔案載入資料，然後再解密資料。</span><span class="sxs-lookup"><span data-stu-id="3041a-122">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="3041a-123">此範例會顯示原始資料、加密的資料和解密的資料。</span><span class="sxs-lookup"><span data-stu-id="3041a-123">The example displays the original data, the encrypted data, and the decrypted data.</span></span>

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3041a-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3041a-124">Compiling the Code</span></span>  

<span data-ttu-id="3041a-125">此範例只會在目標為 .NET Framework 並在 Windows 上執行時，才會進行編譯和執行。</span><span class="sxs-lookup"><span data-stu-id="3041a-125">This example compiles and runs only when targeting .NET Framework and running on Windows.</span></span>

- <span data-ttu-id="3041a-126">包含 `System.Security.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="3041a-126">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="3041a-127">包含 <xref:System>、<xref:System.IO>、<xref:System.Security.Cryptography> 和 <xref:System.Text> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3041a-127">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3041a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="3041a-128">See also</span></span>

- [<span data-ttu-id="3041a-129">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="3041a-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="3041a-130">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="3041a-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="3041a-131">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="3041a-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [<span data-ttu-id="3041a-132">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="3041a-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
