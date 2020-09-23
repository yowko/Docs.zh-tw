---
title: 加密和解密字串
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: e0e3fc332bf9430b1fa56dbb7630f849d3a29c2e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072401"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="3a3f8-102">逐步解說：在 Visual Basic 中為字串加密和解密</span><span class="sxs-lookup"><span data-stu-id="3a3f8-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>

<span data-ttu-id="3a3f8-103">本逐步解說將示範如何使用 <xref:System.Security.Cryptography.DESCryptoServiceProvider> 類別來加密和解密字串，方法是使用密碼編譯服務提供者 (CSP) 版本的三重資料加密標準 (<xref:System.Security.Cryptography.TripleDES>) 演算法。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="3a3f8-104">第一個步驟是建立封裝3DES 演算法的簡單包裝函式類別，並將加密的資料儲存為 base-64 編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="3a3f8-105">然後，該包裝函式會用來將私用使用者資料安全地儲存在可公開存取的文字檔中。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="3a3f8-106">您可以使用加密來保護使用者密碼 (例如，密碼) ，以及讓未經授權的使用者無法讀取認證。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="3a3f8-107">這可以保護授權使用者的身分識別免于遭竊，以保護使用者的資產並提供不可否認性。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="3a3f8-108">加密也可以保護使用者的資料免于未經授權的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="3a3f8-109">如需詳細資訊，請參閱[密碼編譯服務](../../../../standard/security/cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a3f8-110">Rijndael (現在稱為進階加密標準 [AES] ) 以及三重資料加密標準 (3DES) 演算法可提供比 DES 更高的安全性，因為它們會耗用更大量的計算。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="3a3f8-111">如需詳細資訊，請參閱 <xref:System.Security.Cryptography.DES> 和 <xref:System.Security.Cryptography.Rijndael>。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="3a3f8-112">建立加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="3a3f8-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="3a3f8-113">建立 `Simple3Des` 類別來封裝加密和解密方法。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="3a3f8-114">將密碼編譯命名空間的匯入新增至包含類別的檔開頭 `Simple3Des` 。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="3a3f8-115">在 `Simple3Des` 類別中，新增私用欄位來儲存3des 密碼編譯服務提供者。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="3a3f8-116">新增私用方法，以從指定索引鍵的雜湊建立指定長度的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="3a3f8-117">新增用來初始化3DES 密碼編譯服務提供者的函式。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="3a3f8-118">`key`參數會控制 `EncryptData` 和 `DecryptData` 方法。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="3a3f8-119">新增可加密字串的公用方法。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="3a3f8-120">新增可解密字串的公用方法。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="3a3f8-121">包裝函式類別現在可以用來保護使用者資產。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="3a3f8-122">在此範例中，它是用來將私用使用者資料安全地儲存在可公開存取的文字檔中。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="3a3f8-123">測試加密包裝函式</span><span class="sxs-lookup"><span data-stu-id="3a3f8-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="3a3f8-124">在不同的類別中，新增方法來使用包裝函式的 `EncryptData` 方法來加密字串，並將它寫入使用者的我的檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="3a3f8-125">新增方法，以從使用者的我的檔資料夾讀取加密的字串，並使用包裝函式的方法來解密字串 `DecryptData` 。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="3a3f8-126">加入使用者介面程式碼以呼叫 `TestEncoding` 和 `TestDecoding` 方法。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="3a3f8-127">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-127">Run the application.</span></span>  
  
     <span data-ttu-id="3a3f8-128">當您測試應用程式時，請注意，如果您提供錯誤的密碼，它就不會解密資料。</span><span class="sxs-lookup"><span data-stu-id="3a3f8-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3f8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a3f8-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="3a3f8-130">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="3a3f8-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
