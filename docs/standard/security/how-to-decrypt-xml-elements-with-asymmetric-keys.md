---
title: "How to: Decrypt XML Elements with Asymmetric Keys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "System.Security.Cryptography.RSACryptoServiceProvider class"
  - "asymmetric keys"
  - "System.Security.Cryptography.EncryptedXml class"
  - "XML encryption"
  - "decryption"
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# How to: Decrypt XML Elements with Asymmetric Keys
您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密和解密 XML 文件內的項目。  XML 加密是交換或儲存加密 XML 資料的標準方法，不必擔心資料被輕易讀取。  如需 XML 加密標準的詳細資訊，請參閱全球資訊網協會 \(W3C\) 的建議 [XML 簽章語法和處理](http://go.microsoft.com/fwlink/?LinkID=136777)。  
  
 此程序中的範例會解密已使用 [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)中所述方法加密的 XML 項目。  它會找出 \<`EncryptedData`\> 項目、解密該項目，然後再以原始純文字 XML 項目取代該項目。  
  
 此範例會使用兩個金鑰來解密 XML 項目。  它會從金鑰容器中，擷取先前產生的 RSA 私密金鑰，然後使用 RSA 金鑰來解密儲存在 \<`EncryptedData`\> 項目之 \<`EncryptedKey`\> 項目中的工作階段金鑰。  範例接著會使用工作階段金鑰解密 XML 項目。  
  
 這個範例適合多個應用程式必須共用加密資料或應用程式必須在它執行時間之間儲存加密資料的情況。  
  
### 使用非對稱金鑰解密 XML 項目  
  
1.  建立 <xref:System.Security.Cryptography.CspParameters> 物件，並指定金鑰容器的名稱。  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件從容器擷取先前產生的非對稱金鑰。  當您將 <xref:System.Security.Cryptography.CspParameters> 物件傳遞到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 建構函式時，金鑰會自動從金鑰容器擷取。  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  建立新的 <xref:System.Security.Cryptography.Xml.EncryptedXml> 物件以解密文件。  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  加入金鑰\/名稱對應以將 RSA 金鑰與應該解密之文件中的項目相關聯。  您必須使用與加密文件時所使用金鑰相同的名稱。  請注意，這個名稱與用來識別步驟 1 中所指定金鑰容器中的金鑰名稱不同。  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  呼叫 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法來解密 \<`EncryptedData`\> 項目。  這個方法會使用 RSA 金鑰來解密工作階段金鑰，並會自動使用工作階段金鑰解密 XML 項目。  它也會自動將 \<`EncryptedData`\> 項目取代為原始的純文字。  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  儲存 XML 文件。  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## 範例  
 這個範例假設名為 `test.xml` 的檔案已存在於和編譯程式相同的目錄中。  它也假設 `test.xml` 包含的 XML 項目是使用 [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)中所述方法加密。  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## 編譯程式碼  
  
-   若要編譯此範例，您需要包含 `System.Security.dll` 的參考。  
  
-   包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。  
  
## .NET Framework 安全性  
 絕對不要以純文字儲存對稱密碼編譯金鑰，或以純文字格式在電腦之間傳輸對稱金鑰。  此外，絕對不要以純文字儲存或傳輸非對稱金鑰組的私密金鑰。  如需對稱和非對稱密碼編譯金鑰的詳細資訊，請參閱[Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)。  
  
 絕對不要直接將金鑰內嵌在您的原始程式碼。  內嵌的金鑰可以藉由使用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 或是藉由在文字編輯器例如記事本中開啟組件，輕鬆地從組件讀取。  
  
 當您使用完密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。  偵錯工具有時可以從記憶體讀取密碼編譯金鑰，或是在記憶體位置被分頁至磁碟的情況下從硬碟機讀取。  
  
## 請參閱  
 <xref:System.Security.Cryptography.Xml>   
 [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)