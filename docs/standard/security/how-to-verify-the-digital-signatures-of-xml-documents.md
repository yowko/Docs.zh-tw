---
title: 作法：驗證 XML 文件的數位簽章
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: b9b2dc6a558d1fd6acd2922a7c8ad82ce8776c26
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557043"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="b5e91-102">作法：驗證 XML 文件的數位簽章</span><span class="sxs-lookup"><span data-stu-id="b5e91-102">How to: Verify the Digital Signatures of XML Documents</span></span>

<span data-ttu-id="b5e91-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別，驗證使用數位簽章簽署的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="b5e91-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="b5e91-104">XML 數位簽章 (XMLDSIG) 可讓您驗證在簽署資料後，資料未經過變更。</span><span class="sxs-lookup"><span data-stu-id="b5e91-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="b5e91-105">如需 XMLDSIG 標準的詳細資訊，請參閱全球資訊網協會 (W3C) 規格，網址為 <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="b5e91-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b5e91-106">本文中的程式碼適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="b5e91-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="b5e91-107">此程式中的程式碼範例示範如何驗證封裝含在 <> 元素中的 XML 數位簽章 `Signature` 。</span><span class="sxs-lookup"><span data-stu-id="b5e91-107">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="b5e91-108">範例會從金鑰容器擷取 RSA 公開金鑰，然後使用金鑰來驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="b5e91-108">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
<span data-ttu-id="b5e91-109">如需如何使用這項技術來建立可驗證之數位簽章的相關資訊，請參閱[如何：使用數位簽章簽署 XML 檔](how-to-sign-xml-documents-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e91-109">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="b5e91-110">驗證 XML 文件的數位簽章</span><span class="sxs-lookup"><span data-stu-id="b5e91-110">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="b5e91-111">若要驗證文件，您必須使用用於簽章的相同非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="b5e91-111">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="b5e91-112">建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定用於簽章的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="b5e91-112">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="b5e91-113">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別擷取公用金鑰。</span><span class="sxs-lookup"><span data-stu-id="b5e91-113">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="b5e91-114">當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的建構函式時，金鑰會自動依名稱從金鑰容器載入。</span><span class="sxs-lookup"><span data-stu-id="b5e91-114">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="b5e91-115">藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="b5e91-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="b5e91-116"><xref:System.Xml.XmlDocument> 物件包含要驗證的已簽署 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="b5e91-116">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="b5e91-117">建立新的 <xref:System.Security.Cryptography.Xml.SignedXml> 物件，並傳遞 <xref:System.Xml.XmlDocument> 物件給它。</span><span class="sxs-lookup"><span data-stu-id="b5e91-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="b5e91-118">尋找 <`signature`> 元素，並建立新的 <xref:System.Xml.XmlNodeList> 物件。</span><span class="sxs-lookup"><span data-stu-id="b5e91-118">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="b5e91-119">將第一個 <> 元素的 XML 載入 `signature` 至 <xref:System.Security.Cryptography.Xml.SignedXml> 物件。</span><span class="sxs-lookup"><span data-stu-id="b5e91-119">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="b5e91-120">使用 <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> 方法和 RSA 公開金鑰檢查簽章。</span><span class="sxs-lookup"><span data-stu-id="b5e91-120">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="b5e91-121">這個方法會傳回表示成功或失敗的布林值。</span><span class="sxs-lookup"><span data-stu-id="b5e91-121">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b5e91-122">範例</span><span class="sxs-lookup"><span data-stu-id="b5e91-122">Example</span></span>

<span data-ttu-id="b5e91-123">這個範例假設名為 `"test.xml"` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="b5e91-123">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="b5e91-124">檔案 `"test.xml"` 必須使用[如何：使用數位簽章簽署 XML](how-to-sign-xml-documents-with-digital-signatures.md)檔中所述的技術來簽署。</span><span class="sxs-lookup"><span data-stu-id="b5e91-124">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5e91-125">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b5e91-125">Compiling the Code</span></span>  
  
- <span data-ttu-id="b5e91-126">在以 .NET Framework 為目標的專案中，包含的參考 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="b5e91-126">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="b5e91-127">在以 .NET Core 或 .NET 5 為目標的專案中，安裝 NuGet 封裝[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="b5e91-127">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="b5e91-128">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="b5e91-128">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="b5e91-129">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="b5e91-129">.NET Security</span></span>

<span data-ttu-id="b5e91-130">絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b5e91-130">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="b5e91-131">如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[產生加密和解密的金鑰](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e91-131">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="b5e91-132">絕對不要直接將私密金鑰內嵌在您的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b5e91-132">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="b5e91-133">您可以使用[Ildasm.exe (IL](../../framework/tools/ildasm-exe-il-disassembler.md)解譯器) 或在文字編輯器（如 [記事本]）中開啟元件，輕鬆地從元件中讀取內嵌索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b5e91-133">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e91-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5e91-134">See also</span></span>

- [<span data-ttu-id="b5e91-135">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="b5e91-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="b5e91-136">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="b5e91-136">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="b5e91-137">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="b5e91-137">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="b5e91-138">作法：使用數位簽章簽署 XML 文件</span><span class="sxs-lookup"><span data-stu-id="b5e91-138">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
- [<span data-ttu-id="b5e91-139">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="b5e91-139">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
