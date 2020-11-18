---
title: 使用雜湊程式碼確定資料完整性
description: 瞭解如何在 .NET 中使用雜湊碼來確保資料完整性。 雜湊值是可唯一識別資料的固定長度數值。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET], hash
- data integrity
- checking hash codes
- encryption [.NET], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 085a0ea387e3415e6e916bcdf9055ffaa6753fef
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831087"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>使用雜湊程式碼確定資料完整性
雜湊值是可唯一識別資料的固定長度數值。 雜湊值以較小的數值代表大量的資料，所以可和數位簽章一起使用。 比起簽署更大的值，簽署雜湊值更有效率。 如需驗證透過不安全的通道傳送的資料完整性，雜湊值會相當有用。 可比較已接收資料的雜湊值和該資料傳送時的雜湊值，來判斷資料是否已變更。  
  
本主題描述如何使用 <xref:System.Security.Cryptography> 命名空間中的類別來產生及驗證雜湊碼。  
  
## <a name="generating-a-hash"></a>產生雜湊

 Managed 雜湊類別可以雜湊位元組陣列或 Managed 資料流物件。 以下範例使用 SHA1 雜湊演算法來建立字串的雜湊值。 此範例會使用 <xref:System.Text.UnicodeEncoding> 類別，將字串轉換成使用 <xref:System.Security.Cryptography.SHA256> 類別雜湊的位元組陣列。 接著會在主控台顯示雜湊值。  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 此程式碼會在主控台顯示下列字串：  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a>驗證雜湊

 若要判斷資料完整性，可將資料和雜湊值相比較。 通常，資料會在特定時間進行雜湊，該雜湊值則會受某種方式保護。 在一段期間之後，可再重新雜湊資料，並與受保護的值相比較。 如果雜湊值相符，資料就未受變更。 如果值不相符，則資料已損毀。 為了讓這個系統運作，對於來自未受信任的所有對象，都必須將受保護的雜湊加密或保密。  
  
 下列範例會將字串的前一個雜湊值與新的雜湊值相比較。 此範例會在雜湊值的每個位元組中執行迴圈，並加以比較。  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 如果這兩個雜湊值相符，則此程式碼會在主控台中顯示下列內容：  
  
```console  
The hash codes match.  
```  
  
 如果不相符，則此程式碼會顯示下列內容：  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>請參閱

- [密碼編譯模型](cryptography-model.md)
- [密碼編譯服務](cryptographic-services.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
