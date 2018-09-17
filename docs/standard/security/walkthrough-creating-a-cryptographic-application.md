---
title: 逐步解說：建立密碼編譯應用程式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 873b6120929c8c7cf67d53d8f793964361ae88b8
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964700"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="3fad3-102">逐步解說：建立密碼編譯應用程式</span><span class="sxs-lookup"><span data-stu-id="3fad3-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="3fad3-103">本逐步解說示範如何加密和解密內容。</span><span class="sxs-lookup"><span data-stu-id="3fad3-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="3fad3-104">程式碼範例是針對 Windows Form 應用程式所設計。</span><span class="sxs-lookup"><span data-stu-id="3fad3-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="3fad3-105">此應用程式不會示範真實世界案例，例如使用智慧卡。</span><span class="sxs-lookup"><span data-stu-id="3fad3-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="3fad3-106">相反地，它會示範加密和解密的基本概念。</span><span class="sxs-lookup"><span data-stu-id="3fad3-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="3fad3-107">本逐步解說針對加密使用下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="3fad3-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
-   <span data-ttu-id="3fad3-108">使用 <xref:System.Security.Cryptography.RijndaelManaged> 類別 (一個對稱算法) 來加密和解密資料，使用其自動產生的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> 和 <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>。</span><span class="sxs-lookup"><span data-stu-id="3fad3-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
-   <span data-ttu-id="3fad3-109">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> (一個非對稱式演算法)，加密和解密由 <xref:System.Security.Cryptography.RijndaelManaged> 加密之資料的金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="3fad3-110">非對稱演算法最適合用於較少量的資料，例如金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3fad3-111">如果您想要保護電腦上的資料，而不與其他人交換加密的內容，請考慮使用 <xref:System.Security.Cryptography.ProtectedData> 或 <xref:System.Security.Cryptography.ProtectedMemory> 類別。</span><span class="sxs-lookup"><span data-stu-id="3fad3-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="3fad3-112">下表摘要說明本主題中的密碼編譯工作。</span><span class="sxs-lookup"><span data-stu-id="3fad3-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="3fad3-113">工作</span><span class="sxs-lookup"><span data-stu-id="3fad3-113">Task</span></span>|<span data-ttu-id="3fad3-114">描述</span><span class="sxs-lookup"><span data-stu-id="3fad3-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="3fad3-115">建立 Windows Form 應用程式</span><span class="sxs-lookup"><span data-stu-id="3fad3-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="3fad3-116">列出執行應用程式所需的控制項。</span><span class="sxs-lookup"><span data-stu-id="3fad3-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="3fad3-117">宣告全域物件</span><span class="sxs-lookup"><span data-stu-id="3fad3-117">Declaring global objects</span></span>|<span data-ttu-id="3fad3-118">宣告字串路徑變數、<xref:System.Security.Cryptography.CspParameters>，和 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 以擁有 <xref:System.Windows.Forms.Form> 類別的全域內容。</span><span class="sxs-lookup"><span data-stu-id="3fad3-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="3fad3-119">建立非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-119">Creating an asymmetric key</span></span>|<span data-ttu-id="3fad3-120">建立非對稱公開和私密金鑰值組，並指派金鑰容器名稱給它。</span><span class="sxs-lookup"><span data-stu-id="3fad3-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="3fad3-121">加密檔案</span><span class="sxs-lookup"><span data-stu-id="3fad3-121">Encrypting a file</span></span>|<span data-ttu-id="3fad3-122">顯示對話方塊以選取要加密的檔案，並且進行加密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="3fad3-123">解密檔案</span><span class="sxs-lookup"><span data-stu-id="3fad3-123">Decrypting a file</span></span>|<span data-ttu-id="3fad3-124">顯示對話方塊以選取要解密的已加密檔案，並且進行解密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="3fad3-125">取得私密金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-125">Getting a private key</span></span>|<span data-ttu-id="3fad3-126">使用金鑰容器名稱取得完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="3fad3-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="3fad3-127">匯出公開金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-127">Exporting a public key</span></span>|<span data-ttu-id="3fad3-128">將金鑰儲存至僅包含公用參數的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="3fad3-129">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-129">Importing a public key</span></span>|<span data-ttu-id="3fad3-130">將金鑰從 XML 檔案載入到金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="3fad3-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="3fad3-131">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="3fad3-131">Testing the application</span></span>|<span data-ttu-id="3fad3-132">列出測試此應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="3fad3-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="3fad3-133">必要條件</span><span class="sxs-lookup"><span data-stu-id="3fad3-133">Prerequisites</span></span>  
 <span data-ttu-id="3fad3-134">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="3fad3-134">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="3fad3-135"><xref:System.IO> 和 <xref:System.Security.Cryptography> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="3fad3-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="3fad3-136">建立 Windows Form 應用程式</span><span class="sxs-lookup"><span data-stu-id="3fad3-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="3fad3-137">在此逐步解說中的大部分程式碼範例，已設計為按鈕控制項的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3fad3-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="3fad3-138">下表列出範例應用程式所需的控制項，及其必要名稱以符合程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="3fad3-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="3fad3-139">控制項</span><span class="sxs-lookup"><span data-stu-id="3fad3-139">Control</span></span>|<span data-ttu-id="3fad3-140">名稱</span><span class="sxs-lookup"><span data-stu-id="3fad3-140">Name</span></span>|<span data-ttu-id="3fad3-141">文字屬性 (如有需要)</span><span class="sxs-lookup"><span data-stu-id="3fad3-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="3fad3-142">加密檔案</span><span class="sxs-lookup"><span data-stu-id="3fad3-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="3fad3-143">解密檔案</span><span class="sxs-lookup"><span data-stu-id="3fad3-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="3fad3-144">建立金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="3fad3-145">匯出公開金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="3fad3-146">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="3fad3-147">取得私密金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="3fad3-148">按兩下 Visual Studio 設計工具中的按鈕，來建立其事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3fad3-148">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="3fad3-149">宣告全域物件</span><span class="sxs-lookup"><span data-stu-id="3fad3-149">Declaring Global Objects</span></span>  
 <span data-ttu-id="3fad3-150">將下列程式碼加入表單的建構函式：</span><span class="sxs-lookup"><span data-stu-id="3fad3-150">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="3fad3-151">針對您的環境和喜好設定編輯字串變數。</span><span class="sxs-lookup"><span data-stu-id="3fad3-151">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="3fad3-152">建立非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-152">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="3fad3-153">此工作會建立非對稱金鑰來加密及解密 <xref:System.Security.Cryptography.RijndaelManaged> 金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-153">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="3fad3-154">這個金鑰用來加密內容，且它會在標籤控制項上顯示金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="3fad3-154">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="3fad3-155">加入下列程式碼做為 `Create Keys` 按鈕的 `Click` 事件處理常式 (`buttonCreateAsmKeys_Click`)。</span><span class="sxs-lookup"><span data-stu-id="3fad3-155">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="3fad3-156">加密檔案</span><span class="sxs-lookup"><span data-stu-id="3fad3-156">Encrypting a File</span></span>  
 <span data-ttu-id="3fad3-157">這項工作需要兩個方法： 事件處理常式方法，如`Encrypt File` 按鈕 (`buttonEncryptFile_Click`) 和`EncryptFile`方法。</span><span class="sxs-lookup"><span data-stu-id="3fad3-157">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="3fad3-158">第一種方法會顯示一個對話方塊來選取檔案，並將檔案名稱傳遞給第二個方法，後者則會執行加密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-158">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="3fad3-159">加密的內容、金鑰和 IV 全都儲存到一個 <xref:System.IO.FileStream>，稱為加密套件。</span><span class="sxs-lookup"><span data-stu-id="3fad3-159">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="3fad3-160">`EncryptFile` 方法會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3fad3-160">The `EncryptFile` method does the following:</span></span>  
  
