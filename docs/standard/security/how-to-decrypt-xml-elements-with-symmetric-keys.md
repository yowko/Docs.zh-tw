---
title: 作法：使用對稱金鑰解密 XML 元素
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: 8c9f75442e04b76369b5b2c5c1b266ce2a511a63
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555743"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>作法：使用對稱金鑰解密 XML 元素

您可以使用 <xref:System.Security.Cryptography.Xml> 命名空間中的類別來加密 XML 文件內的項目。  XML 加密可讓您儲存或傳輸機密的 XML，而不必擔心資料被輕易讀取。  這個程式碼範例會使用進階加密標準 (AES) 演算法來解密 XML 元素。
  
 如需如何使用此程式加密 XML 元素的詳細資訊，請參閱[如何：使用對稱金鑰加密 xml](how-to-encrypt-xml-elements-with-symmetric-keys.md)專案。  
  
 當您使用如 AES 的對稱演算法來加密 XML 資料時，您必須使用相同的金鑰來加密和解密 XML 資料。  此程序中的範例假設使用相同的金鑰來加密已加密的 XML，並且加密和解密的雙方同意使用的演算法和金鑰。  此範例不會儲存或加密在已加密 XML 中的 AES 金鑰。  
  
 這個範例適合單一應用程式需要根據記憶體中儲存的工作階段金鑰，或是根據衍生自密碼的強式密碼編譯金鑰，來加密資料。  對於兩個或多個應用程式需要共用加密的 XML 資料的情況，請考慮使用根據非對稱式演算法或 X.509 憑證的加密配置。  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>使用對稱金鑰解密 XML 項目  
  
1. 使用 how [to：使用對稱金鑰加密 xml](how-to-encrypt-xml-elements-with-symmetric-keys.md)專案中所述的技術，以先前產生的金鑰來加密 xml 元素。  
  
2. `EncryptedData`在包含加密 xml 的物件中，尋找 XML 加密標準) 所定義的 <> (元素 <xref:System.Xml.XmlDocument> ，並建立新的 <xref:System.Xml.XmlElement> 物件來代表該元素。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. 從先前建立的 <xref:System.Xml.XmlElement> 物件載入原始的 XML 資料，以建立 <xref:System.Security.Cryptography.Xml.EncryptedData> 物件。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. 建立新 <xref:System.Security.Cryptography.Xml.EncryptedXml> 物件，並使用它來解密使用相同金鑰加密的 XML 資料。  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. 將加密的項目取代為 XML 文件中剛解密的純文字項目。  
  
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
  
- 在以 .NET Framework 為目標的專案中，包含的參考 `System.Security.dll` 。

- 在以 .NET Core 或 .NET 5 為目標的專案中，安裝 NuGet 封裝[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。
  
- 包含下列命名空間：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。  
  
## <a name="net-security"></a>.NET 安全性
  
絕對不要以純文字儲存密碼編譯金鑰，或以純文字格式在電腦之間傳輸金鑰。  
  
當您完成使用對稱密碼編譯金鑰，請從記憶體清除它，方法是將每個位元組設定為零，或呼叫 Managed 密碼編譯類別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法。  
  
## <a name="see-also"></a>另請參閱

- [密碼編譯模型](cryptography-model.md)
- [密碼編譯服務](cryptographic-services.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [作法：使用對稱金鑰加密 XML 元素](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
