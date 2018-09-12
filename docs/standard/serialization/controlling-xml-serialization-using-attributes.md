---
title: 使用屬性控制 XML 序列化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET Framework], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
ms.openlocfilehash: 28c7ebe1de3adb92e531597027e4b8bb7a63294c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514497"
---
# <a name="controlling-xml-serialization-using-attributes"></a>使用屬性控制 XML 序列化

屬性可用來控制物件的 XML 序列化或從相同的類別集建立其他的 XML 資料流。 如需建立替代 XML 資料流的詳細資料，請參閱[如何：指定 XML 資料流的替代項目名稱](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)。

> [!NOTE]
> 如果產生的 XML 必須符合第 5 節的 World Wide Web Consortium (W3C) 文件[簡易物件存取通訊協定 (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)，使用屬性中所列[屬性，控制編碼 SOAP序列化](attributes-that-control-encoded-soap-serialization.md)。

根據預設，XML 項目名稱是由類別或成員名稱決定。 在名為 `Book` 的簡單類別中，名為 `ISBN` 的欄位將會產生 XML 項目標記 \<ISBN>，如下列範例所示。

```vb
Public Class Book
    Public ISBN As String
End Class
' When an instance of the Book class is serialized, it might
' produce this XML:
' <ISBN>1234567890</ISBN>.
```

```csharp
public class Book
{
    public string ISBN;
}
// When an instance of the Book class is serialized, it might
// produce this XML:
// <ISBN>1234567890</ISBN>.
```

若想指定項目一個新的名稱，可以變更此預設行為。 下列程式碼顯示一個屬性 (Attribute) 如何透過設定 <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A><xref:System.Xml.Serialization.XmlElementAttribute>的  屬性 (Property)，達成這個目標。

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。 如需控制 XML 序列化的屬性清單，請參閱[可控制 XML 序列化的屬性](attributes-that-control-xml-serialization.md)。

## <a name="controlling-array-serialization"></a>控制陣列序列化

<xref:System.Xml.Serialization.XmlArrayAttribute> 與 <xref:System.Xml.Serialization.XmlArrayItemAttribute> 屬性是針對陣列序列化控制而設計。 使用這些屬性，您可控制項目名稱、命名空間以及 XML 結構描述 (XSD) 資料型別 (如全球資訊網協會 [www.w3.org] 文件＜XML Schema Part 2: Datatypes＞中所定義)。 您也可以指定陣列能包含的類型。

<xref:System.Xml.Serialization.XmlArrayAttribute> 將決定當陣列序列化時，封入 XML 項目的屬性。 例如，依預設，序列化以下的陣列將產生名為 `Employees` 的 XML 項目。 `Employees` 項目將包含一系列根據陣列類型 `Employee`命名的項目。

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

序列化的執行個體可能類似於下列項目。

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

套用 <xref:System.Xml.Serialization.XmlArrayAttribute>，您可變更 XML 項目的名稱，如下所示。

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

產生的 XML 可能類似下列所示。

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

另一方面，<xref:System.Xml.Serialization.XmlArrayItemAttribute> 控制陣列包含的項目如何序列化。 請注意，屬性會套用至傳回陣列的欄位。

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

產生的 XML 可能類似下列所示。

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a>序列化衍生類別

<xref:System.Xml.Serialization.XmlArrayItemAttribute> 的另一用途，是允許衍生類別的序列化。 例如，另一個衍生自 `Manager` 名為 `Employee` 的類別，可加入前面的範例。 若您不套用 <xref:System.Xml.Serialization.XmlArrayItemAttribute>，由於無法識別衍生類別型別，程式碼將在執行階段失敗。 若要修正此狀況，請套用屬性兩次，每次都針對每個可接受的型別 (基底與衍生) 設定 <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> 屬性。

```vb
Public Class Group
    <XmlArrayItem(Type:=GetType(Employee)), _
    XmlArrayItem(Type:=GetType(Manager))> _
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
Public Class Manager
Inherits Employee
    Public Level As Integer
End Class
```

```csharp
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

序列化的執行個體可能類似於下列項目。

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    <Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a>序列化陣列成為項目序列

您也可以套用 <xref:System.Xml.Serialization.XmlElementAttribute> 至傳回陣列的欄位 (如下所示)，將陣列序列化成為 XML 項目的平面序列。

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

序列化的執行個體可能類似於下列項目。

```xml
<Group>
<Employees>
    <Name>Haley</Name>
</Employees>
<Employees>
    <Name>Noriko</Name>
</Employees>
<Employees>
    <Name>Marco</Name>
</Employees>
</Group>
```

另一種區別這兩種 XML 資料流的方法是使用 XML 結構描述定義工具，從編譯的程式碼中產生 XML 結構描述 (XSD) 文件檔案 (如需使用此工具的詳細資料，請參閱 [XML 結構描述定義工具和 XML 序列化](the-xml-schema-definition-tool-and-xml-serialization.md))。無屬性套用至欄位時，結構描述會以下列方式說明項目。

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

當 <xref:System.Xml.Serialization.XmlElementAttribute> 套用至欄位時，產生的結構描述說明項目如下。

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" /> 
```

## <a name="serializing-an-arraylist"></a>序列化 ArrayList

<xref:System.Collections.ArrayList> 類別可包含各種不同物件的集合。 因此您可如同使用陣列的方式使用 <xref:System.Collections.ArrayList>。 不過，若不想建立會傳回型別物件陣列的欄位，可建立傳回單一 <xref:System.Collections.ArrayList>的欄位。 不過，與陣列一樣，您必須將 <xref:System.Xml.Serialization.XmlSerializer> 包含的物件類型告知 <xref:System.Collections.ArrayList>。 若要達成這個目的，請指派多個 <xref:System.Xml.Serialization.XmlElementAttribute> 執行個體至欄位，如下面的範例所示。

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)), 
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a>使用 XmlRootAttribute 與 XmlTypeAttribute 控制類別的序列化

