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
ms.openlocfilehash: d97798dd44e9661e82a303023e041f5af2f43711
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930905"
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="e4236-102">使用屬性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="e4236-102">Controlling XML Serialization Using Attributes</span></span>

<span data-ttu-id="e4236-103">屬性可用來控制物件的 XML 序列化或從相同的類別集建立其他的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="e4236-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="e4236-104">如需建立替代 XML 資料流的詳細資料，請參閱[如何：指定 XML 資料流的替代項目名稱](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="e4236-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e4236-105">如果產生的 XML 必須符合第 5 節的 World Wide Web Consortium (W3C) 文件[簡易物件存取通訊協定 (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)，使用屬性中所列[屬性，控制編碼 SOAP序列化](attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="e4236-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="e4236-106">根據預設，XML 項目名稱是由類別或成員名稱決定。</span><span class="sxs-lookup"><span data-stu-id="e4236-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="e4236-107">在名為 `Book` 的簡單類別中，名為 `ISBN` 的欄位將會產生 XML 項目標記 \<ISBN>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e4236-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

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

<span data-ttu-id="e4236-108">若想指定項目一個新的名稱，可以變更此預設行為。</span><span class="sxs-lookup"><span data-stu-id="e4236-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="e4236-109">下列程式碼顯示一個屬性 (Attribute) 如何透過設定 <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A><xref:System.Xml.Serialization.XmlElementAttribute>的  屬性 (Property)，達成這個目標。</span><span class="sxs-lookup"><span data-stu-id="e4236-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

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