1.  <span data-ttu-id="3fad3-161">建立 <xref:System.Security.Cryptography.RijndaelManaged> 對稱演算法來加密內容。</span><span class="sxs-lookup"><span data-stu-id="3fad3-161">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2.  <span data-ttu-id="3fad3-162">建立 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件來加密 <xref:System.Security.Cryptography.RijndaelManaged> 金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-162">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3.  <span data-ttu-id="3fad3-163">使用 <xref:System.Security.Cryptography.CryptoStream> 物件以讀取及加密原始程式檔的 <xref:System.IO.FileStream> (以位元組區塊為單位) 成為加密檔案的目的地 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="3fad3-163">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4.  <span data-ttu-id="3fad3-164">判斷加密金鑰和 IV 的長度，並建立其長度值的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3fad3-164">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5.  <span data-ttu-id="3fad3-165">將金鑰、IV 和其長度值寫入加密套件。</span><span class="sxs-lookup"><span data-stu-id="3fad3-165">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="3fad3-166">加密套件使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="3fad3-166">The encryption package uses the following format:</span></span>  
  
-   <span data-ttu-id="3fad3-167">金鑰長度，位元組 0 - 3</span><span class="sxs-lookup"><span data-stu-id="3fad3-167">Key length, bytes 0 - 3</span></span>  
  
