---
title: "如何：使用非對稱金鑰加密 XML 項目"
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
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cadd6e5af8ed95da34091bc3a9f3ac8d5af4e9cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="35b55-102">如何：使用非對稱金鑰加密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="35b55-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="35b55-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密 XML 文件內的項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="35b55-104">XML 加密是交換或儲存加密 XML 資料的標準方法，不必擔心資料被輕易讀取。</span><span class="sxs-lookup"><span data-stu-id="35b55-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="35b55-105">如需 XML 加密標準的詳細資訊，請參閱 XML 加密的全球資訊網協會 (W3C) 規格，位於 http://www.w3.org/TR/xmldsig-core/。</span><span class="sxs-lookup"><span data-stu-id="35b55-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="35b55-106">您可以使用 XML 加密將任何 XML 項目或文件取代為包含加密 XML 資料的 <`EncryptedData`> 項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="35b55-107"><`EncryptedData`> 項目也可以包含子項目，而子項目會包含有關加密時所使用之金鑰和程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="35b55-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="35b55-108">XML 加密可讓文件中包含多個加密的元素，並允許元素加密多次。</span><span class="sxs-lookup"><span data-stu-id="35b55-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="35b55-109">這個程序中的程式碼範例將顯示如何建立 <`EncryptedData`> 項目和數個其他子項目，以便稍後在解密時使用。</span><span class="sxs-lookup"><span data-stu-id="35b55-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="35b55-110">此範例會使用兩個金鑰來加密 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="35b55-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="35b55-111">它會產生 RSA 公開/私密金鑰組，並將金鑰組儲存到安全的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="35b55-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="35b55-112">接著這個範例會使用進階加密標準 (AES) 演算法 (也稱為 Rijndael 演算法) 建立不同的工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="35b55-113">範例會使用 AES 工作階段金鑰來加密 XML 文件，然後使用 RSA 公開金鑰來加密 AES 工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="35b55-114">最後，範例會將加密的 AES 工作階段金鑰和加密的 XML 資料儲存在 XML 文件內的新 <`EncryptedData`> 項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="35b55-115">若要解密 XML 項目，您可以從金鑰容器中擷取 RSA 私密金鑰、用它來解密工作階段金鑰，然後使用工作階段金鑰來解密文件。</span><span class="sxs-lookup"><span data-stu-id="35b55-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="35b55-116">如需如何使用這個程序加密 XML 項目解密的詳細資訊，請參閱[How to： 使用非對稱金鑰解密 XML 項目](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="35b55-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="35b55-117">這個範例適合多個應用程式需要共用加密資料或應用程式需要在它執行時間之間儲存加密資料的情況。</span><span class="sxs-lookup"><span data-stu-id="35b55-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="35b55-118">使用非對稱金鑰加密 XML 項目</span><span class="sxs-lookup"><span data-stu-id="35b55-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="35b55-119">建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="35b55-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="35b55-120">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別產生對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="35b55-121">當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的建構函式時，金鑰會自動儲存到金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="35b55-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="35b55-122">這個金鑰會用來加密 AES 工作階段金鑰，而且可以稍後擷取來進行解密。</span><span class="sxs-lookup"><span data-stu-id="35b55-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="35b55-123">藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="35b55-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="35b55-124"><xref:System.Xml.XmlDocument> 物件會包含要加密的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="35b55-125">在 <xref:System.Xml.XmlDocument> 物件中尋找指定的項目，並建立新的 <xref:System.Xml.XmlElement> 物件以代表您想要加密的項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="35b55-126">在此範例中，`"creditcard"` 元素已加密。</span><span class="sxs-lookup"><span data-stu-id="35b55-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="35b55-127">使用 <xref:System.Security.Cryptography.RijndaelManaged> 類別建立新的工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="35b55-128">這個金鑰會加密 XML 項目，並再加密本身並放在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="35b55-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="35b55-129">建立 <xref:System.Security.Cryptography.Xml.EncryptedXml> 類別的新執行個體，並使用它使用工作階段金鑰加密指定的項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="35b55-130"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> 方法會以加密位元組陣列傳回已加密的項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="35b55-131">建構 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件並填入加密 XML 項目的 URL 識別項。</span><span class="sxs-lookup"><span data-stu-id="35b55-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="35b55-132">這個 URL 識別項可讓解密的一方知道 XML 包含加密的項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="35b55-133">您可以使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> 欄位來指定 URL 識別項。</span><span class="sxs-lookup"><span data-stu-id="35b55-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="35b55-134">純文字 XML 項目會取代為  <`EncryptedData`> 項目，它會由這個 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件封裝。</span><span class="sxs-lookup"><span data-stu-id="35b55-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="35b55-135">建立 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 物件，它會初始化為用來產生工作階段金鑰之密碼編譯演算法的 URL 識別項。</span><span class="sxs-lookup"><span data-stu-id="35b55-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="35b55-136">將 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 物件傳遞至 <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="35b55-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="35b55-137">建立 <xref:System.Security.Cryptography.Xml.EncryptedKey> 物件，以包含加密工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="35b55-138">加密工作階段金鑰、將它加入 <xref:System.Security.Cryptography.Xml.EncryptedKey> 物件，然後輸入工作階段金鑰名稱和金鑰識別項 URL。</span><span class="sxs-lookup"><span data-stu-id="35b55-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="35b55-139">建立新的 <xref:System.Security.Cryptography.Xml.DataReference> 物件，將加密的資料對應至特定工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="35b55-140">此選用步驟可讓您輕鬆地指定 XML 文件的多個部分是由單一金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="35b55-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="35b55-141">將加密的金鑰加入 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。</span><span class="sxs-lookup"><span data-stu-id="35b55-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="35b55-142">建立新的 <xref:System.Security.Cryptography.Xml.KeyInfo> 物件，指定 RSA 金鑰的名稱。</span><span class="sxs-lookup"><span data-stu-id="35b55-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="35b55-143">將它加入 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。</span><span class="sxs-lookup"><span data-stu-id="35b55-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="35b55-144">這有助於解密方識別要解密工作階段金鑰時所使用的正確非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="35b55-145">將加密項目資料加入 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。</span><span class="sxs-lookup"><span data-stu-id="35b55-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="35b55-146">將來自原始 <xref:System.Xml.XmlDocument> 物件的項目取代為 <xref:System.Security.Cryptography.Xml.EncryptedData> 項目。</span><span class="sxs-lookup"><span data-stu-id="35b55-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="35b55-147">儲存 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="35b55-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="35b55-148">範例</span><span class="sxs-lookup"><span data-stu-id="35b55-148">Example</span></span>  
 <span data-ttu-id="35b55-149">這個範例假設名為 `"test.xml"` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="35b55-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="35b55-150">它同時也假設 `"test.xml"` 包含 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="35b55-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="35b55-151">您可以將下列 XML 放入稱為 `test.xml` 的檔案，並使用它搭配此範例。</span><span class="sxs-lookup"><span data-stu-id="35b55-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35b55-152">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="35b55-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="35b55-153">若要編譯此範例，您需要包含 `System.Security.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="35b55-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="35b55-154">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="35b55-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="35b55-155">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="35b55-155">.NET Framework Security</span></span>  
 <span data-ttu-id="35b55-156">絕對不要以純文字儲存對稱密碼編譯金鑰，或以純文字格式在電腦之間傳輸對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="35b55-157">此外，絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="35b55-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="35b55-158">如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[產生加密和解密金鑰](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="35b55-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="35b55-159">絕對不要直接將金鑰內嵌在您的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="35b55-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="35b55-160">內嵌的金鑰可以輕鬆地從組件使用讀取[Ildasm.exe （IL 解譯器）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)或藉由在文字編輯器例如記事本中開啟組件。</span><span class="sxs-lookup"><span data-stu-id="35b55-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="35b55-161">當您使用完密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="35b55-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="35b55-162">偵錯工具有時可以從記憶體讀取密碼編譯金鑰，或是在記憶體位置被分頁至磁碟的情況下從硬碟機讀取。</span><span class="sxs-lookup"><span data-stu-id="35b55-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b55-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="35b55-163">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="35b55-164">操作說明：使用非對稱金鑰解密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="35b55-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
