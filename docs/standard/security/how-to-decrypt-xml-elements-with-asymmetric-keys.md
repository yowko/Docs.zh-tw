---
title: 作法：使用非對稱金鑰解密 XML 元素
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 0456c89987b37840daa1c84342528d11c6da73a4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822226"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="06364-102">作法：使用非對稱金鑰解密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="06364-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="06364-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密和解密 XML 文件內的項目。</span><span class="sxs-lookup"><span data-stu-id="06364-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="06364-104">XML 加密是交換或儲存加密 XML 資料的標準方法，不必擔心資料被輕易讀取。</span><span class="sxs-lookup"><span data-stu-id="06364-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="06364-105">如需 XML 加密標準的詳細資訊，請參閱全球資訊網協會 (W3C) 建議 [XML 簽章語法和處理](https://www.w3.org/TR/xmldsig-core/)。</span><span class="sxs-lookup"><span data-stu-id="06364-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="06364-106">本文中的程式碼適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="06364-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="06364-107">此程式中的範例會解密使用 how [to：使用非對稱金鑰加密 XML](how-to-encrypt-xml-elements-with-asymmetric-keys.md)專案中所述方法加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="06364-107">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="06364-108">它會尋找 <`EncryptedData`> 元素、將專案解密，然後將專案取代為原始純文字 XML 專案。</span><span class="sxs-lookup"><span data-stu-id="06364-108">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="06364-109">此範例會使用兩個金鑰來解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="06364-109">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="06364-110">它會從金鑰容器抓取先前產生的 RSA 私密金鑰，然後使用 RSA 金鑰來解密儲存在 <> 專案的 <> 元素中的工作階段金鑰 `EncryptedKey` `EncryptedData` 。</span><span class="sxs-lookup"><span data-stu-id="06364-110">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="06364-111">範例接著會使用工作階段金鑰解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="06364-111">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="06364-112">這個範例適合多個應用程式必須共用加密資料或應用程式必須在它執行時間之間儲存加密資料的情況。</span><span class="sxs-lookup"><span data-stu-id="06364-112">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="06364-113">使用非對稱金鑰解密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="06364-113">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="06364-114">建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="06364-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="06364-115">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件從容器擷取先前產生的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="06364-115">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="06364-116">當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 建構函式時，金鑰會自動從金鑰容器擷取。</span><span class="sxs-lookup"><span data-stu-id="06364-116">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="06364-117">建立新的 <xref:System.Security.Cryptography.Xml.EncryptedXml> 物件以解密文件。</span><span class="sxs-lookup"><span data-stu-id="06364-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="06364-118">加入金鑰/名稱對應以將 RSA 金鑰與應該解密之文件中的項目相關聯。</span><span class="sxs-lookup"><span data-stu-id="06364-118">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="06364-119">您必須使用與加密文件時所使用金鑰相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="06364-119">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="06364-120">請注意，這個名稱與用來識別步驟 1 中所指定金鑰容器中的金鑰名稱不同。</span><span class="sxs-lookup"><span data-stu-id="06364-120">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="06364-121">呼叫 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法來解密 <的 `EncryptedData`> 元素。</span><span class="sxs-lookup"><span data-stu-id="06364-121">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="06364-122">這個方法會使用 RSA 金鑰來解密工作階段金鑰，並會自動使用工作階段金鑰解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="06364-122">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="06364-123">它也會自動 `EncryptedData` 以原始純文字取代 <的> 元素。</span><span class="sxs-lookup"><span data-stu-id="06364-123">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="06364-124">儲存 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="06364-124">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="06364-125">範例</span><span class="sxs-lookup"><span data-stu-id="06364-125">Example</span></span>

<span data-ttu-id="06364-126">這個範例假設名為 `test.xml` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="06364-126">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="06364-127">它也假設 `test.xml` 包含使用 how [to：使用非對稱金鑰加密 XML](how-to-encrypt-xml-elements-with-asymmetric-keys.md)專案中所述技術進行加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="06364-127">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06364-128">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="06364-128">Compiling the Code</span></span>  
  
- <span data-ttu-id="06364-129">在以 .NET Framework 為目標的專案中，包含的參考 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="06364-129">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="06364-130">在以 .NET Core 或 .NET 5 為目標的專案中，安裝 NuGet 套件 [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="06364-130">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="06364-131">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="06364-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="06364-132">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="06364-132">.NET Security</span></span>  

<span data-ttu-id="06364-133">絕對不要以純文字儲存對稱密碼編譯金鑰，或以純文字格式在電腦之間傳輸對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="06364-133">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="06364-134">此外，絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="06364-134">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="06364-135">如需對稱和非對稱式密碼編譯金鑰的詳細資訊，請參閱 [產生加密和解密的金鑰](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="06364-135">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="06364-136">絕對不要直接將金鑰內嵌在您的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="06364-136">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="06364-137">您可以使用 [Ildasm.exe (IL ](../../framework/tools/ildasm-exe-il-disassembler.md) 解譯器) 或在文字編輯器（例如 [記事本]）中開啟元件，輕鬆地從元件讀取內嵌的金鑰。</span><span class="sxs-lookup"><span data-stu-id="06364-137">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="06364-138">當您使用完密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="06364-138">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="06364-139">偵錯工具有時可以從記憶體讀取密碼編譯金鑰，或是在記憶體位置被分頁至磁碟的情況下從硬碟機讀取。</span><span class="sxs-lookup"><span data-stu-id="06364-139">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06364-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="06364-140">See also</span></span>

- [<span data-ttu-id="06364-141">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="06364-141">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="06364-142">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="06364-142">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="06364-143">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="06364-143">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="06364-144">操作說明：使用非對稱金鑰加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="06364-144">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="06364-145">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="06364-145">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
