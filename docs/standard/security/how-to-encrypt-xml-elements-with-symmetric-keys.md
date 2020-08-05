---
title: 作法：使用對稱金鑰加密 XML 元素
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET], symmetric keys
- encryption [.NET], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- Advanced Encryption Standard algorithm
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: dd69ec6a5317f7f6f800cd225d920a1934c77a0c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555809"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="50370-102">作法：使用對稱金鑰加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="50370-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="50370-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密 XML 文件內的項目。</span><span class="sxs-lookup"><span data-stu-id="50370-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="50370-104">XML 加密可讓您儲存或傳輸機密的 XML，而不必擔心資料被輕易讀取。</span><span class="sxs-lookup"><span data-stu-id="50370-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="50370-105">此程式會使用進階加密標準 (AES) 演算法來加密 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="50370-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>  
  
 <span data-ttu-id="50370-106">如需如何解密使用此程式加密之 XML 元素的詳細資訊，請參閱[如何：使用對稱金鑰解密 Xml 元素](how-to-decrypt-xml-elements-with-symmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="50370-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="50370-107">當您使用如 AES 的對稱演算法來加密 XML 資料時，您必須使用相同的金鑰來加密和解密 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="50370-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="50370-108">此程序中的範例假設將使用相同的金鑰來解密已加密的 XML，並且加密和解密的雙方同意使用的演算法和金鑰。</span><span class="sxs-lookup"><span data-stu-id="50370-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="50370-109">此範例不會儲存或加密在已加密 XML 中的 AES 金鑰。</span><span class="sxs-lookup"><span data-stu-id="50370-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="50370-110">這個範例適合單一應用程式需要根據記憶體中儲存的工作階段金鑰，或是根據衍生自密碼的強式密碼編譯金鑰，來加密資料。</span><span class="sxs-lookup"><span data-stu-id="50370-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="50370-111">對於兩個或多個應用程式需要共用加密的 XML 資料的情況，請考慮使用根據非對稱式演算法或 X.509 憑證的加密配置。</span><span class="sxs-lookup"><span data-stu-id="50370-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="50370-112">使用對稱金鑰加密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="50370-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="50370-113">使用 <xref:System.Security.Cryptography.Aes> 類別產生對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="50370-113">Generate a symmetric key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="50370-114">此金鑰會用來加密 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="50370-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="50370-115">藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="50370-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="50370-116"><xref:System.Xml.XmlDocument> 物件會包含要加密的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="50370-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="50370-117">在 <xref:System.Xml.XmlDocument> 物件中尋找指定的項目，並建立新的 <xref:System.Xml.XmlElement> 物件以代表您想要加密的項目。</span><span class="sxs-lookup"><span data-stu-id="50370-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="50370-118">在此範例中，`"creditcard"` 元素已加密。</span><span class="sxs-lookup"><span data-stu-id="50370-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="50370-119">建立 <xref:System.Security.Cryptography.Xml.EncryptedXml> 類別的新執行個體，並使用它來利用對稱金鑰加密 <xref:System.Xml.XmlElement>。</span><span class="sxs-lookup"><span data-stu-id="50370-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="50370-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> 方法會以加密位元組陣列傳回已加密的項目。</span><span class="sxs-lookup"><span data-stu-id="50370-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="50370-121">建構 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件並填入 XML 加密項目的 URL 識別項。</span><span class="sxs-lookup"><span data-stu-id="50370-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="50370-122">這個 URL 識別項可讓解密的一方知道 XML 包含加密的項目。</span><span class="sxs-lookup"><span data-stu-id="50370-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="50370-123">您可以使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> 欄位來指定 URL 識別項。</span><span class="sxs-lookup"><span data-stu-id="50370-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="50370-124">建立 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 物件，它會初始化為用來產生金鑰之密碼編譯演算法的 URL 識別項。</span><span class="sxs-lookup"><span data-stu-id="50370-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="50370-125">將 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 物件傳遞至 <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="50370-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="50370-126">將加密項目資料加入 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。</span><span class="sxs-lookup"><span data-stu-id="50370-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="50370-127">將來自原始 <xref:System.Xml.XmlDocument> 物件的項目取代為 <xref:System.Security.Cryptography.Xml.EncryptedData> 項目。</span><span class="sxs-lookup"><span data-stu-id="50370-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="50370-128">範例</span><span class="sxs-lookup"><span data-stu-id="50370-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="50370-129">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="50370-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="50370-130">在以 .NET Framework 為目標的專案中，包含的參考 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="50370-130">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="50370-131">在以 .NET Core 或 .NET 5 為目標的專案中，安裝 NuGet 封裝[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="50370-131">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="50370-132">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="50370-132">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="50370-133">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="50370-133">.NET Security</span></span>

<span data-ttu-id="50370-134">絕對不要以純文字儲存密碼編譯金鑰，或以純文字格式在電腦之間傳輸金鑰。</span><span class="sxs-lookup"><span data-stu-id="50370-134">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="50370-135">請改用安全的金鑰容器來儲存密碼編譯金鑰。</span><span class="sxs-lookup"><span data-stu-id="50370-135">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
<span data-ttu-id="50370-136">當您使用完密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="50370-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50370-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50370-137">See also</span></span>

- <span data-ttu-id="50370-138">[密碼編譯模型](cryptography-model.md)-說明如何在基類庫中執行密碼編譯。</span><span class="sxs-lookup"><span data-stu-id="50370-138">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="50370-139">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="50370-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="50370-140">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="50370-140">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="50370-141">作法：使用對稱金鑰解密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="50370-141">How to: Decrypt XML Elements with Symmetric Keys</span></span>](how-to-decrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="50370-142">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="50370-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
