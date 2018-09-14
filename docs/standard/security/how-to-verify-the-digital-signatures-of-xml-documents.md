---
title: 如何：驗證 XML 文件的數位簽章
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ec813e50bb4dca33c8dda8b41914cfa5d5596c2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507492"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="be10b-102">如何：驗證 XML 文件的數位簽章</span><span class="sxs-lookup"><span data-stu-id="be10b-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="be10b-103">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別，驗證使用數位簽章簽署的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="be10b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span>  <span data-ttu-id="be10b-104">XML 數位簽章 (XMLDSIG) 可讓您驗證在簽署資料後，資料未經過變更。</span><span class="sxs-lookup"><span data-stu-id="be10b-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="be10b-105">如需 XMLDSIG 標準的詳細資訊，請參閱 World Wide Web Consortium (W3C) 規格： http://www.w3.org/TR/xmldsig-core/。</span><span class="sxs-lookup"><span data-stu-id="be10b-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="be10b-106">這個程序中的程式碼範例會示範如何驗證 <`Signature`> 項目所包含的 XML 數位簽章。</span><span class="sxs-lookup"><span data-stu-id="be10b-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="be10b-107">範例會從金鑰容器擷取 RSA 公開金鑰，然後使用金鑰來驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="be10b-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="be10b-108">如需有關建立可以使用這項技術來驗證數位簽章，請參閱[如何： 使用數位簽章簽署 XML 文件](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="be10b-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="be10b-109">驗證 XML 文件的數位簽章</span><span class="sxs-lookup"><span data-stu-id="be10b-109">To verify the digital signature of an XML document</span></span>  
  
1.  <span data-ttu-id="be10b-110">若要驗證文件，您必須使用用於簽章的相同非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="be10b-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="be10b-111">建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定用於簽章的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="be10b-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="be10b-112">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別擷取公用金鑰。</span><span class="sxs-lookup"><span data-stu-id="be10b-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="be10b-113">當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的建構函式時，金鑰會自動依名稱從金鑰容器載入。</span><span class="sxs-lookup"><span data-stu-id="be10b-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="be10b-114">藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="be10b-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="be10b-115"><xref:System.Xml.XmlDocument> 物件包含要驗證的已簽署 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="be10b-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="be10b-116">建立新的 <xref:System.Security.Cryptography.Xml.SignedXml> 物件，並傳遞 <xref:System.Xml.XmlDocument> 物件給它。</span><span class="sxs-lookup"><span data-stu-id="be10b-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="be10b-117">找出 <`signature`> 項目，並建立新的 <xref:System.Xml.XmlNodeList> 物件。</span><span class="sxs-lookup"><span data-stu-id="be10b-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="be10b-118">將第一個 <`signature`> 項目的 XML 載入至 <xref:System.Security.Cryptography.Xml.SignedXml> 物件。</span><span class="sxs-lookup"><span data-stu-id="be10b-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="be10b-119">使用 <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> 方法和 RSA 公開金鑰檢查簽章。</span><span class="sxs-lookup"><span data-stu-id="be10b-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="be10b-120">這個方法會傳回表示成功或失敗的布林值。</span><span class="sxs-lookup"><span data-stu-id="be10b-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="be10b-121">範例</span><span class="sxs-lookup"><span data-stu-id="be10b-121">Example</span></span>  
 <span data-ttu-id="be10b-122">這個範例假設名為 `"test.xml"` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="be10b-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="be10b-123">`"test.xml"`檔案必須使用中所述的技巧簽署[如何： 使用數位簽章簽署 XML 文件](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="be10b-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be10b-124">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="be10b-124">Compiling the Code</span></span>  
  
-   <span data-ttu-id="be10b-125">若要編譯此範例，您需要包含 `System.Security.dll` 的參考。</span><span class="sxs-lookup"><span data-stu-id="be10b-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="be10b-126">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="be10b-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="be10b-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="be10b-127">.NET Framework Security</span></span>  
 <span data-ttu-id="be10b-128">絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="be10b-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="be10b-129">如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[產生的金鑰來加密和解密](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="be10b-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="be10b-130">絕對不要直接將私密金鑰內嵌在您的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="be10b-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="be10b-131">內嵌的金鑰可以輕鬆地從組件讀取[Ildasm.exe （IL 反組譯工具）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)或是藉由在 [記事本] 之類的文字編輯器中開啟組件。</span><span class="sxs-lookup"><span data-stu-id="be10b-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be10b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be10b-132">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="be10b-133">操作說明：使用數位簽章簽署 XML 文件</span><span class="sxs-lookup"><span data-stu-id="be10b-133">How to: Sign XML Documents with Digital Signatures</span></span>](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
