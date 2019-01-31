---
title: XPath 命名空間巡覽
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 373d1e4e5089b23ecaeffd10fd167b701b75760c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702895"
---
# <a name="xpath-namespace-navigation"></a>XPath 命名空間巡覽
若要使用 XPath 查詢搭配 XML 文件，您必須正確定址 XML 命名空間以及命名空間所包含的項目。 命名空間會避免在多個內容中使用名稱時可能發生的模稜兩可。例如，`ID` 名稱可能會參考多個與不同 XML 文件項目相關聯的識別碼。 命名空間語法會指定 URI、名稱和前置詞，以便區別 XML 文件的項目。  
  
 本主題中的範例將示範如何在透過 <xref:System.Xml.XPath.XPathNavigator> 巡覽 XML 文件時使用前置詞。 如需命名空間和語法的詳細資訊，請參閱[了解 XML 命名空間](https://msdn.microsoft.com/library/aa468565.aspx) (英文)。  
  
## <a name="namespace-declarations"></a>命名空間宣告  
 使用 <xref:System.Xml.XPath.XPathNavigator> 的執行個體時，命名空間宣告會讓 XML 文件的項目成為可區別和可定址的項目。 命名空間前置詞會提供簡短語法來定址命名空間。  
  
 前置詞會依照下列格式定義：`<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.`在這個語法中，前置詞 "`e`" 是標準命名空間 URI 的縮寫。 您可以使用 `Body` 語法，將 `Envelope` 項目識別為 `e:Body` 命名空間的成員。  
  
 下列 XML 文件將當做下一節巡覽範例中的 `response.xml` 參考。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>依照命名空間前置詞巡覽  
 本節中的程式碼會使用 <xref:System.Xml.XPath.XPathNavigator> 和 <xref:System.Xml.XmlNamespaceManager> 物件，從上一節的 XML 文件中選取 `Search` 項目。 `xpath` 查詢會在路徑中包含每個項目的命名空間前置詞。 指定包含每個項目之命名空間的精確識別可確保 `Search` 方法正確巡覽至 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 項目。  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 完整限定命名空間和名稱的精確度不僅是為了方便而已。 如果針對上述範例中的文件定義和程式碼進行一項小實驗，就可確認沒有完整限定項目名稱的巡覽將擲回例外狀況。 例如，如果項目定義：`<Search xmlns="http://schemas.microsoft.com/v1/Search">` 和查詢字串：`xpath = "/s:Envelope/s:Body/Search";` 沒有 `Search` 項目的命名空間前置詞，就會傳回 `null` 而非 `Search` 項目。  
  
## <a name="see-also"></a>另請參閱

- [使用 XPathNavigator 存取 XML 資料](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [使用 XPathNavigator 選取、評估及比對 XML 資料](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
