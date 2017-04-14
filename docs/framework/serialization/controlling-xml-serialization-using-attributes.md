---
title: "使用屬性控制 XML 序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "陣列, 序列化"
  - "屬性 [.NET Framework], XML 序列化"
  - "類別, 序列化"
  - "衍生類別, 序列化"
  - "避免序列化"
  - "序列化, 屬性"
  - "序列化, 範例"
  - "XML 序列化, 屬性"
  - "XML 序列化, 範例"
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 使用屬性控制 XML 序列化
屬性可用來控制物件的 XML 序列化或從相同的類別集建立其他的 XML 資料流。如需關於建立其他 XML 資料流的詳細資訊，請參閱 [HOW TO：指定 XML 資料流的替代項目名稱](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)。  
  
> [!NOTE]
>  若產生的 XML 必須符合全球資訊網協會 \(www.w3.org\) 文件＜Simple Object Access Protocol \(SOAP\) 1.1＞的第 5 節，請使用列在[控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)的屬性。  
  
 根據預設，XML 項目名稱是由類別或成員名稱決定。名為 `Book` 的簡單類別中，名為 `ISBN` 的欄位將產生 XML 項目標記 \<ISBN\>，如以下範例所示。  
  
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
  
 若想指定項目一個新的名稱，可以變更此預設行為。下列程式碼顯示一個屬性 \(Attribute\) 如何透過設定 <xref:System.Xml.Serialization.XmlElementAttribute> 的 <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> 屬性 \(Property\)，達成這個目標。  
  
```vb  
Public Class TaxRates  
   < XmlElement(ElementName = "TaxRate")> _  
    Public ReturnTaxRate As Decimal  
End Class  
  
```  
  
```csharp  
public class TaxRates{  
    [XmlElement(ElementName = "TaxRate")]  
    public decimal ReturnTaxRate;  
}  
```  
  
 如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。如需控制 XML 序列化的屬性清單，請參閱[控制 XML 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)。  
  
## 控制陣列序列化  
 <xref:System.Xml.Serialization.XmlArrayAttribute> 與 <xref:System.Xml.Serialization.XmlArrayItemAttribute> 屬性是針對陣列序列化控制而設計。使用這些屬性，您可控制項目名稱、命名空間以及 XML 結構描述 \(XSD\) 資料型別 \(如全球資訊網協會 \[www.w3.org\] 文件＜XML Schema Part 2: Datatypes＞中所定義\)。您也可以指定陣列能包含的類型。  
  
 <xref:System.Xml.Serialization.XmlArrayAttribute> 將決定當陣列序列化時，封入 XML 項目的屬性。例如，依預設，序列化以下的陣列將產生名為 `Employees` 的 XML 項目。`Employees` 項目將包含一系列根據陣列類型 `Employee` 命名的項目。  
  
```vb  
Public Class Group  
    Public Employees() As Employee  
End Class  
Public Class Employee  
    Public Name As String  
End Class  
  
```  
  
```csharp  
public class Group{  
    public Employee[] Employees;  
}  
public class Employee{  
    public string Name;  
}  
```  
  
 序列化的執行個體可能類似於下列項目。  
  
```  
<Group>  
<Employees>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</Employees >  
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
public class Group{  
    [XmlArray("TeamMembers")]  
    public Employee[] Employees;  
}  
```  
  
 產生的 XML 可能類似下列所示。  
  
```  
<Group>  
<TeamMembers>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</TeamMembers>  
```  
  
 另一方面，<xref:System.Xml.Serialization.XmlArrayItemAttribute> 控制陣列包含的項目如何序列化。請注意，屬性會套用至傳回陣列的欄位。  
  
```vb  
Public Class Group  
    <XmlArrayItem("MemberName")> _  
    Public Employee() As Employees  
End Class  
  
```  
  
```csharp  
public class Group{  
    [XmlArrayItem("MemberName")]  
    public Employee[] Employees;  
}  
```  
  
 產生的 XML 可能類似下列所示。  
  
```  
<Group>  
<Employees>  
    <MemberName>Haley</MemberName>  
</Employees>  
</Group>  
```  
  
## 序列化衍生類別  
 <xref:System.Xml.Serialization.XmlArrayItemAttribute> 的另一用途，是允許衍生類別的序列化。例如，另一個衍生自 `Employee` 名為 `Manager` 的類別，可加入前面的範例。若您不套用 <xref:System.Xml.Serialization.XmlArrayItemAttribute>，由於無法識別衍生類別型別，程式碼將在執行階段失敗。若要修正此狀況，請套用屬性兩次，每次都針對每個可接受的型別 \(基底與衍生\) 設定 <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> 屬性。  
  
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
public class Group{  
    [XmlArrayItem(Type = typeof(Employee)),  
    XmlArrayItem(Type = typeof(Manager))]  
    public Employee[] Employees;  
}  
public class Employee{  
    public string Name;  
}  
public class Manager:Employee{  
    public int Level;  
}  
```  
  
 序列化的執行個體可能類似於下列項目。  
  
```  
<Group>  
<Employees>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
    <Employee xsi:type = "Manager">  
        <Name>Ann</Name>  
        <Level>3</Level>  
    <Employee>  
