---
title: "在 Visual Basic 中的字串加密和解密"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd9ec8e7af771db3f042e08c8ab30f6ed5832c2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>逐步解說：在 Visual Basic 中為字串加密和解密
本逐步解說會示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>類別來加密和解密使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準字串 (<xref:System.Security.Cryptography.TripleDES>) 演算法。 第一個步驟是建立一個簡單的包裝函式類別來封裝 3DES 演算法，並將加密的資料儲存為 base 64 編碼的字串。 然後，該包裝函式用來安全地儲存在可公開存取的文字檔中的私用使用者資料。  
  
 您可以使用加密來保護使用者的機密資訊 （例如密碼），並使未經授權的使用者無法讀取認證。 這樣可以防止授權的使用者的身分識別遭竊、 從保護使用者的資產，並提供不可否認性。 加密也可以從正在存取未經授權的使用者保護使用者資料。  
  
 如需詳細資訊，請參閱[密碼編譯服務](../../../../standard/security/cryptographic-services.md)。  
  
> [!IMPORTANT]
>  Rijndael （現在稱為進階加密標準 [AES]） 和三重資料加密標準 (3DES) 演算法提供更高的安全性比 DES 因為它們是多個耗用大量運算資源。 如需詳細資訊，請參閱 <xref:System.Security.Cryptography.DES> 與 <xref:System.Security.Cryptography.Rijndael>。  
  
### <a name="to-create-the-encryption-wrapper"></a>若要建立加密包裝函式  
  
1.  建立`Simple3Des`類別來封裝加密和解密的方法。  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  將匯入的密碼編譯命名空間加入至檔案，其中包含開頭`Simple3Des`類別。  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  在`Simple3Des`類別，加入私用欄位，以存放區 3DES 密碼編譯服務提供者。  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  加入私用的方法，從指定之索引鍵的雜湊建立所指定長度的位元組陣列。  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  新增的建構函式來初始化 3DES 密碼編譯服務提供者。  
  
     `key`參數會控制`EncryptData`和`DecryptData`方法。  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  加入加密字串的公用方法。  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  加入解密字串的公用方法。  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     包裝函式類別現在可用來保護使用者資產。 在此範例中，它用來安全地儲存可公開存取的文字檔案中的 私用使用者資料。  
  
### <a name="to-test-the-encryption-wrapper"></a>若要測試加密包裝函式  
  
1.  在個別的類別，將會使用包裝函式的方法`EncryptData`方法來加密字串並寫入使用者的 我的文件資料夾。  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  加入的 我的文件資料夾，並解密使用包裝函式的字串讀取使用者的加密的字串的方法`DecryptData`方法。  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  加入使用者介面的程式碼以呼叫`TestEncoding`和`TestDecoding`方法。  
  
4.  執行應用程式。  
  
     當您測試應用程式時，請注意它將會解密資料，是否您提供的密碼錯誤。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [密碼編譯服務](../../../../standard/security/cryptographic-services.md)
