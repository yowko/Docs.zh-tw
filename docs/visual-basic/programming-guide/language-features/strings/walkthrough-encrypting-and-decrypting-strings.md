---
title: 在 Visual Basic 中的字串加密和解密
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 1d003df87327e14a6cbd65222f86c3dc4df169ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334038"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>逐步解說：在 Visual Basic 中的字串加密和解密
本逐步解說會示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>類別來加密和解密使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準字串 (<xref:System.Security.Cryptography.TripleDES>) 演算法。 第一個步驟是建立封裝的 3DES 演算法，並將加密的資料儲存為 base-64 編碼字串的簡單包裝函式類別。 然後，該包裝函式用來安全地儲存在可公開存取的文字檔中的 私用的使用者資料。  
  
 您可以使用加密，來保護使用者的機密資訊 （例如密碼），以及使未經授權的使用者無法讀取認證。 這樣可以防止授權的使用者的身分識別從被盜竊，保護使用者的資產，並提供不可否認性。 加密也可以保護使用者的資料不受存取未經授權的使用者。  
  
 如需詳細資訊，請參閱[密碼編譯服務](../../../../standard/security/cryptographic-services.md)。  
  
> [!IMPORTANT]
>  Rijndael （現在稱為進階加密標準 [AES]） 和三重資料加密標準 (3DES) 演算法提供更高的安全性，比 DES 因為它們是需密集運算。 如需詳細資訊，請參閱 <xref:System.Security.Cryptography.DES> 與 <xref:System.Security.Cryptography.Rijndael>。  
  
### <a name="to-create-the-encryption-wrapper"></a>若要建立加密的包裝函式  
  
1. 建立`Simple3Des`類別來封裝加密和解密的方法。  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. 將匯入的密碼編譯命名空間新增至檔案，其中包含開頭`Simple3Des`類別。  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. 在 `Simple3Des`類別中，加入私用欄位來儲存 3DES 密碼編譯服務提供者。  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. 加入私用的方法，從指定的索引鍵的雜湊建立指定長度的位元組陣列。  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. 新增初始化 3DES 密碼編譯服務提供者的建構函式。  
  
     `key`參數會控制`EncryptData`和`DecryptData`方法。  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. 將公用方法來加密的字串。  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. 將公用方法來解密字串。  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     包裝函式類別現在可用來保護使用者的資產。 在此範例中，它用來安全地儲存在可公開存取的文字檔中的 私用的使用者資料。  
  
### <a name="to-test-the-encryption-wrapper"></a>若要測試的加密包裝函式  
  
1. 在個別的類別中，將會使用包裝函式的方法新增`EncryptData`方法加密的字串，並將資料寫入使用者的 我的文件資料夾。  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. 新增的方法，從使用者讀取加密的字串的 [我的文件] 資料夾，並解密使用包裝函式的字串`DecryptData`方法。  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. 加入使用者介面的程式碼來呼叫`TestEncoding`和`TestDecoding`方法。  
  
4. 執行應用程式。  
  
     當您測試應用程式時，請注意它會解密資料，是否您提供錯誤的密碼。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [The signature is valid](../../../../standard/security/cryptographic-services.md)
