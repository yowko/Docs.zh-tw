---
title: 從 XslTransform 類別移轉
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8b8c21af8ca0a21d97e8246ad82c42aaaf4974
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190984"
---
# <a name="migrating-from-the-xsltransform-class"></a>從 XslTransform 類別移轉
XSLT 架構已在 [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] 版本中重新設計。 <xref:System.Xml.Xsl.XslTransform> 類別取代了 <xref:System.Xml.Xsl.XslCompiledTransform> 類別。  
  
 下列章節將說明 <xref:System.Xml.Xsl.XslCompiledTransform> 與 <xref:System.Xml.Xsl.XslTransform> 類別之間的一些主要差異。  
  
## <a name="performance"></a>效能  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別包括許多效能改進。 類似於 Common Language Runtime (CLR) 處理其他程式設計語言的方式，新版 XSLT 處理器會將 XSLT 樣式表編譯成常見的中繼格式。 樣式表一旦編譯完畢，便可對其進行快取及重複使用。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別還包括其他最佳化功能，讓其速度要比 <xref:System.Xml.Xsl.XslTransform> 類別快很多。  
  
> [!NOTE]
>  雖然 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的整體效能優於 <xref:System.Xml.Xsl.XslTransform> 類別，但是在轉換時第一次呼叫 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslCompiledTransform> 方法之執行速度可能會比 <xref:System.Xml.Xsl.XslTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslTransform> 方法慢許多。 這是因為在載入之前必須先編譯 XSLT 檔案。 如需詳細資訊，請參閱下列部落格文章：[XslCompiledTransform 比 XslTransform 還慢嗎？](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/) (英文)  
  
## <a name="security"></a>安全性  
 根據預設，<xref:System.Xml.Xsl.XslCompiledTransform> 類別會停用 XSLT `document()` 函式與內嵌指令碼的支援。 您可藉由建立啟用這些功能的 <xref:System.Xml.Xsl.XsltSettings> 物件，並將其傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法來啟用功能。 下列範例將示範如何啟用指令碼及執行 XSLT 轉換。  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 如需詳細資訊，請參閱 [XSLT 安全性考量](../../../../docs/standard/data/xml/xslt-security-considerations.md)。  
  
## <a name="new-features"></a>新功能  
  
### <a name="temporary-files"></a>暫存檔案  
 暫存檔案有時會在 XSLT 處理期間產生。 如果樣式表包含指令碼區塊，或是在編譯時將偵錯設定為 true，則可能會在 %TEMP% 資料夾中建立暫存檔案。 可能會有一些案例是因為時間問題而刪除某些暫存檔案。 例如，如果目前的 AppDomain 或偵錯工具正在使用檔案，則 <xref:System.CodeDom.Compiler.TempFileCollection> 物件的完成項無法將其移除。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> 屬性可用於其他清除工作，以確定所有的暫存檔案都已從用戶端中移除。  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>xsl:output 項目和 XmlWriter 的支援  
 當轉換輸出傳送到 <xref:System.Xml.Xsl.XslTransform> 物件時，`xsl:output` 類別會忽略 <xref:System.Xml.XmlWriter> 設定。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別具有 <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> 屬性，此屬性會傳回包含衍生自樣式表 <xref:System.Xml.XmlWriterSettings> 項目之輸出資訊的 `xsl:output` 物件。 <xref:System.Xml.XmlWriterSettings> 物件是用來建立 <xref:System.Xml.XmlWriter> 物件，其正確的設定可以傳遞給 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。 下列 C# 程式碼說明這個行為：  
  
```  
// Create the XslTransform object and load the style sheet.  
XslCompiledTransform xslt = new XslCompiledTransform();  
xslt.Load(stylesheet);  
  
// Load the file to transform.  
XPathDocument doc = new XPathDocument(filename);  
  
// Create the writer.  
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);  
  
// Transform the file and send the output to the console.  
xslt.Transform(doc, writer);  
writer.Close();  
```  
  