<span data-ttu-id="e4236-110">如需屬性的詳細資訊，請參閱[屬性](../../../docs/standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e4236-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="e4236-111">如需控制 XML 序列化的屬性清單，請參閱[可控制 XML 序列化的屬性](attributes-that-control-xml-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="e4236-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="e4236-112">控制陣列序列化</span><span class="sxs-lookup"><span data-stu-id="e4236-112">Controlling Array Serialization</span></span>

<span data-ttu-id="e4236-113"><xref:System.Xml.Serialization.XmlArrayAttribute> 與 <xref:System.Xml.Serialization.XmlArrayItemAttribute> 屬性是針對陣列序列化控制而設計。</span><span class="sxs-lookup"><span data-stu-id="e4236-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="e4236-114">使用這些屬性，您可控制項目名稱、命名空間以及 XML 結構描述 (XSD) 資料型別 (如全球資訊網協會 [www.w3.org] 文件＜XML Schema Part 2: Datatypes＞中所定義)。</span><span class="sxs-lookup"><span data-stu-id="e4236-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="e4236-115">您也可以指定陣列能包含的類型。</span><span class="sxs-lookup"><span data-stu-id="e4236-115">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="e4236-116"><xref:System.Xml.Serialization.XmlArrayAttribute> 將決定當陣列序列化時，封入 XML 項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="e4236-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="e4236-117">例如，依預設，序列化以下的陣列將產生名為 `Employees` 的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="e4236-118">`Employees` 項目將包含一系列根據陣列類型 `Employee`命名的項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

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

<span data-ttu-id="e4236-119">序列化的執行個體可能類似於下列項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-119">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="e4236-120">套用 <xref:System.Xml.Serialization.XmlArrayAttribute>，您可變更 XML 項目的名稱，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e4236-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

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

<span data-ttu-id="e4236-121">產生的 XML 可能類似下列所示。</span><span class="sxs-lookup"><span data-stu-id="e4236-121">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="e4236-122">另一方面，<xref:System.Xml.Serialization.XmlArrayItemAttribute> 控制陣列包含的項目如何序列化。</span><span class="sxs-lookup"><span data-stu-id="e4236-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="e4236-123">請注意，屬性會套用至傳回陣列的欄位。</span><span class="sxs-lookup"><span data-stu-id="e4236-123">Note that the attribute is applied to the field returning the array.</span></span>

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

<span data-ttu-id="e4236-124">產生的 XML 可能類似下列所示。</span><span class="sxs-lookup"><span data-stu-id="e4236-124">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="e4236-125">序列化衍生類別</span><span class="sxs-lookup"><span data-stu-id="e4236-125">Serializing Derived Classes</span></span>

<span data-ttu-id="e4236-126"><xref:System.Xml.Serialization.XmlArrayItemAttribute> 的另一用途，是允許衍生類別的序列化。</span><span class="sxs-lookup"><span data-stu-id="e4236-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="e4236-127">例如，另一個衍生自 `Manager` 名為 `Employee` 的類別，可加入前面的範例。</span><span class="sxs-lookup"><span data-stu-id="e4236-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="e4236-128">若您不套用 <xref:System.Xml.Serialization.XmlArrayItemAttribute>，由於無法識別衍生類別型別，程式碼將在執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="e4236-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="e4236-129">若要修正此狀況，請套用屬性兩次，每次都針對每個可接受的型別 (基底與衍生) 設定 <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e4236-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

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

<span data-ttu-id="e4236-130">序列化的執行個體可能類似於下列項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-130">A serialized instance might resemble the following.</span></span>

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

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="e4236-131">序列化陣列成為項目序列</span><span class="sxs-lookup"><span data-stu-id="e4236-131">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="e4236-132">您也可以套用 <xref:System.Xml.Serialization.XmlElementAttribute> 至傳回陣列的欄位 (如下所示)，將陣列序列化成為 XML 項目的平面序列。</span><span class="sxs-lookup"><span data-stu-id="e4236-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

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

<span data-ttu-id="e4236-133">序列化的執行個體可能類似於下列項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-133">A serialized instance might resemble the following.</span></span>

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

<span data-ttu-id="e4236-134">另一種區別這兩種 XML 資料流的方法是使用 XML 結構描述定義工具，從編譯的程式碼中產生 XML 結構描述 (XSD) 文件檔案</span><span class="sxs-lookup"><span data-stu-id="e4236-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="e4236-135">(如需使用此工具的詳細資料，請參閱 [XML 結構描述定義工具和 XML 序列化](the-xml-schema-definition-tool-and-xml-serialization.md))。無屬性套用至欄位時，結構描述會以下列方式說明項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="e4236-136">當 <xref:System.Xml.Serialization.XmlElementAttribute> 套用至欄位時，產生的結構描述說明項目如下。</span><span class="sxs-lookup"><span data-stu-id="e4236-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" /> 
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="e4236-137">序列化 ArrayList</span><span class="sxs-lookup"><span data-stu-id="e4236-137">Serializing an ArrayList</span></span>

<span data-ttu-id="e4236-138"><xref:System.Collections.ArrayList> 類別可包含各種不同物件的集合。</span><span class="sxs-lookup"><span data-stu-id="e4236-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="e4236-139">因此您可如同使用陣列的方式使用 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="e4236-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="e4236-140">不過，若不想建立會傳回型別物件陣列的欄位，可建立傳回單一 <xref:System.Collections.ArrayList>的欄位。</span><span class="sxs-lookup"><span data-stu-id="e4236-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="e4236-141">不過，與陣列一樣，您必須將 <xref:System.Xml.Serialization.XmlSerializer> 包含的物件類型告知 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="e4236-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="e4236-142">若要達成這個目的，請指派多個 <xref:System.Xml.Serialization.XmlElementAttribute> 執行個體至欄位，如下面的範例所示。</span><span class="sxs-lookup"><span data-stu-id="e4236-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

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

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="e4236-143">使用 XmlRootAttribute 與 XmlTypeAttribute 控制類別的序列化</span><span class="sxs-lookup"><span data-stu-id="e4236-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="e4236-144">有兩種屬性可套用至類別 (只有一種類別)：<xref:System.Xml.Serialization.XmlRootAttribute> 與 <xref:System.Xml.Serialization.XmlTypeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e4236-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="e4236-145">這些屬性非常類似。</span><span class="sxs-lookup"><span data-stu-id="e4236-145">These attributes are very similar.</span></span> <span data-ttu-id="e4236-146"><xref:System.Xml.Serialization.XmlRootAttribute> 僅能套用至一類別：在序列化後此類別代表 XML 文件開啟與關閉的項目，換句話說就是根項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="e4236-147">另一方面，<xref:System.Xml.Serialization.XmlTypeAttribute> 可套用至任何類別，包括根類別。</span><span class="sxs-lookup"><span data-stu-id="e4236-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="e4236-148">例如，在前述的範例中，`Group` 類別為根類別，它所有的公用欄位與屬性成為在 XML 文件中發現的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="e4236-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="e4236-149">因此，只能有一個根類別。</span><span class="sxs-lookup"><span data-stu-id="e4236-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="e4236-150">藉由套用 <xref:System.Xml.Serialization.XmlRootAttribute>，您可用 <xref:System.Xml.Serialization.XmlSerializer>控制產生的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="e4236-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="e4236-151">例如，您可變更項目名稱與命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4236-151">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="e4236-152"><xref:System.Xml.Serialization.XmlTypeAttribute> 允許您控制產生之 XML 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e4236-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="e4236-153">當您需要透過 XML Web 服務發怖此結構描述時，此能力就很重要。</span><span class="sxs-lookup"><span data-stu-id="e4236-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="e4236-154">下列範例會將 <xref:System.Xml.Serialization.XmlTypeAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute>套用至相同類別。</span><span class="sxs-lookup"><span data-stu-id="e4236-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

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

<span data-ttu-id="e4236-155">如果此類別已編譯，且使用 XML 結構描述定義工具產生它的結構描述，您會發現下列的 XML 說明 `Group`。</span><span class="sxs-lookup"><span data-stu-id="e4236-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName">
```

<span data-ttu-id="e4236-156">相反地，若您要序列化類別的執行個體，在 XML 文件中只會發現 `NewGroupName`。</span><span class="sxs-lookup"><span data-stu-id="e4236-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="e4236-157">避免以 XmlIgnoreAttribute 序列化</span><span class="sxs-lookup"><span data-stu-id="e4236-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="e4236-158">也有可能不需將公用屬性或欄位序列化的狀況。</span><span class="sxs-lookup"><span data-stu-id="e4236-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="e4236-159">例如，欄位或屬性可用來包含中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e4236-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="e4236-160">在這樣的情況下，套用 <xref:System.Xml.Serialization.XmlIgnoreAttribute> 至欄位或屬性，且將略過 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="e4236-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4236-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4236-161">See Also</span></span>

[<span data-ttu-id="e4236-162">可控制 XML 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="e4236-162">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)  
[<span data-ttu-id="e4236-163">可控制編碼 SOAP 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="e4236-163">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)  
[<span data-ttu-id="e4236-164">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="e4236-164">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)  
[<span data-ttu-id="e4236-165">XML 序列化範例</span><span class="sxs-lookup"><span data-stu-id="e4236-165">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)  
[<span data-ttu-id="e4236-166">如何：指定 XML 資料流的替代元素名稱</span><span class="sxs-lookup"><span data-stu-id="e4236-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
[<span data-ttu-id="e4236-167">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="e4236-167">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
[<span data-ttu-id="e4236-168">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="e4236-168">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)  