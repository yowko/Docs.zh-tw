---
title: 逐步解說：建立密碼編譯應用程式
description: 逐步解說如何建立密碼編譯應用程式。 瞭解如何在 Windows Forms 應用程式中加密和解密內容。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 70218d60abb336cdb35fc2e89e62a50b6bd79c67
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830554"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="c1397-104">逐步解說：建立密碼編譯應用程式</span><span class="sxs-lookup"><span data-stu-id="c1397-104">Walkthrough: Creating a Cryptographic Application</span></span>

> [!NOTE]
> <span data-ttu-id="c1397-105">本文適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="c1397-105">This article applies to Windows.</span></span>
>
> <span data-ttu-id="c1397-106">如需 ASP.NET Core 的詳細資訊，請參閱 [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)。</span><span class="sxs-lookup"><span data-stu-id="c1397-106">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="c1397-107">本逐步解說示範如何加密和解密內容。</span><span class="sxs-lookup"><span data-stu-id="c1397-107">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="c1397-108">程式碼範例是針對 Windows Form 應用程式所設計。</span><span class="sxs-lookup"><span data-stu-id="c1397-108">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="c1397-109">此應用程式不會示範真實世界案例，例如使用智慧卡。</span><span class="sxs-lookup"><span data-stu-id="c1397-109">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="c1397-110">相反地，它會示範加密和解密的基本概念。</span><span class="sxs-lookup"><span data-stu-id="c1397-110">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
<span data-ttu-id="c1397-111">本逐步解說針對加密使用下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="c1397-111">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="c1397-112">使用 <xref:System.Security.Cryptography.Aes> 類別 (一個對稱算法) 來加密和解密資料，使用其自動產生的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> 和 <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>。</span><span class="sxs-lookup"><span data-stu-id="c1397-112">Use the <xref:System.Security.Cryptography.Aes> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="c1397-113">使用 <xref:System.Security.Cryptography.RSA> 非對稱演算法來加密金鑰，並將其解密至加密的資料 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="c1397-113">Use the <xref:System.Security.Cryptography.RSA> asymmetric algorithm to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.Aes>.</span></span> <span data-ttu-id="c1397-114">非對稱演算法最適合用於較少量的資料，例如金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1397-114">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1397-115">如果您想要保護電腦上的資料，而不是與其他人交換加密的內容，請考慮使用 <xref:System.Security.Cryptography.ProtectedData> 類別。</span><span class="sxs-lookup"><span data-stu-id="c1397-115">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> class.</span></span>  
  
 <span data-ttu-id="c1397-116">下表摘要說明本主題中的密碼編譯工作。</span><span class="sxs-lookup"><span data-stu-id="c1397-116">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="c1397-117">工作</span><span class="sxs-lookup"><span data-stu-id="c1397-117">Task</span></span>|<span data-ttu-id="c1397-118">說明</span><span class="sxs-lookup"><span data-stu-id="c1397-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c1397-119">建立 Windows Form 應用程式</span><span class="sxs-lookup"><span data-stu-id="c1397-119">Creating a Windows Forms application</span></span>|<span data-ttu-id="c1397-120">列出執行應用程式所需的控制項。</span><span class="sxs-lookup"><span data-stu-id="c1397-120">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="c1397-121">宣告全域物件</span><span class="sxs-lookup"><span data-stu-id="c1397-121">Declaring global objects</span></span>|<span data-ttu-id="c1397-122">宣告字串路徑變數、<xref:System.Security.Cryptography.CspParameters>，和 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 以擁有 <xref:System.Windows.Forms.Form> 類別的全域內容。</span><span class="sxs-lookup"><span data-stu-id="c1397-122">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="c1397-123">建立非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-123">Creating an asymmetric key</span></span>|<span data-ttu-id="c1397-124">建立非對稱公開和私密金鑰值組，並指派金鑰容器名稱給它。</span><span class="sxs-lookup"><span data-stu-id="c1397-124">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="c1397-125">加密檔案</span><span class="sxs-lookup"><span data-stu-id="c1397-125">Encrypting a file</span></span>|<span data-ttu-id="c1397-126">顯示對話方塊以選取要加密的檔案，並且進行加密。</span><span class="sxs-lookup"><span data-stu-id="c1397-126">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="c1397-127">解密檔案</span><span class="sxs-lookup"><span data-stu-id="c1397-127">Decrypting a file</span></span>|<span data-ttu-id="c1397-128">顯示對話方塊以選取要解密的已加密檔案，並且進行解密。</span><span class="sxs-lookup"><span data-stu-id="c1397-128">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="c1397-129">取得私密金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-129">Getting a private key</span></span>|<span data-ttu-id="c1397-130">使用金鑰容器名稱取得完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c1397-130">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="c1397-131">匯出公開金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-131">Exporting a public key</span></span>|<span data-ttu-id="c1397-132">將金鑰儲存至僅包含公用參數的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-132">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="c1397-133">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-133">Importing a public key</span></span>|<span data-ttu-id="c1397-134">將金鑰從 XML 檔案載入到金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="c1397-134">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="c1397-135">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="c1397-135">Testing the application</span></span>|<span data-ttu-id="c1397-136">列出測試此應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="c1397-136">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="c1397-137">必要條件</span><span class="sxs-lookup"><span data-stu-id="c1397-137">Prerequisites</span></span>  