</Employees >  
</Group>  
```  
  
## 序列化陣列成為項目序列  
 您也可以套用 <xref:System.Xml.Serialization.XmlElementAttribute> 至傳回陣列的欄位 \(如下所示\)，將陣列序列化成為 XML 項目的平面序列。  
  
```vb  
Public Class Group  
    <XmlElement> _  
    Public Employees() As Employee  
End Class  
  
```  
  
```csharp  
public class Group{  
    [XmlElement]  
    public Employee[] Employees;  
}  
```  
  
 序列化的執行個體可能類似於下列項目。  
  
```  
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
  
 另一種區別這兩種 XML 資料流的方法是使用 XML 結構描述定義工具，從編譯的程式碼中產生 XML 結構描述 \(XSD\) 文件檔案 \(如需使用該工具的詳細資訊，請參閱 [XML 結構描述定義工具和 XML 序列化](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)\)。無屬性套用至欄位時，結構描述會以下列方式說明項目。  
  
```  
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />  
```  
  
 當 <xref:System.Xml.Serialization.XmlElementAttribute> 套用至欄位時，產生的結構描述說明項目如下。  
  
```  
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />   
```  
  
## 序列化 ArrayList  
 <xref:System.Collections.ArrayList> 類別可包含各種不同物件的集合。因此您可如同使用陣列的方式使用 <xref:System.Collections.ArrayList>。不過，若不想建立會傳回型別物件陣列的欄位，可建立傳回單一 <xref:System.Collections.ArrayList> 的欄位。不過，與陣列一樣，您必須將 <xref:System.Collections.ArrayList> 包含的物件類型告知 <xref:System.Xml.Serialization.XmlSerializer>。若要達成這個目的，請指派多個 <xref:System.Xml.Serialization.XmlElementAttribute> 執行個體至欄位，如下面的範例所示。  
  
```vb  
Public Class Group  
    <XmlElement(Type:=GetType(Employee)), _  
    XmlElement(Type:=GetType(Manager))> _  
    Public Info As ArrayList  
End Class  
  
```  
  
```csharp  
public class Group{  
    [XmlElement(Type = typeof(Employee)),   
    XmlElement(Type = typeof(Manager))]  
    public ArrayList Info;  
}  
```  
  
## 使用 XmlRootAttribute 與 XmlTypeAttribute 控制類別的序列化  
 有兩種屬性可套用至類別 \(只有一種類別\)：<xref:System.Xml.Serialization.XmlRootAttribute> 與 <xref:System.Xml.Serialization.XmlTypeAttribute>。這些屬性非常類似。<xref:System.Xml.Serialization.XmlRootAttribute> 僅能套用至一類別：在序列化後此類別代表 XML 文件開啟與關閉的項目，換句話說就是根項目。另一方面，<xref:System.Xml.Serialization.XmlTypeAttribute> 可套用至任何類別，包括根類別。  
  
 例如，在前述的範例中，`Group` 類別為根類別，它所有的公用欄位與屬性成為在 XML 文件中發現的 XML 項目。因此，只能有一個根類別。藉由套用 <xref:System.Xml.Serialization.XmlRootAttribute>，您可用 <xref:System.Xml.Serialization.XmlSerializer> 控制產生的 XML 資料流。例如，您可變更項目名稱與命名空間。  
  
 <xref:System.Xml.Serialization.XmlTypeAttribute> 允許您控制產生之 XML 的結構描述。當您需要透過 XML Web 服務發怖此結構描述時，此能力就很重要。下列範例會將 <xref:System.Xml.Serialization.XmlTypeAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 套用至相同類別。  
  
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
public class Group{  
    public Employee[] Employees;  
}  
```  
  
 如果此類別已編譯，且使用 XML 結構描述定義工具產生它的結構描述，您會發現下列的 XML 說明 `Group`。  
  
```  
<xs:element name="NewGroupName" type="NewTypeName">  
```  
  
 相反地，若您要序列化類別的執行個體，在 XML 文件中只會發現 `NewGroupName`。  
  
```  
<NewGroupName>  
    . . .  
</NewGroupName>  
```  
  
## 避免以 XmlIgnoreAttribute 序列化  
 也有可能不需將公用屬性或欄位序列化的狀況。例如，欄位或屬性可用來包含中繼資料。在這樣的情況下，套用 <xref:System.Xml.Serialization.XmlIgnoreAttribute> 至欄位或屬性，且將略過 <xref:System.Xml.Serialization.XmlSerializer>。  
  
## 請參閱  
 [控制 XML 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)   
 [控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)   
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [XML 序列化的範例](../../../docs/framework/serialization/examples-of-xml-serialization.md)   
 [HOW TO：指定 XML 資料流的替代項目名稱](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)