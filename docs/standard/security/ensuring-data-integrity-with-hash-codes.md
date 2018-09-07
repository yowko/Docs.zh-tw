---
title: 使用雜湊程式碼確定資料完整性
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075581"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="d1c6a-102">使用雜湊程式碼確定資料完整性</span><span class="sxs-lookup"><span data-stu-id="d1c6a-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="d1c6a-103">雜湊值是可唯一識別資料的固定長度數值。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="d1c6a-104">雜湊值以較小的數值代表大量的資料，所以可和數位簽章一起使用。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="d1c6a-105">比起簽署更大的值，簽署雜湊值更有效率。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="d1c6a-106">如需驗證透過不安全的通道傳送的資料完整性，雜湊值會相當有用。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="d1c6a-107">可比較已接收資料的雜湊值和該資料傳送時的雜湊值，來判斷資料是否已變更。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="d1c6a-108">本主題描述如何使用 <xref:System.Security.Cryptography?displayProperty=nameWithType> 命名空間中的類別來產生及驗證雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="d1c6a-109">產生雜湊</span><span class="sxs-lookup"><span data-stu-id="d1c6a-109">Generating a Hash</span></span>  
 <span data-ttu-id="d1c6a-110">Managed 雜湊類別可以雜湊位元組陣列或 Managed 資料流物件。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="d1c6a-111">以下範例使用 SHA1 雜湊演算法來建立字串的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="d1c6a-112">此範例會使用 <xref:System.Text.UnicodeEncoding> 類別，將字串轉換成使用 <xref:System.Security.Cryptography.SHA1Managed> 類別雜湊的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="d1c6a-113">接著會在主控台顯示雜湊值。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="d1c6a-114">此程式碼會在主控台顯示下列字串：</span><span class="sxs-lookup"><span data-stu-id="d1c6a-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="d1c6a-115">驗證雜湊</span><span class="sxs-lookup"><span data-stu-id="d1c6a-115">Verifying a Hash</span></span>  
 <span data-ttu-id="d1c6a-116">若要判斷資料完整性，可將資料和雜湊值相比較。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="d1c6a-117">通常，資料會在特定時間進行雜湊，該雜湊值則會受某種方式保護。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="d1c6a-118">在一段期間之後，可再重新雜湊資料，並與受保護的值相比較。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="d1c6a-119">如果雜湊值相符，資料就未受變更。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="d1c6a-120">如果值不相符，則資料已損毀。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="d1c6a-121">為了讓這個系統運作，對於來自未受信任的所有對象，都必須將受保護的雜湊加密或保密。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="d1c6a-122">下列範例會將字串的前一個雜湊值與新的雜湊值相比較。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="d1c6a-123">此範例會在雜湊值的每個位元組中執行迴圈，並加以比較。</span><span class="sxs-lookup"><span data-stu-id="d1c6a-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="d1c6a-124">如果這兩個雜湊值相符，則此程式碼會在主控台中顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="d1c6a-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="d1c6a-125">如果不相符，則此程式碼會顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="d1c6a-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1c6a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c6a-126">See also</span></span>

- [<span data-ttu-id="d1c6a-127">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="d1c6a-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
