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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 460b0e6e84f5be23f0c811e48daf36d3d4af3d23
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="1ee7d-102">逐步解說：在 Visual Basic 中為字串加密和解密</span><span class="sxs-lookup"><span data-stu-id="1ee7d-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="1ee7d-103">本逐步解說會示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>來加密和解密使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準字串類別 (<xref:System.Security.Cryptography.TripleDES>) 演算法。</xref:System.Security.Cryptography.TripleDES> </xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="1ee7d-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="1ee7d-104">第一個步驟是建立簡單的包裝函式類別來封裝 3DES 演算法，並將加密的資料儲存為 base 64 編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="1ee7d-105">然後，該包裝函式用來安全地儲存在可公開存取的文字檔中的 私用使用者資料。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="1ee7d-106">您可以使用加密來保護使用者的機密資訊 （例如密碼），並使未經授權的使用者無法讀取認證。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="1ee7d-107">這樣可以防止授權的使用者的身分識別遭竊、 從保護使用者的資產，並提供不可否認性。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="1ee7d-108">加密也可以從正在存取未經授權的使用者保護使用者資料。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="1ee7d-109">如需詳細資訊，請參閱[密碼編譯服務](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-109">For more information, see [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1ee7d-110">Rijndael （現在稱為進階加密標準 [AES]） 和三重資料加密標準 (3DES) 演算法提供更安全的 DES 因為需耗用大量運算資源。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="1ee7d-111">如需詳細資訊，請參閱<xref:System.Security.Cryptography.DES>和<xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael> </xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="1ee7d-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="1ee7d-112">若要建立加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="1ee7d-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="1ee7d-113">建立`Simple3Des`類別來封裝加密和解密的方法。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     <span data-ttu-id="1ee7d-114">[!code-vb[VbVbalrStrings #&38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-114">[!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span></span>  
  
2.  <span data-ttu-id="1ee7d-115">將匯入的密碼編譯命名空間加入至檔案，其中包含開頭`Simple3Des`類別。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-115">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     <span data-ttu-id="1ee7d-116">[!code-vb[VbVbalrStrings #&77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-116">[!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span></span>  
  
3.  <span data-ttu-id="1ee7d-117">在`Simple3Des`類別中，新增私用欄位來儲存 3DES 密碼編譯服務提供者。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-117">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="1ee7d-118">[!code-vb[VbVbalrStrings #&39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-118">[!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span></span>  
  
4.  <span data-ttu-id="1ee7d-119">加入私用方法，從指定的索引鍵的雜湊建立指定之長度的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-119">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     <span data-ttu-id="1ee7d-120">[!code-vb[VbVbalrStrings #&41;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-120">[!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span></span>  
  
5.  <span data-ttu-id="1ee7d-121">新增的建構函式初始化 3DES 密碼編譯服務提供者。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-121">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="1ee7d-122">`key`參數用於控制`EncryptData`和`DecryptData`方法。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-122">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     <span data-ttu-id="1ee7d-123">[!code-vb[VbVbalrStrings #&40;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-123">[!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span></span>  
  
6.  <span data-ttu-id="1ee7d-124">加入加密字串的公用方法。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-124">Add a public method that encrypts a string.</span></span>  
  
     <span data-ttu-id="1ee7d-125">[!code-vb[VbVbalrStrings #&42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-125">[!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span></span>  
  
7.  <span data-ttu-id="1ee7d-126">加入解密字串的公用方法。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-126">Add a public method that decrypts a string.</span></span>  
  
     <span data-ttu-id="1ee7d-127">[!code-vb[VbVbalrStrings #&43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-127">[!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span></span>  
  
     <span data-ttu-id="1ee7d-128">包裝函式類別現在可用來保護使用者資產。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-128">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="1ee7d-129">在此範例中，它用來安全地儲存在可公開存取的文字檔中的 私用使用者資料。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-129">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="1ee7d-130">若要測試加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="1ee7d-130">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="1ee7d-131">在個別的類別中，將使用包裝函式的方法加入`EncryptData`方法來加密字串並寫入使用者的我的文件 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-131">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     <span data-ttu-id="1ee7d-132">[!code-vb[VbVbalrStrings #&78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-132">[!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span></span>  
  
2.  <span data-ttu-id="1ee7d-133">新增從使用者讀取加密的字串的方法的 [我的文件] 資料夾和解密使用包裝函式的字串`DecryptData`方法。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-133">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     <span data-ttu-id="1ee7d-134">[!code-vb[VbVbalrStrings #&79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ee7d-134">[!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span></span>  
  
3.  <span data-ttu-id="1ee7d-135">加入使用者介面的程式碼以呼叫`TestEncoding`和`TestDecoding`方法。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-135">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="1ee7d-136">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-136">Run the application.</span></span>  
  
     <span data-ttu-id="1ee7d-137">當您測試應用程式時，請注意它會解密資料，是否您提供的密碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="1ee7d-137">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee7d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee7d-138">See Also</span></span>  
 <span data-ttu-id="1ee7d-139"><xref:System.Security.Cryptography></xref:System.Security.Cryptography></span><span class="sxs-lookup"><span data-stu-id="1ee7d-139"><xref:System.Security.Cryptography></span></span>   
 <span data-ttu-id="1ee7d-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="1ee7d-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></span></span>   
 <span data-ttu-id="1ee7d-141"><xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="1ee7d-141"><xref:System.Security.Cryptography.DES></span></span>   
 <span data-ttu-id="1ee7d-142"><xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES></span><span class="sxs-lookup"><span data-stu-id="1ee7d-142"><xref:System.Security.Cryptography.TripleDES></span></span>   
 <span data-ttu-id="1ee7d-143"><xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael></span><span class="sxs-lookup"><span data-stu-id="1ee7d-143"><xref:System.Security.Cryptography.Rijndael></span></span>   
<span data-ttu-id="1ee7d-144"> [密碼編譯服務](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span><span class="sxs-lookup"><span data-stu-id="1ee7d-144"> [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span></span>
