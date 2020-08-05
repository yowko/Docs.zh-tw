---
title: 作法：使用數位簽章簽署 XML 文件
description: 瞭解如何使用數位簽章簽署 XML 檔。 在 .NET 的 System.Security.Cryptography.Xml 命名空間中使用類別。
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSA class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: e1457fd659ab63489bd4cfafd7731a4b098a2791
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557069"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="0f440-104">作法：使用數位簽章簽署 XML 文件</span><span class="sxs-lookup"><span data-stu-id="0f440-104">How to: Sign XML Documents with Digital Signatures</span></span>

<span data-ttu-id="0f440-105">您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別，以數位簽章簽署 XML 文件或 XML 文件的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f440-105">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="0f440-106">XML 數位簽章 (XMLDSIG) 可讓您驗證在簽署資料後，資料未經過變更。</span><span class="sxs-lookup"><span data-stu-id="0f440-106">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="0f440-107">如需 XMLDSIG 標準的詳細資訊，請參閱全球資訊網協會 (W3C) 建議[XML 簽章語法和處理](https://www.w3.org/TR/xmldsig-core/)。</span><span class="sxs-lookup"><span data-stu-id="0f440-107">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f440-108">本文中的程式碼適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="0f440-108">The code in this article applies to Windows.</span></span>

<span data-ttu-id="0f440-109">此程式中的程式碼範例示範如何以數位方式簽署整個 XML 檔，並將簽章附加至 <> 元素中的檔 `Signature` 。</span><span class="sxs-lookup"><span data-stu-id="0f440-109">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="0f440-110">範例會建立 RSA 簽章金鑰、將金鑰加入安全的金鑰容器，然後使用金鑰來數位簽署 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0f440-110">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="0f440-111">金鑰便可以擷取來驗證 XML 數位簽章，或可以用來簽署另一份 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0f440-111">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
<span data-ttu-id="0f440-112">如需如何驗證使用此程式所建立之 XML 數位簽章的相關資訊，請參閱[如何：驗證 Xml 檔的數位簽章](how-to-verify-the-digital-signatures-of-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="0f440-112">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="0f440-113">數位簽署 XML 文件</span><span class="sxs-lookup"><span data-stu-id="0f440-113">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="0f440-114">建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f440-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="0f440-115">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別產生非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="0f440-115">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="0f440-116">當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的建構函式時，金鑰會自動儲存到金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="0f440-116">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="0f440-117">此金鑰會用來簽署 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0f440-117">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="0f440-118">藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-118">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="0f440-119"><xref:System.Xml.XmlDocument> 物件會包含要加密的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="0f440-119">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="0f440-120">建立新的 <xref:System.Security.Cryptography.Xml.SignedXml> 物件，並傳遞 <xref:System.Xml.XmlDocument> 物件給它。</span><span class="sxs-lookup"><span data-stu-id="0f440-120">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="0f440-121">將簽署的 RSA 金鑰加入 <xref:System.Security.Cryptography.Xml.SignedXml> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-121">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="0f440-122">建立描述要簽署項目的 <xref:System.Security.Cryptography.Xml.Reference> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-122">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="0f440-123">若要簽署整份文件，請將 <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> 屬性設為 `""`。</span><span class="sxs-lookup"><span data-stu-id="0f440-123">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="0f440-124">將 <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> 物件加入 <xref:System.Security.Cryptography.Xml.Reference> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-124">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="0f440-125">轉換可讓驗證器工具以簽署者使用的相同方式代表 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="0f440-125">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="0f440-126">XML 資料可以用不同的方式代表，因此這個步驟對於驗證很重要。</span><span class="sxs-lookup"><span data-stu-id="0f440-126">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="0f440-127">將 <xref:System.Security.Cryptography.Xml.Reference> 物件加入 <xref:System.Security.Cryptography.Xml.SignedXml> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-127">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="0f440-128">呼叫 <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> 方法來計算簽章。</span><span class="sxs-lookup"><span data-stu-id="0f440-128">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="0f440-129"> (<> 專案) ，抓取簽章的 XML 標記法 `Signature` ，並將其儲存至新的 <xref:System.Xml.XmlElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-129">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="0f440-130">將項目附加至 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="0f440-130">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="0f440-131">儲存文件。</span><span class="sxs-lookup"><span data-stu-id="0f440-131">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="0f440-132">範例</span><span class="sxs-lookup"><span data-stu-id="0f440-132">Example</span></span>  
 <span data-ttu-id="0f440-133">這個範例假設名為 `test.xml` 的檔案已存在於和編譯程式相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0f440-133">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="0f440-134">您可以將下列 XML 放入稱為 `test.xml` 的檔案，並使用它搭配此範例。</span><span class="sxs-lookup"><span data-stu-id="0f440-134">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f440-135">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0f440-135">Compiling the Code</span></span>  
  
- <span data-ttu-id="0f440-136">在以 .NET Framework 為目標的專案中，包含的參考 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="0f440-136">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="0f440-137">在以 .NET Core 或 .NET 5 為目標的專案中，安裝 NuGet 封裝[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="0f440-137">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="0f440-138">包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="0f440-138">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="0f440-139">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="0f440-139">.NET Security</span></span>

<span data-ttu-id="0f440-140">絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="0f440-140">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="0f440-141">如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[產生加密和解密的金鑰](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="0f440-141">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="0f440-142">絕對不要直接將私密金鑰內嵌在您的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f440-142">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="0f440-143">您可以使用[Ildasm.exe (IL](../../framework/tools/ildasm-exe-il-disassembler.md)解譯器) 或在文字編輯器（如 [記事本]）中開啟元件，輕鬆地從元件中讀取內嵌索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0f440-143">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f440-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f440-144">See also</span></span>

- [<span data-ttu-id="0f440-145">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="0f440-145">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="0f440-146">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="0f440-146">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="0f440-147">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="0f440-147">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="0f440-148">作法：驗證 XML 文件的數位簽章</span><span class="sxs-lookup"><span data-stu-id="0f440-148">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
- [<span data-ttu-id="0f440-149">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="0f440-149">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