有兩種屬性可套用至類別 (只有一種類別)：<xref:System.Xml.Serialization.XmlRootAttribute> 與 <xref:System.Xml.Serialization.XmlTypeAttribute>。 這些屬性非常類似。 <xref:System.Xml.Serialization.XmlRootAttribute> 僅能套用至一類別：在序列化後此類別代表 XML 文件開啟與關閉的項目，換句話說就是根項目。 另一方面，<xref:System.Xml.Serialization.XmlTypeAttribute> 可套用至任何類別，包括根類別。

例如，在前述的範例中，`Group` 類別為根類別，它所有的公用欄位與屬性成為在 XML 文件中發現的 XML 項目。 因此，只能有一個根類別。 藉由套用 <xref:System.Xml.Serialization.XmlRootAttribute>，您可用 <xref:System.Xml.Serialization.XmlSerializer>控制產生的 XML 資料流。 例如，您可變更項目名稱與命名空間。

<xref:System.Xml.Serialization.XmlTypeAttribute> 允許您控制產生之 XML 的結構描述。 當您需要透過 XML Web 服務發怖此結構描述時，此能力就很重要。 下列範例會將 <xref:System.Xml.Serialization.XmlTypeAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute>套用至相同類別。

```vb
<XmlRoot("NewGroupName"), _
XmlType("NewTypeName")> _
Public Class Group
    Public Employees() As Employee
End Class
```

```csharp
[XmlRoot("NewGroupName")]
[XmlType("NewTypeName")]
public class Group {
    public Employee[] Employees;
}
```

如果此類別已編譯，且使用 XML 結構描述定義工具產生它的結構描述，您會發現下列的 XML 說明 `Group`。

```xml
<xs:element name="NewGroupName" type="NewTypeName">
```

相反地，若您要序列化類別的執行個體，在 XML 文件中只會發現 `NewGroupName`。

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a>避免以 XmlIgnoreAttribute 序列化

也有可能不需將公用屬性或欄位序列化的狀況。 例如，欄位或屬性可用來包含中繼資料。 在這樣的情況下，套用 <xref:System.Xml.Serialization.XmlIgnoreAttribute> 至欄位或屬性，且將略過 <xref:System.Xml.Serialization.XmlSerializer>。

## <a name="see-also"></a>另請參閱

- [可控制 XML 序列化的屬性](attributes-that-control-xml-serialization.md)  
- [可控制編碼 SOAP 序列化的屬性](attributes-that-control-encoded-soap-serialization.md)  
- [XML 序列化簡介](introducing-xml-serialization.md)  
- [XML 序列化範例](examples-of-xml-serialization.md)  
- [如何：指定 XML 資料流的替代元素名稱](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
- [如何：序列化物件](how-to-serialize-an-object.md)  
- [如何：還原序列化物件](how-to-deserialize-an-object.md)  
