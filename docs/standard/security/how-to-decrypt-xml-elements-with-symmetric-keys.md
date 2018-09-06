---
title: 如何：使用對稱金鑰解密 XML 項目
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38bb22de14ecef618d45f54cced32af57542d3df
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866841"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>如何：使用對稱金鑰解密 XML 項目
您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密 XML 文件內的項目。  XML 加密可讓您儲存或傳輸機密的 XML，而不必擔心資料被輕易讀取。  這個程式碼範例會使用進階加密標準 (AES) 演算法 (也稱為 Rijndael)，來解密 XML 項目。  
  
 如何加密 XML 項目使用此程序的相關資訊，請參閱[如何： 使用對稱金鑰加密 XML 項目](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)。  
  
 當您使用如 AES 的對稱演算法來加密 XML 資料時，您必須使用相同的金鑰來加密和解密 XML 資料。  此程序中的範例假設使用相同的金鑰來加密已加密的 XML，並且加密和解密的雙方同意使用的演算法和金鑰。  此範例不會儲存或加密在已加密 XML 中的 AES 金鑰。  
  
 這個範例適合單一應用程式需要根據記憶體中儲存的工作階段金鑰，或是根據衍生自密碼的強式密碼編譯金鑰，來加密資料。  對於兩個或多個應用程式需要共用加密的 XML 資料的情況，請考慮使用根據非對稱式演算法或 X.509 憑證的加密配置。  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>使用對稱金鑰解密 XML 項目  
  
1.  具有使用中所述的技巧先前產生的金鑰加密 XML 項目[如何： 使用對稱金鑰加密 XML 項目](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)。  
  
2.  在包含加密 XML 的 <xref:System.Xml.XmlDocument> 物件中尋找 <`EncryptedData`> 項目 (由 XML 加密標準定義)，並建立新的 <xref:System.Xml.XmlElement> 物件來代表該項目。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  從先前建立的 <xref:System.Xml.XmlElement> 物件載入原始的 XML 資料，以建立 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  建立新 <xref:System.Security.Cryptography.Xml.EncryptedXml> 物件，並使用它來解密使用相同金鑰加密的 XML 資料。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  將加密的項目取代為 XML 文件中剛解密的純文字項目。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>範例  
 這個範例假設名為 `"test.xml"` 的檔案已存在於和編譯程式相同的目錄中。  它同時也假設 `"test.xml"` 包含 `"creditcard"` 元素。  您可以將下列 XML 放入稱為 `test.xml` 的檔案，並使用它搭配此範例。  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   若要編譯此範例，您需要包含 `System.Security.dll` 的參考。  
  
-   包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 絕對不要以純文字儲存密碼編譯金鑰，或以純文字格式在電腦之間傳輸金鑰。  
  
 當您完成使用對稱密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Cryptography.Xml>  
- [操作說明：使用對稱金鑰加密 XML 元素](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
