---
title: "在 Visual Basic 中的字串加密和解密 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- encryption, strings
- strings [Visual Basic], encrypting
- decryption, strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ae3d599f7173162c07fbaeda60435615f101b10d
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>逐步解說：在 Visual Basic 中為字串加密和解密
本逐步解說會示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>來加密和解密使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準字串類別 (<xref:System.Security.Cryptography.TripleDES>) 演算法。</xref:System.Security.Cryptography.TripleDES> </xref:System.Security.Cryptography.DESCryptoServiceProvider> 第一個步驟是建立簡單的包裝函式類別來封裝 3DES 演算法，並將加密的資料儲存為 base 64 編碼的字串。 然後，該包裝函式用來安全地儲存在可公開存取的文字檔中的 私用使用者資料。  
  
 您可以使用加密來保護使用者的機密資訊 （例如密碼），並使未經授權的使用者無法讀取認證。 這樣可以防止授權的使用者的身分識別遭竊、 從保護使用者的資產，並提供不可否認性。 加密也可以從正在存取未經授權的使用者保護使用者資料。  
  
 如需詳細資訊，請參閱[密碼編譯服務](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)。  
  
> [!IMPORTANT]
>  Rijndael （現在稱為進階加密標準 [AES]） 和三重資料加密標準 (3DES) 演算法提供更安全的 DES 因為需耗用大量運算資源。 如需詳細資訊，請參閱<xref:System.Security.Cryptography.DES>和<xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael> </xref:System.Security.Cryptography.DES>  
  
### <a name="to-create-the-encryption-wrapper"></a>若要建立加密包裝函式  
  
1.  建立`Simple3Des`類別來封裝加密和解密的方法。  
  
     [!code-vb[VbVbalrStrings #&38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  將匯入的密碼編譯命名空間加入至檔案，其中包含開頭`Simple3Des`類別。  
  
     [!code-vb[VbVbalrStrings #&77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  在`Simple3Des`類別中，新增私用欄位來儲存 3DES 密碼編譯服務提供者。  
  
     [!code-vb[VbVbalrStrings #&39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  加入私用方法，從指定的索引鍵的雜湊建立指定之長度的位元組陣列。  
  
     [!code-vb[VbVbalrStrings #&41;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  新增的建構函式初始化 3DES 密碼編譯服務提供者。  
  
     `key`參數用於控制`EncryptData`和`DecryptData`方法。  
  
     [!code-vb[VbVbalrStrings #&40;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  加入加密字串的公用方法。  
  
     [!code-vb[VbVbalrStrings #&42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  加入解密字串的公用方法。  
  
     [!code-vb[VbVbalrStrings #&43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     包裝函式類別現在可用來保護使用者資產。 在此範例中，它用來安全地儲存在可公開存取的文字檔中的 私用使用者資料。  
  
### <a name="to-test-the-encryption-wrapper"></a>若要測試加密包裝函式  
  
1.  在個別的類別中，將使用包裝函式的方法加入`EncryptData`方法來加密字串並寫入使用者的我的文件 資料夾。  
  
     [!code-vb[VbVbalrStrings #&78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  新增從使用者讀取加密的字串的方法的 [我的文件] 資料夾和解密使用包裝函式的字串`DecryptData`方法。  
  
     [!code-vb[VbVbalrStrings #&79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  加入使用者介面的程式碼以呼叫`TestEncoding`和`TestDecoding`方法。  
  
4.  執行應用程式。  
  
     當您測試應用程式時，請注意它會解密資料，是否您提供的密碼錯誤。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Security.Cryptography></xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael>   
 [密碼編譯服務](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)
