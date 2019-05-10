---
title: HOW TO：使用資料保護
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dc8c75d3c8c91d974388779528deff16453d852
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602544"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="cd897-102">HOW TO：使用資料保護</span><span class="sxs-lookup"><span data-stu-id="cd897-102">How to: Use Data Protection</span></span>
<span data-ttu-id="cd897-103">.NET Framework 提供資料保護 API (DPAPI) 的存取，這可讓您使用目前使用者帳戶或電腦的資訊來加密資料。</span><span class="sxs-lookup"><span data-stu-id="cd897-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="cd897-104">當您使用 DPAPI 時，會減少明確產生並儲存密碼編譯金鑰的困難問題。</span><span class="sxs-lookup"><span data-stu-id="cd897-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="cd897-105">使用 <xref:System.Security.Cryptography.ProtectedMemory> 類別來加密記憶體中的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="cd897-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="cd897-106">這項功能提供於 Microsoft Windows XP 和更新版本的作業系統。</span><span class="sxs-lookup"><span data-stu-id="cd897-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="cd897-107">您可以指定由目前處理序加密的記憶體只能由目前的處理序解密、可由所有處理序解密，或是可從相同的使用者內容解密。</span><span class="sxs-lookup"><span data-stu-id="cd897-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="cd897-108">請參閱 <xref:System.Security.Cryptography.MemoryProtectionScope> 列舉，以取得 <xref:System.Security.Cryptography.ProtectedMemory> 選項的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="cd897-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="cd897-109">使用 <xref:System.Security.Cryptography.ProtectedData> 類別來加密位元組陣列的複本。</span><span class="sxs-lookup"><span data-stu-id="cd897-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="cd897-110">這項功能提供於 Microsoft Windows 2000 和更新版本的作業系統。</span><span class="sxs-lookup"><span data-stu-id="cd897-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="cd897-111">您可以指定由目前使用者帳戶加密的資料只能由相同的使用者帳戶解密，或是您可以指定目前使用者帳戶加密的資料可以由電腦上的任何帳戶解密。</span><span class="sxs-lookup"><span data-stu-id="cd897-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="cd897-112">請參閱 <xref:System.Security.Cryptography.DataProtectionScope> 列舉，以取得 <xref:System.Security.Cryptography.ProtectedData> 選項的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="cd897-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="cd897-113">使用資料保護來加密記憶體中的資料</span><span class="sxs-lookup"><span data-stu-id="cd897-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="cd897-114">呼叫靜態 <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> 方法並傳遞要加密的位元組陣列、entropy 及記憶體保護範圍。</span><span class="sxs-lookup"><span data-stu-id="cd897-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="cd897-115">使用資料保護來解密記憶體中的資料</span><span class="sxs-lookup"><span data-stu-id="cd897-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="cd897-116">呼叫靜態 <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> 方法並傳遞要解密的位元組陣列及記憶體保護範圍。</span><span class="sxs-lookup"><span data-stu-id="cd897-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="cd897-117">使用資料保護將資料加密到檔案或資料流</span><span class="sxs-lookup"><span data-stu-id="cd897-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="cd897-118">建立隨機的 entropy。</span><span class="sxs-lookup"><span data-stu-id="cd897-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="cd897-119">呼叫靜態 <xref:System.Security.Cryptography.ProtectedData.Protect%2A> 方法並傳遞要加密的位元組陣列、entropy 及資料保護範圍。</span><span class="sxs-lookup"><span data-stu-id="cd897-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="cd897-120">將加密的資料寫入檔案或資料流。</span><span class="sxs-lookup"><span data-stu-id="cd897-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="cd897-121">使用資料保護從檔案或資料流解密資料</span><span class="sxs-lookup"><span data-stu-id="cd897-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="cd897-122">從檔案或資料流讀取加密的資料。</span><span class="sxs-lookup"><span data-stu-id="cd897-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="cd897-123">呼叫靜態 <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> 方法並傳遞要解密的位元組陣列及資料保護範圍。</span><span class="sxs-lookup"><span data-stu-id="cd897-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd897-124">範例</span><span class="sxs-lookup"><span data-stu-id="cd897-124">Example</span></span>  
 <span data-ttu-id="cd897-125">下列程式碼範例示範兩種形式的加密和解密。</span><span class="sxs-lookup"><span data-stu-id="cd897-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="cd897-126">首先，程式碼範例會加密，然後再解密記憶體中的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="cd897-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="cd897-127">接下來，程式碼範例會加密位元組陣列的複本、將它儲存至檔案、從檔案載入資料，然後再解密資料。</span><span class="sxs-lookup"><span data-stu-id="cd897-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="cd897-128">此範例會顯示原始資料、加密的資料和解密的資料。</span><span class="sxs-lookup"><span data-stu-id="cd897-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd897-129">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cd897-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="cd897-130">包含 `System.Security.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="cd897-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="cd897-131">包含 <xref:System>、<xref:System.IO>、<xref:System.Security.Cryptography> 和 <xref:System.Text> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="cd897-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd897-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd897-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