<span data-ttu-id="c1397-138">您需要下列元件才能完成這個逐步解說：</span><span class="sxs-lookup"><span data-stu-id="c1397-138">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="c1397-139"><xref:System.IO> 和 <xref:System.Security.Cryptography> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="c1397-139">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="c1397-140">建立 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="c1397-140">Creating a Windows Forms Application</span></span>  

<span data-ttu-id="c1397-141">在此逐步解說中的大部分程式碼範例，已設計為按鈕控制項的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1397-141">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="c1397-142">下表列出範例應用程式所需的控制項，及其必要名稱以符合程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c1397-142">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="c1397-143">控制</span><span class="sxs-lookup"><span data-stu-id="c1397-143">Control</span></span>|<span data-ttu-id="c1397-144">名稱</span><span class="sxs-lookup"><span data-stu-id="c1397-144">Name</span></span>|<span data-ttu-id="c1397-145">文字屬性 (如有需要)</span><span class="sxs-lookup"><span data-stu-id="c1397-145">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="c1397-146">加密檔案</span><span class="sxs-lookup"><span data-stu-id="c1397-146">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="c1397-147">解密檔案</span><span class="sxs-lookup"><span data-stu-id="c1397-147">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="c1397-148">建立金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-148">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="c1397-149">匯出公開金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-149">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="c1397-150">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-150">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="c1397-151">取得私密金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-151">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="c1397-152">未設定金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-152">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="c1397-153">按兩下 Visual Studio 設計工具中的按鈕，以建立其事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1397-153">Double-click the buttons in the Visual Studio designer to create their event handlers.</span></span>
  
## <a name="declaring-global-objects"></a><span data-ttu-id="c1397-154">宣告全域物件</span><span class="sxs-lookup"><span data-stu-id="c1397-154">Declaring Global Objects</span></span>  

<span data-ttu-id="c1397-155">將下列程式碼加入表單的建構函式：</span><span class="sxs-lookup"><span data-stu-id="c1397-155">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="c1397-156">針對您的環境和喜好設定編輯字串變數。</span><span class="sxs-lookup"><span data-stu-id="c1397-156">Edit the string variables for your environment and preferences.</span></span>  
  
