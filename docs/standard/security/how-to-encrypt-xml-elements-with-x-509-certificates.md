---
title: "How to: Encrypt XML Elements with X.509 Certificates | Microsoft Docs"
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
  - "encryption [.NET Framework], X.509 certificates"
  - "cryptography [.NET Framework], X.509 certificates"
  - "System.Security.Cryptography.EncryptedXml class"
  - "XML encryption"
  - "System.Security.Cryptography.X509Certificate2 class"
  - "X.509 certificates"
  - "certificates, X.509 certificates"
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# How to: Encrypt XML Elements with X.509 Certificates
您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密 XML 文件內的項目。  XML 加密是交換或儲存加密 XML 資料的標準方法，不必擔心資料被輕易讀取。  如需 XML 加密標準的詳細資訊，請參閱 XML 加密的全球資訊網協會 \(W3C\) 規格，位於 http:\/\/www.w3.org\/TR\/xmldsig\-core\/。  
  
 您可以使用 XML 加密將任何 XML 項目或文件取代為包含加密 XML 資料的 \<`EncryptedData`\> 項目。  \<`EncryptedData`\> 項目可以包含子項目，而子項目會包含有關加密時所使用之金鑰和程序的資訊。  XML 加密可讓文件中包含多個加密的項目，並允許項目加密多次。  這個程序中的程式碼範例將顯示如何建立 \<`EncryptedData`\> 項目和數個其他子項目，以便稍後在解密時使用。  
  
 此範例會使用兩個金鑰來加密 XML 項目。  它會使用[Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md) 產生測試 X.509 憑證，並將憑證儲存到憑證存放區。  範例接著會以程式設計方式擷取憑證，並使用它使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 方法加密 XML 項目。  就內部而言，<xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 方法會建立個別的工作階段金鑰，並使用它來加密 XML 文件。  這個方法會加密工作階段金鑰，並將它與加密的 XML 一併儲存在新的 \<`EncryptedData`\> 項目中。  
  
 若要解密 XML 項目，只要呼叫 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法，它會自動從存放區擷取 X.509 憑證，並執行必要的解密。  如需如何將使用這個程序加密的 XML 項目解密的詳細資訊，請參閱 [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)。  
  
 這個範例適合多個應用程式需要共用加密資料或應用程式需要在它執行時間之間儲存加密資料的情況。  
  
### 使用 X.509 憑證加密 XML 項目  
  
1.  請使用[Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md) 產生測試 X.509 憑證，並將它放在本機使用者存放區中。  您必須產生交換金鑰，且必須使金鑰可以匯出。  執行下列命令：  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  建立 <xref:System.Security.Cryptography.X509Certificates.X509Store> 物件，並將它初始化以開啟目前使用者存放區。  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  在唯讀模式開啟存放區。  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  使用存放區中的所有憑證初始化 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection>。  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  列舉存放區中的憑證，並尋找適當名稱的憑證。  在此範例中，憑證會命名為 `"CN=XML_ENC_TEST_CERT"`。  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  找到憑證之後，關閉存放區。  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  藉由從磁碟載入 XML 檔案，建立 <xref:System.Xml.XmlDocument> 物件。  <xref:System.Xml.XmlDocument> 物件會包含要加密的 XML 項目。  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  在 <xref:System.Xml.XmlDocument> 物件中尋找指定的項目，並建立新的 <xref:System.Xml.XmlElement> 物件以代表您想要加密的項目。  在此範例中，`"creditcard"` 項目已加密。  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. 建立 <xref:System.Security.Cryptography.Xml.EncryptedXml> 類別的新執行個體，並使用它使用 X.509 憑證加密指定的項目。  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 方法會以 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件傳回已加密的項目。  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. 將來自 <xref:System.Xml.XmlDocument> 物件的原始項目取代為 <xref:System.Security.Cryptography.Xml.EncryptedData> 項目。  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. 儲存 <xref:System.Xml.XmlDocument> 物件。  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## 範例  
 這個範例假設名為 `"test.xml"` 的檔案已存在於和編譯程式相同的目錄中。  它同時也假設 `"test.xml"` 包含 `"creditcard"` 項目。  您可以將下列 XML 放入稱為 `test.xml` 的檔案，並使用它搭配此範例。  
  
```  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## 編譯程式碼  
  
-   若要編譯此範例，您需要包含 `System.Security.dll` 的參考。  
  
-   包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。  
  
## .NET Framework 安全性  
 此範例中使用的 X.509 憑證僅供測試使用。  應用程式應該使用由受信任的憑證授權單位所產生的 X.509 憑證，或使用由 Microsoft Windows 憑證伺服器所產生的憑證。  
  
## 請參閱  
 <xref:System.Security.Cryptography.Xml>   
 [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)