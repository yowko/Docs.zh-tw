---
title: 管理 XML 文件中的命名空間
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83ea398f18ab02840ea811c74a6053dba11a3baa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490883"
---
# <a name="managing-namespaces-in-an-xml-document"></a>管理 XML 文件中的命名空間
XML 命名空間會將 XML 文件中的項目與屬性名稱連結到自訂和預定的 URI。 若要建立這些關聯，請為命名空間 URI 定義前置詞，並使用這些前置詞來限定 XML 資料中的元素與屬性名稱。 命名空間可用來避免元素和屬性名稱發生衝突，並讓相同名稱的元素和屬性以不同方式處理和驗證。  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>宣告命名空間  
 若要在元素上宣告命名空間，請使用 `xmlns:` 屬性：  
  
 `xmlns:<name>=<"uri">`  
  
 其中 `<name>` 是命名空間前置詞，而 `<"uri">` 則是識別命名空間的 URI。 在宣告前置詞之後，您可以用它來限定 XML 文件中的元素和屬性，並將其與命名空間 URI 產生關聯。 因為命名空間前置詞會用於整份文件，所以其長度應該短一點。  
  
 這個範例會定義兩個 `BOOK` 元素。 第一個元素由前置詞 `mybook` 所限定，而第二個元素則由前置詞 `bb` 所限定。 每個前置詞都與不同的命名空間 URI 相關：  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 若要表示某元素是特定命名空間的一部分，請將命名空間前置詞加到其中。 例如，如果 `Author` 元素屬於 `mybook` 命名空間，便會將它宣告為 `<mybook:Author>`。  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>宣告範圍  
 命名空間的有效範圍，是從宣告點至宣告該命名空間之元素的結尾。 在此範例中，於 `BOOK` 元素中定義的命名空間並不適用於 `BOOK` 元素以外的元素，如 `Publisher` 元素：  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 雖然命名空間必須先行宣告才能使用，但它不必出現在 XML 文件的最前面。  
  
 當您在 XML 文件中使用多個命名空間時，您可以定義一個命名空間當做預設命名空間，以便建立更易讀取的文件。 預設命名空間會在根元素中宣告，並且套用到文件中所有非限定的元素。 預設命名空間僅適用於元素，不適用於屬性。  
  
 若要使用預設命名空間，請在元素的宣告中省略前置詞和冒號：  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>管理命名空間  
 <xref:System.Xml.XmlNamespaceManager> 類別會保存命名空間 URI 和其前置詞的集合，並讓您從這個集合查詢、加入及移除命名空間。 某些內容中需要使用這個類別，才能改善 XML 處理效能。 例如，<xref:System.Xml.Xsl.XsltContext> 類別會使用 <xref:System.Xml.XmlNamespaceManager>，以提供 XPath 支援。  
  
 命名空間管理員不會在命名空間上執行任何驗證，而是會假設前置詞和命名空間已經過驗證並且符合 [W3C 命名空間](https://www.w3.org/TR/REC-xml-names/)規格。  
  
> [!NOTE]
> [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) 和 [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) 中的 LINQ TO XML 不會使用 <xref:System.Xml.XmlNamespaceManager> 管理命名空間。 如需在使用 LINQ to XML 時管理命名空間的資訊，請參閱 LINQ 文件中的[處理 XML 命名空間 (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) 和[處理 XML 命名空間 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 以下是您可以使用 <xref:System.Xml.XmlNamespaceManager> 類別執行的一些管理和查詢工作。 如需詳細資訊和範例，請追蹤每個方法或屬性的參考頁面連結。  
  
|以|使用|  
|--------|---------|  
|加入命名空間|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> 方法|  
|移除命名空間|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> 方法|  
|尋找預設命名空間的 URI|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> 屬性|  
|尋找命名空間前置詞的 URI|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> 方法|  
|尋找命名空間 URI 的前置詞|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> 方法|  
|取得目前節點中的命名空間清單|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> 方法|  
|設定命名空間的範圍|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> 和 <xref:System.Xml.XmlNamespaceManager.PopScope%2A> 方法|  
|檢查前置詞是否定義於目前範圍中|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> 方法|  
|取得用來查詢前置詞與 URI 的名稱資料表|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> 屬性|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlNamespaceManager>
- [XML 文件和資料](../../../../docs/standard/data/xml/index.md)
