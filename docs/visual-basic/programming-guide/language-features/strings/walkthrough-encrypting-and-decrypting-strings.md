---
title: 在 Visual Basic 中的字串加密和解密
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651219"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="239ef-102">逐步解說：在 Visual Basic 中為字串加密和解密</span><span class="sxs-lookup"><span data-stu-id="239ef-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="239ef-103">本逐步解說會示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>類別來加密和解密使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準字串 (<xref:System.Security.Cryptography.TripleDES>) 演算法。</span><span class="sxs-lookup"><span data-stu-id="239ef-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="239ef-104">第一個步驟是建立一個簡單的包裝函式類別來封裝 3DES 演算法，並將加密的資料儲存為 base 64 編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="239ef-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="239ef-105">然後，該包裝函式用來安全地儲存在可公開存取的文字檔中的私用使用者資料。</span><span class="sxs-lookup"><span data-stu-id="239ef-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="239ef-106">您可以使用加密來保護使用者的機密資訊 （例如密碼），並使未經授權的使用者無法讀取認證。</span><span class="sxs-lookup"><span data-stu-id="239ef-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="239ef-107">這樣可以防止授權的使用者的身分識別遭竊、 從保護使用者的資產，並提供不可否認性。</span><span class="sxs-lookup"><span data-stu-id="239ef-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="239ef-108">加密也可以從正在存取未經授權的使用者保護使用者資料。</span><span class="sxs-lookup"><span data-stu-id="239ef-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="239ef-109">如需詳細資訊，請參閱[密碼編譯服務](../../../../standard/security/cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="239ef-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="239ef-110">Rijndael （現在稱為進階加密標準 [AES]） 和三重資料加密標準 (3DES) 演算法提供更高的安全性比 DES 因為它們是多個耗用大量運算資源。</span><span class="sxs-lookup"><span data-stu-id="239ef-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="239ef-111">如需詳細資訊，請參閱 <xref:System.Security.Cryptography.DES> 與 <xref:System.Security.Cryptography.Rijndael>。</span><span class="sxs-lookup"><span data-stu-id="239ef-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="239ef-112">若要建立加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="239ef-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="239ef-113">建立`Simple3Des`類別來封裝加密和解密的方法。</span><span class="sxs-lookup"><span data-stu-id="239ef-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  <span data-ttu-id="239ef-114">將匯入的密碼編譯命名空間加入至檔案，其中包含開頭`Simple3Des`類別。</span><span class="sxs-lookup"><span data-stu-id="239ef-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  <span data-ttu-id="239ef-115">在`Simple3Des`類別，加入私用欄位，以存放區 3DES 密碼編譯服務提供者。</span><span class="sxs-lookup"><span data-stu-id="239ef-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  <span data-ttu-id="239ef-116">加入私用的方法，從指定之索引鍵的雜湊建立所指定長度的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="239ef-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  <span data-ttu-id="239ef-117">新增的建構函式來初始化 3DES 密碼編譯服務提供者。</span><span class="sxs-lookup"><span data-stu-id="239ef-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="239ef-118">`key`參數會控制`EncryptData`和`DecryptData`方法。</span><span class="sxs-lookup"><span data-stu-id="239ef-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  <span data-ttu-id="239ef-119">加入加密字串的公用方法。</span><span class="sxs-lookup"><span data-stu-id="239ef-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  <span data-ttu-id="239ef-120">加入解密字串的公用方法。</span><span class="sxs-lookup"><span data-stu-id="239ef-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     <span data-ttu-id="239ef-121">包裝函式類別現在可用來保護使用者資產。</span><span class="sxs-lookup"><span data-stu-id="239ef-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="239ef-122">在此範例中，它用來安全地儲存可公開存取的文字檔案中的 私用使用者資料。</span><span class="sxs-lookup"><span data-stu-id="239ef-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="239ef-123">若要測試加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="239ef-123">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="239ef-124">在個別的類別，將會使用包裝函式的方法`EncryptData`方法來加密字串並寫入使用者的 我的文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="239ef-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  <span data-ttu-id="239ef-125">加入的 我的文件資料夾，並解密使用包裝函式的字串讀取使用者的加密的字串的方法`DecryptData`方法。</span><span class="sxs-lookup"><span data-stu-id="239ef-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  <span data-ttu-id="239ef-126">加入使用者介面的程式碼以呼叫`TestEncoding`和`TestDecoding`方法。</span><span class="sxs-lookup"><span data-stu-id="239ef-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="239ef-127">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="239ef-127">Run the application.</span></span>  
  
     <span data-ttu-id="239ef-128">當您測試應用程式時，請注意它將會解密資料，是否您提供的密碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="239ef-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239ef-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="239ef-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [<span data-ttu-id="239ef-130">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="239ef-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
