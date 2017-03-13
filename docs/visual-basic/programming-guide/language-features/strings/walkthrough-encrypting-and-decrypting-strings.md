---
title: "Walkthrough: Encrypting and Decrypting Strings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "encryption, strings"
  - "strings [Visual Basic], encrypting"
  - "decryption, strings"
  - "strings [Visual Basic], decrypting"
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Walkthrough: Encrypting and Decrypting Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個逐步解說會顯示如何使用 <xref:System.Security.Cryptography.DESCryptoServiceProvider> 類別，利用三重資料加密標準 \(<xref:System.Security.Cryptography.TripleDES>\) 演算法的密碼編譯服務提供者 \(CSP\) 版本，進行字串的加密和解密。  第一步是建立簡單的包裝函式類別 \(Wrapper Class\)，封裝 3DES 演算法，並以 Base\-64 編碼字串儲存加密的資料。  接著使用該包裝函式，在可公開存取的文字檔中安全地儲存私密的使用者資料。  
  
 您可以使用加密保護使用者的機密資訊 \(例如密碼\)，使未經授權的使用者無法讀取認證。  這樣可保護授權使用者的識別 \(Identity\) 不致遭人盜用，進而保護使用者的資產並提供不可否認性。  加密也可以保護使用者的資料，避免遭到未經授權的使用者加以存取。  
  
 如需詳細資訊，請參閱[密碼編譯服務](../Topic/Cryptographic%20Services.md)。  
  
> [!IMPORTANT]
>  Rijndael \(現為進階加密標準 \[AES\]\) 和三重資料加密標準 \(3DES\) 演算法使用了更精密的計算方法，所以可提供比 DES 更佳的安全性。  如需詳細資訊，請參閱<xref:System.Security.Cryptography.DES>與<xref:System.Security.Cryptography.Rijndael>。  
  
### 若要建立加密包裝函式  
  
1.  建立 `Simple3Des` 類別封裝加密和解密方法。  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  加入加密命名空間匯入至包含 `Simple3Des` 類別檔案的開頭。  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  在 `Simple3Des` 類別，請將私用欄位來儲存 3DES 密碼編譯服務提供者。  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  加入私用方法，從指定的金鑰雜湊建立指定之長度的位元組陣列。  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  加入建構函式 \(Constructor\)，初始化 3DES 密碼編譯服務提供者。  
  
     `key` 參數會控制 `EncryptData` 和 `DecryptData` 方法。  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  加入將字串加密的公用 \(Public\) 方法。  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  加入將字串解密的公用方法。  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     現在包裝函式類別已可用來保護使用者資產。  在這個範例中，此包裝函式類別會用於在可公開存取的文字檔中安全地儲存私密的使用者資料。  
  
### 若要測試加密包裝函式  
  
1.  在不同的類別中，加入使用該包裝函式之 `EncryptData` 方法的方法，將字串加密並寫入使用者的 \[我的文件\] 資料夾。  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  加入從使用者 \[我的文件\] 資料夾讀取加密字串的方法，再使用包裝函式的 `DecryptData` 方法將該字串解密。  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  加入使用者介面程式碼，呼叫 `TestEncoding` 和 `TestDecoding` 方法。  
  
4.  執行應用程式。  
  
     請注意，如果您在測試應用程式時提供錯誤的密碼，則不會將資料解密。  
  
## 請參閱  
 <xref:System.Security.Cryptography>   
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>   
 <xref:System.Security.Cryptography.DES>   
 <xref:System.Security.Cryptography.TripleDES>   
 <xref:System.Security.Cryptography.Rijndael>   
 [密碼編譯服務](../Topic/Cryptographic%20Services.md)