-   <span data-ttu-id="3fad3-168">IV 長度，位元組 4 - 7</span><span class="sxs-lookup"><span data-stu-id="3fad3-168">IV length, bytes 4 - 7</span></span>  
  
-   <span data-ttu-id="3fad3-169">加密的金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-169">Encrypted key</span></span>  
  
-   <span data-ttu-id="3fad3-170">IV</span><span class="sxs-lookup"><span data-stu-id="3fad3-170">IV</span></span>  
  
-   <span data-ttu-id="3fad3-171">加密文字</span><span class="sxs-lookup"><span data-stu-id="3fad3-171">Cipher text</span></span>  
  
 <span data-ttu-id="3fad3-172">您可以使用金鑰和 IV 的長度來決定加密套件所有部分的起始點和長度，這些可以用來解密檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-172">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="3fad3-173">加入下列程式碼做為 `Encrypt File` 按鈕的 `Click` 事件處理常式 (`buttonEncryptFile_Click`)。</span><span class="sxs-lookup"><span data-stu-id="3fad3-173">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="3fad3-174">將下列 `EncryptFile` 方法加入表單。</span><span class="sxs-lookup"><span data-stu-id="3fad3-174">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="3fad3-175">解密檔案</span><span class="sxs-lookup"><span data-stu-id="3fad3-175">Decrypting a File</span></span>  
 <span data-ttu-id="3fad3-176">這項工作需要兩個方法：`Decrypt File` 按鈕的事件處理常式方法 (`buttonDecryptFile_Click`) 和 `DecryptFile` 方法。</span><span class="sxs-lookup"><span data-stu-id="3fad3-176">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="3fad3-177">第一種方法會顯示一個對話方塊來選取檔案，並將其檔案名稱傳遞給第二個方法，後者則會執行解密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-177">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="3fad3-178">`Decrypt` 方法會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3fad3-178">The `Decrypt` method does the following:</span></span>  
  
