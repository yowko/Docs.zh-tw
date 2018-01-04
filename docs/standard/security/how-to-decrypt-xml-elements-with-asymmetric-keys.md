---
title: "如何：使用非對稱金鑰解密 XML 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 099937fe113c39c717b4c9fcba2042115b9105e6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="1e308-102">如何：使用非對稱金鑰解密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="1e308-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="1e308-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密和解密 XML 文件內的項目。</span><span class="sxs-lookup"><span data-stu-id="1e308-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="1e308-104">XML 加密是交換或儲存加密 XML 資料的標準方法，不必擔心資料被輕易讀取。</span><span class="sxs-lookup"><span data-stu-id="1e308-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="1e308-105">如需 XML 加密標準的詳細資訊，請參閱全球資訊網協會 (W3C) 的建議[XML 簽章語法和處理](http://go.microsoft.com/fwlink/?LinkID=136777)。</span><span class="sxs-lookup"><span data-stu-id="1e308-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](http://go.microsoft.com/fwlink/?LinkID=136777).</span></span>  
  
 <span data-ttu-id="1e308-106">在此程序的範例會解密 XML 項目使用中所述方法加密[How to： 使用非對稱金鑰加密 XML 項目](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="1e308-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="1e308-107">它會找出 <`EncryptedData`> 項目、解密該項目，然後再以原始純文字 XML 項目取代該項目。</span><span class="sxs-lookup"><span data-stu-id="1e308-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="1e308-108">此範例會使用兩個金鑰來解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="1e308-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="1e308-109">它會從金鑰容器中，擷取先前產生的 RSA 私密金鑰，然後使用 RSA 金鑰來解密儲存在 <`EncryptedData`> 項目之 <`EncryptedKey`> 項目中的工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e308-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="1e308-110">範例接著會使用工作階段金鑰解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="1e308-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="1e308-111">這個範例適合多個應用程式必須共用加密資料或應用程式必須在它執行時間之間儲存加密資料的情況。</span><span class="sxs-lookup"><span data-stu-id="1e308-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="1e308-112">使用非對稱金鑰解密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="1e308-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="1e308-113">建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="1e308-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="1e308-114">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件從容器擷取先前產生的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e308-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="1e308-115">當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 建構函式時，金鑰會自動從金鑰容器擷取。</span><span class="sxs-lookup"><span data-stu-id="1e308-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="1e308-116">建立新的 <xref:System.Security.Cryptography.Xml.EncryptedXml> 物件以解密文件。</span><span class="sxs-lookup"><span data-stu-id="1e308-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  <span data-ttu-id="1e308-117">加入金鑰/名稱對應以將 RSA 金鑰與應該解密之文件中的項目相關聯。</span><span class="sxs-lookup"><span data-stu-id="1e308-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="1e308-118">您必須使用與加密文件時所使用金鑰相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="1e308-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="1e308-119">請注意，這個名稱與用來識別步驟 1 中所指定金鑰容器中的金鑰名稱不同。</span><span class="sxs-lookup"><span data-stu-id="1e308-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  <span data-ttu-id="1e308-120">呼叫 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法來解密 <`EncryptedData`> 項目。</span><span class="sxs-lookup"><span data-stu-id="1e308-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="1e308-121">這個方法會使用 RSA 金鑰來解密工作階段金鑰，並會自動使用工作階段金鑰解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="1e308-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="1e308-122">它也會自動將 <`EncryptedData`> 項目取代為原始的純文字。</span><span class="sxs-lookup"><span data-stu-id="1e308-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  <span data-ttu-id="1e308-123">儲存 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1e308-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="1e308-124">範例</span><span class="sxs-lookup"><span data-stu-id="1e308-124">Example</span></span>  
 <span data-ttu-id="1e308-125">這個範例假設名為 `test.xml` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="1e308-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="1e308-126">它同時也假設`test.xml`包含使用中所述的技巧加密的 XML 項目[How to： 使用非對稱金鑰加密 XML 項目](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="1e308-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e308-127">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1e308-127">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1e308-128">若要編譯此範例，您需要包含 `System.Security.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="1e308-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="1e308-129">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="1e308-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1e308-130">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1e308-130">.NET Framework Security</span></span>  
 <span data-ttu-id="1e308-131">絕對不要以純文字儲存對稱密碼編譯金鑰，或以純文字格式在電腦之間傳輸對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e308-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="1e308-132">此外，絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1e308-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="1e308-133">如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[產生加密和解密金鑰](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="1e308-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="1e308-134">絕對不要直接將金鑰內嵌在您的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e308-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="1e308-135">內嵌的金鑰可以輕鬆地讀取從組件使用[Ildasm.exe （IL 解譯器）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)或藉由在文字編輯器例如記事本中開啟組件。</span><span class="sxs-lookup"><span data-stu-id="1e308-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="1e308-136">當您使用完密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1e308-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="1e308-137">偵錯工具有時可以從記憶體讀取密碼編譯金鑰，或是在記憶體位置被分頁至磁碟的情況下從硬碟機讀取。</span><span class="sxs-lookup"><span data-stu-id="1e308-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e308-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e308-138">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="1e308-139">操作說明：使用非對稱金鑰加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="1e308-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
