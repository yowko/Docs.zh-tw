---
title: 加密和解密 Visual Basic 中的字串
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee8691fedb537d1aa588eaac61624b445da64d1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944419"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>逐步解說：加密和解密 Visual Basic 中的字串
本逐步解說將示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>類別, 利用三重資料加密標準 (<xref:System.Security.Cryptography.TripleDES>) 演算法的密碼編譯服務提供者 (CSP) 版本來加密和解密字串。 第一個步驟是建立簡單的包裝函式類別來封裝3DES 演算法, 並將加密的資料儲存為以基底64編碼的字串。 然後, 該包裝函式會用來將私用使用者資料安全地儲存在可公開存取的文字檔中。  
  
 您可以使用加密來保護使用者秘密 (例如, 密碼), 並讓未經授權的使用者無法讀取認證。 這可保護授權使用者的身分識別免于遭竊, 以保護使用者的資產並提供不可否認性。 加密也可以保護使用者的資料, 使其無法被未經授權的使用者存取。  
  
 如需詳細資訊，請參閱[密碼編譯服務](../../../../standard/security/cryptographic-services.md)。  
  
> [!IMPORTANT]
> Rijndael (現在稱為進階加密標準 [AES]) 和「三重資料加密標準」 (3DES) 演算法提供比 DES 更高的安全性, 因為它們會耗用更多的計算能力。 如需詳細資訊，請參閱 <xref:System.Security.Cryptography.DES> 與 <xref:System.Security.Cryptography.Rijndael>。  
  
### <a name="to-create-the-encryption-wrapper"></a>建立加密包裝函式  
  
1. `Simple3Des`建立類別以封裝加密和解密方法。  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. 將密碼編譯命名空間的匯入新增至包含`Simple3Des`類別的檔案開頭。  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. `Simple3Des`在類別中, 新增私用欄位來儲存3des 密碼編譯服務提供者。  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. 新增私用方法, 以從指定之索引鍵的雜湊建立指定長度的位元組陣列。  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. 新增用來初始化3DES 密碼編譯服務提供者的函式。  
  
     參數會`EncryptData`控制和`DecryptData`方法。 `key`  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. 新增可加密字串的公用方法。  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. 加入解密字串的公用方法。  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     包裝函式類別現在可以用來保護使用者資產。 在此範例中, 它是用來將私用使用者資料安全地儲存在可公開存取的文字檔中。  
  
### <a name="to-test-the-encryption-wrapper"></a>測試加密包裝函式  
  
1. 在不同的類別中, 新增一個方法, 使用包裝函`EncryptData`式的方法來加密字串, 並將它寫入使用者的 [我的文件] 資料夾。  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. 新增方法, 從使用者的 [我的文件] 資料夾讀取加密的字串, 並使用包裝函式的`DecryptData`方法來解密字串。  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. 新增使用者介面程式碼以呼叫`TestEncoding`和`TestDecoding`方法。  
  
4. 執行應用程式。  
  
     當您測試應用程式時, 請注意, 如果您提供錯誤的密碼, 它不會將資料解密。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [The signature is valid](../../../../standard/security/cryptographic-services.md)
