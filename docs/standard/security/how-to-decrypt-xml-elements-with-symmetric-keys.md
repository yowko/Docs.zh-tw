---
title: "如何：使用對稱金鑰解密 XML 項目"
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
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6bacdb47d1107f6a800d9beec2578c0f7085a894
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="8ecfe-102">如何：使用對稱金鑰解密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="8ecfe-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="8ecfe-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密 XML 文件內的項目。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="8ecfe-104">XML 加密可讓您儲存或傳輸機密的 XML，而不必擔心資料被輕易讀取。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="8ecfe-105">這個程式碼範例會使用進階加密標準 (AES) 演算法 (也稱為 Rijndael)，來解密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="8ecfe-106">如需如何加密 XML 項目使用此程序資訊，請參閱[How to： 使用對稱金鑰加密 XML 項目](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="8ecfe-107">當您使用如 AES 的對稱演算法來加密 XML 資料時，您必須使用相同的金鑰來加密和解密 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="8ecfe-108">此程序中的範例假設使用相同的金鑰來加密已加密的 XML，並且加密和解密的雙方同意使用的演算法和金鑰。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="8ecfe-109">此範例不會儲存或加密在已加密 XML 中的 AES 金鑰。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="8ecfe-110">這個範例適合單一應用程式需要根據記憶體中儲存的工作階段金鑰，或是根據衍生自密碼的強式密碼編譯金鑰，來加密資料。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="8ecfe-111">對於兩個或多個應用程式需要共用加密的 XML 資料的情況，請考慮使用根據非對稱式演算法或 X.509 憑證的加密配置。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="8ecfe-112">使用對稱金鑰解密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="8ecfe-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="8ecfe-113">加密 XML 項目與先前產生的索引鍵中所描述的技術[How to： 使用對稱金鑰加密 XML 項目](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="8ecfe-114">在包含加密 XML 的 <xref:System.Xml.XmlDocument> 物件中尋找 <`EncryptedData`> 項目 (由 XML 加密標準定義)，並建立新的 <xref:System.Xml.XmlElement> 物件來代表該項目。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="8ecfe-115">從先前建立的 <xref:System.Xml.XmlElement> 物件載入原始的 XML 資料，以建立 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="8ecfe-116">建立新 <xref:System.Security.Cryptography.Xml.EncryptedXml> 物件，並使用它來解密使用相同金鑰加密的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="8ecfe-117">將加密的項目取代為 XML 文件中剛解密的純文字項目。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="8ecfe-118">範例</span><span class="sxs-lookup"><span data-stu-id="8ecfe-118">Example</span></span>  
 <span data-ttu-id="8ecfe-119">這個範例假設名為 `"test.xml"` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="8ecfe-120">它同時也假設 `"test.xml"` 包含 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="8ecfe-121">您可以將下列 XML 放入稱為 `test.xml` 的檔案，並使用它搭配此範例。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ecfe-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8ecfe-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="8ecfe-123">若要編譯此範例，您需要包含 `System.Security.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="8ecfe-124">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8ecfe-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8ecfe-125">.NET Framework Security</span></span>  
 <span data-ttu-id="8ecfe-126">絕對不要以純文字儲存密碼編譯金鑰，或以純文字格式在電腦之間傳輸金鑰。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="8ecfe-127">當您完成使用對稱密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8ecfe-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecfe-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ecfe-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="8ecfe-129">操作說明：使用對稱金鑰加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="8ecfe-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
