---
title: HOW TO：使用數位簽章簽署 XML 文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49999ae8b66b01ca71c0027bdf43c13272fbe8a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622620"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>HOW TO：使用數位簽章簽署 XML 文件
您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別，以數位簽章簽署 XML 文件或 XML 文件的一部分。  XML 數位簽章 (XMLDSIG) 可讓您驗證在簽署資料後，資料未經過變更。  如需 XMLDSIG 標準的詳細資訊，請參閱 World Wide Web Consortium (W3C) 建議事項[XML 簽章語法和處理](https://www.w3.org/TR/xmldsig-core/)。  
  
 這個程序中的程式碼範例會示範如何數位簽署整份 XML 文件，並將簽章附加到 <`Signature`> 項目的文件中。  範例會建立 RSA 簽章金鑰、將金鑰加入安全的金鑰容器，然後使用金鑰來數位簽署 XML 文件。  金鑰便可以擷取來驗證 XML 數位簽章，或可以用來簽署另一份 XML 文件。  
  
 如需有關如何驗證 XML 數位簽章使用此程序所建立的資訊，請參閱[How to:驗證 XML 文件的數位簽章](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)。  
  
### <a name="to-digitally-sign-an-xml-document"></a>數位簽署 XML 文件  
  
1.  建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定金鑰容器的名稱。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別產生非對稱金鑰。  當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的建構函式時，金鑰會自動儲存到金鑰容器。  此金鑰會用來簽署 XML 文件。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。  <xref:System.Xml.XmlDocument> 物件會包含要加密的 XML 項目。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  建立新的 <xref:System.Security.Cryptography.Xml.SignedXml> 物件，並傳遞 <xref:System.Xml.XmlDocument> 物件給它。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  將簽署的 RSA 金鑰加入 <xref:System.Security.Cryptography.Xml.SignedXml> 物件。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  建立描述要簽署項目的 <xref:System.Security.Cryptography.Xml.Reference> 物件。  若要簽署整份文件，請將 <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> 屬性設為 `""`。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  將 <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> 物件加入 <xref:System.Security.Cryptography.Xml.Reference> 物件。  轉換可讓驗證器工具以簽署者使用的相同方式代表 XML 資料。  XML 資料可以用不同的方式代表，因此這個步驟對於驗證很重要。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  將 <xref:System.Security.Cryptography.Xml.Reference> 物件加入 <xref:System.Security.Cryptography.Xml.SignedXml> 物件。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. 呼叫 <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> 方法來計算簽章。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. 擷取簽章的 XML 表示 (<`Signature`> 項目)，並將它儲存在新的 <xref:System.Xml.XmlElement> 物件內。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. 將項目附加至 <xref:System.Xml.XmlDocument> 物件。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. 儲存文件。  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>範例  
 這個範例假設名為 `test.xml` 的檔案已存在於和編譯程式相同的目錄中。  您可以將下列 XML 放入稱為 `test.xml` 的檔案，並使用它搭配此範例。  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   若要編譯此範例，您需要包含 `System.Security.dll` 的參考。  
  
-   包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。  如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[產生的金鑰來加密和解密](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)。  
  
 絕對不要直接將私密金鑰內嵌在您的原始程式碼。  內嵌的金鑰可以輕鬆地從組件讀取[Ildasm.exe （IL 反組譯工具）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)或是藉由在 [記事本] 之類的文字編輯器中開啟組件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Cryptography.Xml>
- [如何：驗證 XML 文件的數位簽章](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
