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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334038"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="fa62c-102">逐步解說：在 Visual Basic 中的字串加密和解密</span><span class="sxs-lookup"><span data-stu-id="fa62c-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="fa62c-103">本逐步解說會示範如何使用<xref:System.Security.Cryptography.DESCryptoServiceProvider>類別來加密和解密使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準字串 (<xref:System.Security.Cryptography.TripleDES>) 演算法。</span><span class="sxs-lookup"><span data-stu-id="fa62c-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="fa62c-104">第一個步驟是建立封裝的 3DES 演算法，並將加密的資料儲存為 base-64 編碼字串的簡單包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="fa62c-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="fa62c-105">然後，該包裝函式用來安全地儲存在可公開存取的文字檔中的 私用的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="fa62c-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="fa62c-106">您可以使用加密，來保護使用者的機密資訊 （例如密碼），以及使未經授權的使用者無法讀取認證。</span><span class="sxs-lookup"><span data-stu-id="fa62c-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="fa62c-107">這樣可以防止授權的使用者的身分識別從被盜竊，保護使用者的資產，並提供不可否認性。</span><span class="sxs-lookup"><span data-stu-id="fa62c-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="fa62c-108">加密也可以保護使用者的資料不受存取未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="fa62c-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="fa62c-109">如需詳細資訊，請參閱[密碼編譯服務](../../../../standard/security/cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fa62c-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa62c-110">Rijndael （現在稱為進階加密標準 [AES]） 和三重資料加密標準 (3DES) 演算法提供更高的安全性，比 DES 因為它們是需密集運算。</span><span class="sxs-lookup"><span data-stu-id="fa62c-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="fa62c-111">如需詳細資訊，請參閱 <xref:System.Security.Cryptography.DES> 與 <xref:System.Security.Cryptography.Rijndael>。</span><span class="sxs-lookup"><span data-stu-id="fa62c-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="fa62c-112">若要建立加密的包裝函式</span><span class="sxs-lookup"><span data-stu-id="fa62c-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="fa62c-113">建立`Simple3Des`類別來封裝加密和解密的方法。</span><span class="sxs-lookup"><span data-stu-id="fa62c-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="fa62c-114">將匯入的密碼編譯命名空間新增至檔案，其中包含開頭`Simple3Des`類別。</span><span class="sxs-lookup"><span data-stu-id="fa62c-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="fa62c-115">在 `Simple3Des`類別中，加入私用欄位來儲存 3DES 密碼編譯服務提供者。</span><span class="sxs-lookup"><span data-stu-id="fa62c-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="fa62c-116">加入私用的方法，從指定的索引鍵的雜湊建立指定長度的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="fa62c-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="fa62c-117">新增初始化 3DES 密碼編譯服務提供者的建構函式。</span><span class="sxs-lookup"><span data-stu-id="fa62c-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="fa62c-118">`key`參數會控制`EncryptData`和`DecryptData`方法。</span><span class="sxs-lookup"><span data-stu-id="fa62c-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="fa62c-119">將公用方法來加密的字串。</span><span class="sxs-lookup"><span data-stu-id="fa62c-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="fa62c-120">將公用方法來解密字串。</span><span class="sxs-lookup"><span data-stu-id="fa62c-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="fa62c-121">包裝函式類別現在可用來保護使用者的資產。</span><span class="sxs-lookup"><span data-stu-id="fa62c-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="fa62c-122">在此範例中，它用來安全地儲存在可公開存取的文字檔中的 私用的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="fa62c-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="fa62c-123">若要測試的加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="fa62c-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="fa62c-124">在個別的類別中，將會使用包裝函式的方法新增`EncryptData`方法加密的字串，並將資料寫入使用者的 我的文件資料夾。</span><span class="sxs-lookup"><span data-stu-id="fa62c-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="fa62c-125">新增的方法，從使用者讀取加密的字串的 [我的文件] 資料夾，並解密使用包裝函式的字串`DecryptData`方法。</span><span class="sxs-lookup"><span data-stu-id="fa62c-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="fa62c-126">加入使用者介面的程式碼來呼叫`TestEncoding`和`TestDecoding`方法。</span><span class="sxs-lookup"><span data-stu-id="fa62c-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="fa62c-127">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="fa62c-127">Run the application.</span></span>  
  
     <span data-ttu-id="fa62c-128">當您測試應用程式時，請注意它會解密資料，是否您提供錯誤的密碼。</span><span class="sxs-lookup"><span data-stu-id="fa62c-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa62c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa62c-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="fa62c-130">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="fa62c-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