1.  <span data-ttu-id="3fad3-179">建立 <xref:System.Security.Cryptography.RijndaelManaged> 對稱演算法來解密內容。</span><span class="sxs-lookup"><span data-stu-id="3fad3-179">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2.  <span data-ttu-id="3fad3-180">讀取加密套件的 <xref:System.IO.FileStream> 前八個位元組到位元組陣列，以取得加密金鑰和 IV 的長度。</span><span class="sxs-lookup"><span data-stu-id="3fad3-180">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3.  <span data-ttu-id="3fad3-181">從加密套件將金鑰和 IV 擷取到位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3fad3-181">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4.  <span data-ttu-id="3fad3-182">建立 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件來解密 <xref:System.Security.Cryptography.RijndaelManaged> 金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-182">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5.  <span data-ttu-id="3fad3-183">使用 <xref:System.Security.Cryptography.CryptoStream> 物件以讀取及解密 <xref:System.IO.FileStream> 加密套件的加密文字區段 (以位元組區域為單位 ) 到解密檔案的 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="3fad3-183">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="3fad3-184">完成後，就會解密完成。</span><span class="sxs-lookup"><span data-stu-id="3fad3-184">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="3fad3-185">加入下列程式碼做為 `Decrypt File` 按鈕的 `Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3fad3-185">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="3fad3-186">將下列 `DecryptFile` 方法加入表單。</span><span class="sxs-lookup"><span data-stu-id="3fad3-186">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="3fad3-187">匯出公開金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-187">Exporting a Public Key</span></span>  
 <span data-ttu-id="3fad3-188">這項工作會將 `Create Keys` 按鈕所建立的金鑰儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-188">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="3fad3-189">它只會匯出公用參數。</span><span class="sxs-lookup"><span data-stu-id="3fad3-189">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="3fad3-190">這項工作模擬的案例是 Alice 提供給 Bob 她的公開金鑰，讓他可以為她加密檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-190">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="3fad3-191">他和其他擁有該公開金鑰的使用者將無法解密這些檔案，因為他們沒有具私密參數的完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="3fad3-191">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="3fad3-192">加入下列程式碼做為 `Export Public Key` 按鈕的 `Click` 事件處理常式 (`buttonExportPublicKey_Click`)。</span><span class="sxs-lookup"><span data-stu-id="3fad3-192">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="3fad3-193">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-193">Importing a Public Key</span></span>  
 <span data-ttu-id="3fad3-194">這項工作載入金鑰時只會附帶公用參數，如 `Export Public Key` 按鈕所建立，然後將它設定為金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="3fad3-194">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="3fad3-195">這項工作模擬的案例是 Bob 載入 Alice 的金鑰且僅包含公用參數，讓他可以為她加密檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-195">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="3fad3-196">加入下列程式碼做為 `Import Public Key` 按鈕的 `Click` 事件處理常式 (`buttonImportPublicKey_Click`)。</span><span class="sxs-lookup"><span data-stu-id="3fad3-196">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="3fad3-197">取得私密金鑰</span><span class="sxs-lookup"><span data-stu-id="3fad3-197">Getting a Private Key</span></span>  
 <span data-ttu-id="3fad3-198">這項工作會將金鑰容器名稱設為使用 `Create Keys` 按鈕所建立的金鑰名稱。</span><span class="sxs-lookup"><span data-stu-id="3fad3-198">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="3fad3-199">金鑰容器將會包含完整金鑰組和私密參數。</span><span class="sxs-lookup"><span data-stu-id="3fad3-199">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="3fad3-200">這項工作模擬的案例是 Alice 使用她的私密金鑰來解密 Bob 所加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-200">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="3fad3-201">加入下列程式碼做為 `Get Private Key` 按鈕的 `Click` 事件處理常式 (`buttonGetPrivateKey_Click`)。</span><span class="sxs-lookup"><span data-stu-id="3fad3-201">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="3fad3-202">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="3fad3-202">Testing the Application</span></span>  
 <span data-ttu-id="3fad3-203">建立應用程式之後，請執行下列測試案例。</span><span class="sxs-lookup"><span data-stu-id="3fad3-203">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="3fad3-204">建立金鑰、加密和解密</span><span class="sxs-lookup"><span data-stu-id="3fad3-204">To create keys, encrypt, and decrypt</span></span>  
  
1.  <span data-ttu-id="3fad3-205">按一下 `Create Keys` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fad3-205">Click the `Create Keys` button.</span></span> <span data-ttu-id="3fad3-206">標籤會顯示金鑰名稱，並顯示它是完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="3fad3-206">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2.  <span data-ttu-id="3fad3-207">按一下 `Export Public Key` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fad3-207">Click the `Export Public Key` button.</span></span> <span data-ttu-id="3fad3-208">請注意匯出公開金鑰參數時，不會變更目前的金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-208">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3.  <span data-ttu-id="3fad3-209">按一下 `Encrypt File` 按鈕，然後選取檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-209">Click the `Encrypt File` button and select a file.</span></span>  
  
4.  <span data-ttu-id="3fad3-210">按一下 `Decrypt File` 按鈕，然後選取剛才加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-210">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5.  <span data-ttu-id="3fad3-211">檢查剛才解密的檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-211">Examine the file just decrypted.</span></span>  
  
6.  <span data-ttu-id="3fad3-212">關閉應用程式，然後重新啟動，以便在下一個案例中測試擷取保存的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="3fad3-212">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="3fad3-213">使用公開金鑰加密</span><span class="sxs-lookup"><span data-stu-id="3fad3-213">To encrypt using the public key</span></span>  
  
1.  <span data-ttu-id="3fad3-214">按一下 `Import Public Key` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fad3-214">Click the `Import Public Key` button.</span></span> <span data-ttu-id="3fad3-215">標籤會顯示金鑰名稱，並顯示它只是公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="3fad3-215">The label displays the key name and shows that it is public only.</span></span>  
  
2.  <span data-ttu-id="3fad3-216">按一下 `Encrypt File` 按鈕，然後選取檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-216">Click the `Encrypt File` button and select a file.</span></span>  
  
3.  <span data-ttu-id="3fad3-217">按一下 `Decrypt File` 按鈕，然後選取剛才加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-217">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="3fad3-218">這將會失敗，因為您必須擁有私密金鑰才能解密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-218">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="3fad3-219">這個案例示範了只具有公用金鑰來為另一個人加密檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-219">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="3fad3-220">通常那個人只會提供您公開金鑰，並且保留私密金鑰來進行解密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-220">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="3fad3-221">使用私密金鑰解密</span><span class="sxs-lookup"><span data-stu-id="3fad3-221">To decrypt using the private key</span></span>  
  
1.  <span data-ttu-id="3fad3-222">按一下 `Get Private Key` 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3fad3-222">Click the `Get Private Key` button.</span></span> <span data-ttu-id="3fad3-223">標籤會顯示金鑰名稱，並顯示它是否為完整金鑰組。</span><span class="sxs-lookup"><span data-stu-id="3fad3-223">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2.  <span data-ttu-id="3fad3-224">按一下 `Decrypt File` 按鈕，然後選取剛才加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="3fad3-224">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="3fad3-225">這將會成功，因為您有完整金鑰組可以解密。</span><span class="sxs-lookup"><span data-stu-id="3fad3-225">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fad3-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fad3-226">See also</span></span>

- [<span data-ttu-id="3fad3-227">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="3fad3-227">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