[!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
[!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="c1397-157">建立非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-157">Creating an Asymmetric Key</span></span>  

<span data-ttu-id="c1397-158">此工作會建立非對稱金鑰來加密及解密 <xref:System.Security.Cryptography.Aes> 金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1397-158">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.Aes> key.</span></span> <span data-ttu-id="c1397-159">這個金鑰用來加密內容，且它會在標籤控制項上顯示金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="c1397-159">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="c1397-160">加入下列程式碼做為 `Create Keys` 按鈕的 `Click` 事件處理常式 (`buttonCreateAsmKeys_Click`)。</span><span class="sxs-lookup"><span data-stu-id="c1397-160">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="c1397-161">加密檔案</span><span class="sxs-lookup"><span data-stu-id="c1397-161">Encrypting a File</span></span>  

<span data-ttu-id="c1397-162">這項工作牽涉到兩個方法：按鈕的事件處理常式方法 `Encrypt File` (`buttonEncryptFile_Click`) 和 `EncryptFile` 方法。</span><span class="sxs-lookup"><span data-stu-id="c1397-162">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="c1397-163">第一種方法會顯示一個對話方塊來選取檔案，並將檔案名稱傳遞給第二個方法，後者則會執行加密。</span><span class="sxs-lookup"><span data-stu-id="c1397-163">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
<span data-ttu-id="c1397-164">加密的內容、金鑰和 IV 全都儲存到一個 <xref:System.IO.FileStream>，稱為加密套件。</span><span class="sxs-lookup"><span data-stu-id="c1397-164">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
<span data-ttu-id="c1397-165">`EncryptFile` 方法會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c1397-165">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="c1397-166">建立 <xref:System.Security.Cryptography.Aes> 對稱演算法來加密內容。</span><span class="sxs-lookup"><span data-stu-id="c1397-166">Creates a <xref:System.Security.Cryptography.Aes> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="c1397-167">建立 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件來加密 <xref:System.Security.Cryptography.Aes> 金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1397-167">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
3. <span data-ttu-id="c1397-168">使用 <xref:System.Security.Cryptography.CryptoStream> 物件以讀取及加密原始程式檔的 <xref:System.IO.FileStream> (以位元組區塊為單位) 成為加密檔案的目的地 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="c1397-168">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="c1397-169">判斷加密金鑰和 IV 的長度，並建立其長度值的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c1397-169">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="c1397-170">將金鑰、IV 和其長度值寫入加密套件。</span><span class="sxs-lookup"><span data-stu-id="c1397-170">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="c1397-171">加密套件使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="c1397-171">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="c1397-172">金鑰長度，位元組 0 - 3</span><span class="sxs-lookup"><span data-stu-id="c1397-172">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="c1397-173">IV 長度，位元組 4 - 7</span><span class="sxs-lookup"><span data-stu-id="c1397-173">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="c1397-174">加密的金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-174">Encrypted key</span></span>  
  
- <span data-ttu-id="c1397-175">IV</span><span class="sxs-lookup"><span data-stu-id="c1397-175">IV</span></span>  
  
- <span data-ttu-id="c1397-176">加密文字</span><span class="sxs-lookup"><span data-stu-id="c1397-176">Cipher text</span></span>  
  
 <span data-ttu-id="c1397-177">您可以使用金鑰和 IV 的長度來決定加密套件所有部分的起始點和長度，這些可以用來解密檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-177">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="c1397-178">加入下列程式碼做為 `Encrypt File` 按鈕的 `Click` 事件處理常式 (`buttonEncryptFile_Click`)。</span><span class="sxs-lookup"><span data-stu-id="c1397-178">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="c1397-179">將下列 `EncryptFile` 方法加入表單。</span><span class="sxs-lookup"><span data-stu-id="c1397-179">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="c1397-180">解密檔案</span><span class="sxs-lookup"><span data-stu-id="c1397-180">Decrypting a File</span></span>  

<span data-ttu-id="c1397-181">這項工作需要兩個方法：`Decrypt File` 按鈕的事件處理常式方法 (`buttonDecryptFile_Click`) 和 `DecryptFile` 方法。</span><span class="sxs-lookup"><span data-stu-id="c1397-181">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="c1397-182">第一種方法會顯示一個對話方塊來選取檔案，並將其檔案名稱傳遞給第二個方法，後者則會執行解密。</span><span class="sxs-lookup"><span data-stu-id="c1397-182">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
<span data-ttu-id="c1397-183">`Decrypt` 方法會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c1397-183">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="c1397-184">建立 <xref:System.Security.Cryptography.Aes> 對稱演算法來解密內容。</span><span class="sxs-lookup"><span data-stu-id="c1397-184">Creates an <xref:System.Security.Cryptography.Aes> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="c1397-185">讀取加密套件的 <xref:System.IO.FileStream> 前八個位元組到位元組陣列，以取得加密金鑰和 IV 的長度。</span><span class="sxs-lookup"><span data-stu-id="c1397-185">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="c1397-186">從加密套件將金鑰和 IV 擷取到位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c1397-186">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="c1397-187">建立 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件來解密 <xref:System.Security.Cryptography.Aes> 金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1397-187">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
5. <span data-ttu-id="c1397-188">使用 <xref:System.Security.Cryptography.CryptoStream> 物件以讀取及解密 <xref:System.IO.FileStream> 加密套件的加密文字區段 (以位元組區域為單位 ) 到解密檔案的 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="c1397-188">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="c1397-189">完成後，就會解密完成。</span><span class="sxs-lookup"><span data-stu-id="c1397-189">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="c1397-190">加入下列程式碼做為 `Decrypt File` 按鈕的 `Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1397-190">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="c1397-191">將下列 `DecryptFile` 方法加入表單。</span><span class="sxs-lookup"><span data-stu-id="c1397-191">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="c1397-192">匯出公開金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-192">Exporting a Public Key</span></span>

<span data-ttu-id="c1397-193">這項工作會將 `Create Keys` 按鈕所建立的金鑰儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-193">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="c1397-194">它只會匯出公用參數。</span><span class="sxs-lookup"><span data-stu-id="c1397-194">It exports only the public parameters.</span></span>  
  
<span data-ttu-id="c1397-195">這項工作模擬的案例是 Alice 提供給 Bob 她的公開金鑰，讓他可以為她加密檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-195">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="c1397-196">他和其他擁有該公開金鑰的使用者將無法解密這些檔案，因為他們沒有具私密參數的完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c1397-196">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="c1397-197">加入下列程式碼做為 `Export Public Key` 按鈕的 `Click` 事件處理常式 (`buttonExportPublicKey_Click`)。</span><span class="sxs-lookup"><span data-stu-id="c1397-197">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="c1397-198">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-198">Importing a Public Key</span></span>

<span data-ttu-id="c1397-199">這項工作載入金鑰時只會附帶公用參數，如 `Export Public Key` 按鈕所建立，然後將它設定為金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="c1397-199">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
<span data-ttu-id="c1397-200">這項工作模擬的案例是 Bob 載入 Alice 的金鑰且僅包含公用參數，讓他可以為她加密檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-200">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
<span data-ttu-id="c1397-201">加入下列程式碼做為 `Import Public Key` 按鈕的 `Click` 事件處理常式 (`buttonImportPublicKey_Click`)。</span><span class="sxs-lookup"><span data-stu-id="c1397-201">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="c1397-202">取得私密金鑰</span><span class="sxs-lookup"><span data-stu-id="c1397-202">Getting a Private Key</span></span>  

<span data-ttu-id="c1397-203">這項工作會將金鑰容器名稱設為使用 `Create Keys` 按鈕所建立的金鑰名稱。</span><span class="sxs-lookup"><span data-stu-id="c1397-203">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="c1397-204">金鑰容器將會包含完整金鑰組和私密參數。</span><span class="sxs-lookup"><span data-stu-id="c1397-204">The key container will contain the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="c1397-205">這項工作模擬的案例是 Alice 使用她的私密金鑰來解密 Bob 所加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-205">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
<span data-ttu-id="c1397-206">加入下列程式碼做為 `Get Private Key` 按鈕的 `Click` 事件處理常式 (`buttonGetPrivateKey_Click`)。</span><span class="sxs-lookup"><span data-stu-id="c1397-206">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="c1397-207">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="c1397-207">Testing the Application</span></span>

<span data-ttu-id="c1397-208">建立應用程式之後，請執行下列測試案例。</span><span class="sxs-lookup"><span data-stu-id="c1397-208">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="c1397-209">建立金鑰、加密和解密</span><span class="sxs-lookup"><span data-stu-id="c1397-209">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="c1397-210">按一下 `Create Keys` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1397-210">Click the `Create Keys` button.</span></span> <span data-ttu-id="c1397-211">標籤會顯示金鑰名稱，並顯示它是完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c1397-211">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="c1397-212">按一下 `Export Public Key` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1397-212">Click the `Export Public Key` button.</span></span> <span data-ttu-id="c1397-213">請注意匯出公開金鑰參數時，不會變更目前的金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1397-213">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="c1397-214">按一下 `Encrypt File` 按鈕，然後選取檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-214">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="c1397-215">按一下 `Decrypt File` 按鈕，然後選取剛才加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-215">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="c1397-216">檢查剛才解密的檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-216">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="c1397-217">關閉應用程式，然後重新啟動，以便在下一個案例中測試擷取保存的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="c1397-217">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="c1397-218">使用公開金鑰加密</span><span class="sxs-lookup"><span data-stu-id="c1397-218">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="c1397-219">按一下 `Import Public Key` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1397-219">Click the `Import Public Key` button.</span></span> <span data-ttu-id="c1397-220">標籤會顯示金鑰名稱，並顯示它只是公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1397-220">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="c1397-221">按一下 `Encrypt File` 按鈕，然後選取檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-221">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="c1397-222">按一下 `Decrypt File` 按鈕，然後選取剛才加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-222">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="c1397-223">這將會失敗，因為您必須擁有私密金鑰才能解密。</span><span class="sxs-lookup"><span data-stu-id="c1397-223">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="c1397-224">這個案例示範了只具有公用金鑰來為另一個人加密檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-224">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="c1397-225">通常那個人只會提供您公開金鑰，並且保留私密金鑰來進行解密。</span><span class="sxs-lookup"><span data-stu-id="c1397-225">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="c1397-226">使用私密金鑰解密</span><span class="sxs-lookup"><span data-stu-id="c1397-226">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="c1397-227">按一下 `Get Private Key` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1397-227">Click the `Get Private Key` button.</span></span> <span data-ttu-id="c1397-228">標籤會顯示金鑰名稱，並顯示它是否為完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c1397-228">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="c1397-229">按一下 `Decrypt File` 按鈕，然後選取剛才加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="c1397-229">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="c1397-230">這將會成功，因為您有完整金鑰組可以解密。</span><span class="sxs-lookup"><span data-stu-id="c1397-230">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1397-231">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1397-231">See also</span></span>

- <span data-ttu-id="c1397-232">[加密模型](cryptography-model.md) -說明如何在基類庫中執行密碼編譯。</span><span class="sxs-lookup"><span data-stu-id="c1397-232">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="c1397-233">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="c1397-233">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="c1397-234">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="c1397-234">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="c1397-235">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="c1397-235">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