### <a name="debug-option"></a>偵錯選項  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別可以產生偵錯資訊，此資訊可讓您使用 Microsoft Visual Studio 偵錯工具來偵錯樣式表。 如需詳細資訊，請參閱 <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>。  
  
## <a name="behavioral-differences"></a>行為的差異  
  
### <a name="transforming-to-an-xmlreader"></a>轉換成 XmlReader  
 <xref:System.Xml.Xsl.XslTransform> 類別有數個 Transform 多載，可將轉換結果當做 <xref:System.Xml.XmlReader> 物件傳回。 這些多載可用來將轉換結果載入記憶體中的表示法 (例如 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathDocument>)，而不會產生序列化和還原序列化結果 XML 樹狀結構的額外負荷。 下列 C# 程式碼示範如何將轉換結果載入 <xref:System.Xml.XmlDocument> 物件。  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別不支援轉換成 <xref:System.Xml.XmlReader> 物件。 但是，您可以採取類似的處理方式，透過 <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> 方法從 <xref:System.Xml.XmlWriter> 直接載入產生的 XML 樹狀結構。 下列 C# 程式碼將示範如何使用 <xref:System.Xml.Xsl.XslCompiledTransform> 完成相同的工作。  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>Discretionary 行為  
 ＜W3C XSL 轉換 (XSLT) 1.0 版建議事項＞中所包含的領域，可告訴實作提供者該採取哪些決策來處理哪種狀況。 這些領域視為 Discretionary 行為。 在幾個領域中，<xref:System.Xml.Xsl.XslCompiledTransform> 的行為與 <xref:System.Xml.Xsl.XslTransform> 類別有一些差異。 如需詳細資訊，請參閱[可復原的 XSLT 錯誤](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)。  
  
### <a name="extension-objects-and-script-functions"></a>擴充物件和指令碼函式  
 <xref:System.Xml.Xsl.XslCompiledTransform> 對於指令碼函式的使用引入兩項新的限制：  
  
-   只有公用方法才可以從 XPath 運算式呼叫。  
  
-   多載可根據引數的數目彼此區分。 如果有一個以上的多載具有相同的引數數目，將會引發例外狀況。  
  
 在 <xref:System.Xml.Xsl.XslCompiledTransform> 中，繫結 (方法名稱查閱) 至指令碼函式會在編譯時期發生，樣式表 (使用 XslTranform 並且以 <xref:System.Xml.Xsl.XslCompiledTransform> 載入) 可能會導致例外狀況。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 支援在 `msxsl:using` 項目內有 `msxsl:assembly` 和 `msxsl:script` 子項目。 `msxsl:using` 和 `msxsl:assembly` 項目是用來宣告要在指令碼區塊內使用的其他命名空間和組件。 如需詳細資訊，請參閱[使用 msxsl:script 的指令碼區塊](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 禁止具有多個多載的擴充物件有相同的引數數目。  
  
### <a name="msxml-functions"></a>MSXML 函式  
 其他 MSXML 函式的支援已加入到 <xref:System.Xml.Xsl.XslCompiledTransform> 類別中。 下列清單說明新的或改良的功能：  
  
-   msxsl:node-set：<xref:System.Xml.Xsl.XslTransform> 要求 [node-set Function](https://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) 函式的引數為 result tree fragment。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別並沒有這項需求。  
  
-   msxsl:version：在 <xref:System.Xml.Xsl.XslCompiledTransform> 中支援此函式。  
  
-   XPath 擴充函式：現在支援 [ms:string-compare Function](https://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee)、[ms:utc Function](https://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-uri Function](https://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7)、[ms:local-name Function](https://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5)、[ms:number Function](https://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954)、[ms:format-date Function](https://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5) 和 [ms:format-time Function](https://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) 函式。  
  
-   與結構描述相關的 XPath 擴充函式：<xref:System.Xml.Xsl.XslCompiledTransform> 原本就不支援這些函式。 不過，它們可以實作為擴充函式。  
  
## <a name="see-also"></a>另請參閱

- [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
