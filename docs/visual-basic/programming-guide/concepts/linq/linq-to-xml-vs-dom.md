---
title: LINQ to XML 比較DOM (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 282df577808342a52a70f419b2a7559752103a0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051490"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML 比較DOM (Visual Basic)
本節描述 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 和目前主流的 XML 程式設計 API (也就是 W3C 文件物件模型 (DOM)) 之間的一些主要差異。  
  
## <a name="new-ways-to-construct-xml-trees"></a>建構 XML 樹狀的新方式  
 在 W3C DOM 中，您可以從下往上建置 XML 樹狀；也就是說，您可以建立文件、建立項目，然後將項目加入到文件中。  
  
 例如，以下是使用 Microsoft 的 DOM 實作 <xref:System.Xml.XmlDocument> 建立 XML 樹狀的典型方式：  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 這個編碼樣式在視覺上不會提供太多 XML 樹狀的相關資訊。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 支援使用這個方法來建構 XML 樹狀結構，但是也支援採用「功能建構」的替代方法。 在 Visual Basic 中，功能結構會使用 XML 常值，來建置 XML 樹狀結構。  
  
 此處說明您如何使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 功能建構，來建構相同的 XML 樹狀結構：  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 請注意，將要建構 XML 樹狀結構的程式碼縮排可顯示基礎 XML 的結構。  
  
 如需詳細資訊，請參閱 <<c0> [ 建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)。  
  
## <a name="working-directly-with-xml-elements"></a>直接使用 XML 項目  
 當您使用 XML 進行程式設計時，您的主要焦點通常是 XML 項目，也可能是屬性。 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，您可以直接使用 XML 項目和屬性。 例如，您可以：  
  
- 完全不使用文件物件來建立 XML 項目。 當您必須使用 XML 樹狀結構的片段時，這可以簡化程式設計的方式。  
  
- 從 XML 檔案直接載入 `T:System.Xml.Linq.XElement` 物件。  
  
- 將 `T:System.Xml.Linq.XElement` 物件序列化為檔案或資料流。  
  
 將這個 XML 項目或屬性與 W3C DOM 相比較，後者中的 XML 文件會當做 XML 樹狀結構的邏輯容器使用。 在 DOM 中，XML 節點 (包括項目和屬性) 必須在 XML 文件的內容中建立。 此處為要在 DOM 中建立名稱項目之節點的片段：  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 如果您要跨多個文件使用同一個項目，您必須匯入跨這些文件的節點。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]可避免這層複雜度。  
  
 使用 LINQ to XML 時，您僅能在想要於文件根層級上加入註解或處理指示時，才能使用 <xref:System.Xml.Linq.XDocument> 類別。  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>簡化的名稱和命名空間處理方式  
 名稱、命名空間和命名空間前置詞的處理通常是 XML 程式設計的複雜部分。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 不必處理命名空間前置詞，可簡化名稱和命名空間。 您也可以控制命名空間前置詞。 但是，如果您決定不明確控制命名空間前置詞，則在序列化期間，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會指派命名空間前置詞 (如有必要)，或使用預設的命名空間進行序列化 (如果非必要的話)。 如果使用預設的命名空間，在產生的文件中將不會有任何命名空間前置詞。 如需詳細資訊，請參閱 <<c0> [ 處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 另一個 DOM 問題是，DOM 不會讓您變更節點的名稱， 而是必須建立新的節點，並將所有子節點複製到該節點中，因此會失去原始的節點識別。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會讓您在節點上設定 <xref:System.Xml.Linq.XName> 屬性，藉以避免這個問題。  
  
## <a name="static-method-support-for-loading-xml"></a>載入 XML 的靜態方法支援  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可讓您使用靜態方法 (而非執行個體方法) 來載入 XML。 這會簡化載入和剖析的程序。 如需詳細資訊，請參閱[如何：載入 XML 檔案 (Visual Basic) 中](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)。  
  
## <a name="removal-of-support-for-dtd-constructs"></a>移除 DTD 建構函式的支援  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會移除實體和實體參考的支援，進一步簡化 XML 程式設計。 實體的管理很複雜，而且不常使用。 移除這些支援會增進效能並簡化程式設計介面。 填入 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 樹狀結構時，系統會展開所有 DTD 實體。  
  
## <a name="support-for-fragments"></a>支援片段  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 不提供 `XmlDocumentFragment` 類別的對等類別。 在許多情況下，`XmlDocumentFragment` 概念可藉由查詢結果來處理，該查詢的類型為 <xref:System.Xml.Linq.XNode> 的 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Xml.Linq.XElement> 的 <xref:System.Collections.Generic.IEnumerable%601>。  
  
## <a name="support-for-xpathnavigator"></a>支援 XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 透過 <xref:System.Xml.XPath?displayProperty=nameWithType> 命名空間中的擴充方法，提供 <xref:System.Xml.XPath.XPathNavigator> 的支援。 如需詳細資訊，請參閱<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。  
  
## <a name="support-for-white-space-and-indentation"></a>支援空白字元與縮排  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 處理空白字元時，比處理 DOM 更為容易。  
  
 常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。 當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。 這是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的預設行為。  
  
 其他常見案例為讀取與修改已經過刻意縮排的 XML。 您可能不想用任何方式變更這個縮排。 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，您就可以達到這個效果。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會將空白字元儲存為 <xref:System.Xml.Linq.XText> 節點，而不是像 DOM 儲存為序列化的 <xref:System.Xml.XmlNodeType.Whitespace> 節點類型。  
  
## <a name="support-for-annotations"></a>支援附註  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 項目支援一組可延伸的附註。 這在追蹤項目的其他資訊 (例如，結構描述資訊)、項目是否繫結至 UI 的相關資訊，或任何種類的應用程式專屬資訊時，相當實用。 如需詳細資訊，請參閱 [LINQ to XML 註釋](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md)。  
  
## <a name="support-for-schema-information"></a>支援結構描述資訊  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 透過 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的擴充方法，提供 XSD 驗證支援。 您可以驗證 XML 樹狀是以 XSD 編譯。 您可以利用 Post-Schema-Validation Infoset (PSVI) 填入 XML 樹狀。 如需詳細資訊，請參閱[如何：使用 XSD 進行驗證](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)和 <xref:System.Xml.Schema.Extensions>。  
  
## <a name="see-also"></a>另請參閱

- [使用者入門 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
