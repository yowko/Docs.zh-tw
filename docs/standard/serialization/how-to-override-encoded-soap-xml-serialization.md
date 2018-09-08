---
title: HOW TO：覆寫已編碼的 SOAP XML 序列化
ms.date: 03/30/2017
helpviewer_keywords:
- overriding XML serialization
- SOAP, overriding encoded XML serialization
ms.assetid: d0791df8-04e3-46b4-a6be-fe0ed09267e8
ms.openlocfilehash: 721a27b4bba239f0d22a24e0e159ef36b742d1b7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191224"
---
# <a name="how-to-override-encoded-soap-xml-serialization"></a>HOW TO：覆寫已編碼的 SOAP XML 序列化
[程式碼範例](#tskhowtooverrideencodedsoapxmlserializationanchor1)  
  
 將物件的 XML 序列化覆寫為 SOAP 訊息的程序，與覆寫標準 XML 序列化的程序類似。 如需覆寫標準 XML 序列化的資訊，請參閱[如何：指定 XML 資料流的替代項目名稱](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)。  
  
### <a name="to-override-serialization-of-objects-as-soap-messages"></a>將物件的序列化覆寫為 SOAP 訊息  
  
1.  建立 <xref:System.Xml.Serialization.SoapAttributeOverrides> 類別的執行個體。  
  
2.  為每個序列化的類別成員建立 `SoapAttributes`。  
  
3.  對序列化的成員適當地建立會影響 XML 序列化之一個或多個屬性的執行個體。 如需詳細資訊，請參閱＜控制編碼 SOAP 序列化的屬性＞。  
  
4.  將 `SoapAttributes` 的適當屬性 (property) 設定為在步驟 3 所建立的屬性 (attribute)。  
  
5.  將 `SoapAttributes` 加入 `SoapAttributeOverrides`。  
  
6.  使用 `XmlTypeMapping` 建立 `SoapAttributeOverrides`。 請使用 `SoapReflectionImporter.ImportTypeMapping` 方法。  
  
7.  使用 `XmlSerializer` 建立 `XmlTypeMapping`。  
  
8.  序列化或還原序列化物件。  
  
## <a name="example"></a>範例  
 下列程式碼範例以兩種方法序列化檔案：第一種是不覆寫 `XmlSerializer` 類別的行為，第二種則是覆寫此行為。 本範例包含具有數個成員的 `Group` 類別。 已將不同屬性 (例如 `SoapElementAttribute`) 套用至類別成員。 當類別以 `SerializeOriginal` 方法序列化後，屬性會控制 SOAP 訊息內容。 呼叫 `SerializeOverride` 方法時，會建立不同屬性 (Attribute) 並將 `XmlSerializer` 的屬性 (Property) 設定為那些屬性 (Attribute) 來覆寫 `SoapAttributes` 的行為 (如果適合的話)。  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Serialization;  
using System.Xml.Schema;  
  
public class Group  
{  
    [SoapAttribute (Namespace = "http://www.cpandl.com")]  
    public string GroupName;  
  
    [SoapAttribute(DataType = "base64Binary")]  
    public Byte [] GroupNumber;  
  
    [SoapAttribute(DataType = "date", AttributeName = "CreationDate")]  
    public DateTime Today;  
    [SoapElement(DataType = "nonNegativeInteger", ElementName = "PosInt")]  
    public string PostitiveInt;  
    // This is ignored when serialized unless it is overridden.  
    [SoapIgnore]   
    public bool IgnoreThis;  
  
    public GroupType Grouptype;  
  
    [SoapInclude(typeof(Car))]  
    public Vehicle myCar(string licNumber)  
    {  
        Vehicle v;  
        if(licNumber == "")  
            {  
                v = new Car();  
            v.licenseNumber = "!!!!!!";  
        }  
        else  
        {  
            v = new Car();  
            v.licenseNumber = licNumber;  
        }  
        return v;  
    }  
}  
  
public abstract class Vehicle  
{  
    public string licenseNumber;  
    public DateTime makeDate;  
}  
  
public class Car: Vehicle  
{  
}  
  
public enum GroupType  
{  
    // These enums can be overridden.  
    small,  
    large  
}  
  
public class Run  
{  
    public static void Main()  
    {  
        Run test = new Run();  
        test.SerializeOriginal("SoapOriginal.xml");  
        test.SerializeOverride("SoapOverrides.xml");  
        test.DeserializeOriginal("SoapOriginal.xml");  
        test.DeserializeOverride("SoapOverrides.xml");  
  
    }  
    public void SerializeOriginal(string filename)  
    {  
        // Creates an instance of the XmlSerializer class.  
        XmlTypeMapping myMapping =   
        (new SoapReflectionImporter().ImportTypeMapping(  
        typeof(Group)));  
        XmlSerializer mySerializer =    
        new XmlSerializer(myMapping);  
  
        // Writing the file requires a TextWriter.  
        TextWriter writer = new StreamWriter(filename);  
  
        // Creates an instance of the class that will be serialized.  
        Group myGroup = new Group();  
  
        // Sets the object properties.  
        myGroup.GroupName = ".NET";  
  
        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),  
        Convert.ToByte(50)};  
        myGroup.GroupNumber = hexByte;  
  
        DateTime myDate = new DateTime(2002,5,2);  
        myGroup.Today = myDate;  
  
        myGroup.PostitiveInt= "10000";  
        myGroup.IgnoreThis=true;  
        myGroup.Grouptype= GroupType.small;  
        Car thisCar =(Car)  myGroup.myCar("1234566");  
  
        // Prints the license number just to prove the car was created.  
        Console.WriteLine("License#: " + thisCar.licenseNumber + "\n");  
  
        // Serializes the class and closes the TextWriter.  
        mySerializer.Serialize(writer, myGroup);  
        writer.Close();  
    }  
  
    public void SerializeOverride(string filename)  
    {  
        // Creates an instance of the XmlSerializer class  
        // that overrides the serialization.  
        XmlSerializer overRideSerializer = CreateOverrideSerializer();  
  
        // Writing the file requires a TextWriter.  
        TextWriter writer = new StreamWriter(filename);  
  
        // Creates an instance of the class that will be serialized.  
        Group myGroup = new Group();  
  
        // Sets the object properties.  
        myGroup.GroupName = ".NET";  
  
        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),  
        Convert.ToByte(50)};  
        myGroup.GroupNumber = hexByte;  
  
        DateTime myDate = new DateTime(2002,5,2);  
        myGroup.Today = myDate;  
  
        myGroup.PostitiveInt= "10000";  
        myGroup.IgnoreThis=true;  
        myGroup.Grouptype= GroupType.small;  
        Car thisCar =(Car)  myGroup.myCar("1234566");  
  
        // Serializes the class and closes the TextWriter.  
        overRideSerializer.Serialize(writer, myGroup);  
         writer.Close();  
    }  
  
    public void DeserializeOriginal(string filename)  
    {  
        // Creates an instance of the XmlSerializer class.  
        XmlTypeMapping myMapping =   
        (new SoapReflectionImporter().ImportTypeMapping(  
        typeof(Group)));  
        XmlSerializer mySerializer =    
        new XmlSerializer(myMapping);  
  
        TextReader reader = new StreamReader(filename);  
  
        // Deserializes and casts the object.  
        Group myGroup;   
        myGroup = (Group) mySerializer.Deserialize(reader);  
  
        Console.WriteLine(myGroup.GroupName);  
        Console.WriteLine(myGroup.GroupNumber[0]);  
        Console.WriteLine(myGroup.GroupNumber[1]);  
        Console.WriteLine(myGroup.Today);  
        Console.WriteLine(myGroup.PostitiveInt);  
        Console.WriteLine(myGroup.IgnoreThis);  
        Console.WriteLine();  
    }  
  
    public void DeserializeOverride(string filename)  
    {  
        // Creates an instance of the XmlSerializer class.  
        XmlSerializer overRideSerializer = CreateOverrideSerializer();  
        // Reading the file requires a TextReader.  
        TextReader reader = new StreamReader(filename);  
  
        // Deserializes and casts the object.  
        Group myGroup;   
        myGroup = (Group) overRideSerializer.Deserialize(reader);  
  
        Console.WriteLine(myGroup.GroupName);  
        Console.WriteLine(myGroup.GroupNumber[0]);  
        Console.WriteLine(myGroup.GroupNumber[1]);  
        Console.WriteLine(myGroup.Today);  
        Console.WriteLine(myGroup.PostitiveInt);  
        Console.WriteLine(myGroup.IgnoreThis);  
    }  
  
    private XmlSerializer CreateOverrideSerializer()  
    {  
        SoapAttributeOverrides mySoapAttributeOverrides =   
        new SoapAttributeOverrides();  
        SoapAttributes soapAtts = new SoapAttributes();  
  
        SoapElementAttribute mySoapElement = new SoapElementAttribute();  
        mySoapElement.ElementName = "xxxx";  
        soapAtts.SoapElement = mySoapElement;  
        mySoapAttributeOverrides.Add(typeof(Group), "PostitiveInt",   
        soapAtts);  
  
        // Overrides the IgnoreThis property.  
        SoapIgnoreAttribute myIgnore = new SoapIgnoreAttribute();  
        soapAtts = new SoapAttributes();  
        soapAtts.SoapIgnore = false;        
        mySoapAttributeOverrides.Add(typeof(Group), "IgnoreThis",   
        soapAtts);  
  
        // Overrides the GroupType enumeration.  
        soapAtts = new SoapAttributes();  
        SoapEnumAttribute xSoapEnum = new SoapEnumAttribute();  
        xSoapEnum.Name = "Over1000";  
        soapAtts.SoapEnum = xSoapEnum;  
  
        // Adds the SoapAttributes to the   
        // mySoapAttributeOverridesrides.  
        mySoapAttributeOverrides.Add(typeof(GroupType), "large",   
        soapAtts);  
  
        // Creates a second enumeration and adds it.  
        soapAtts = new SoapAttributes();  
        xSoapEnum = new SoapEnumAttribute();  
        xSoapEnum.Name = "ZeroTo1000";  
        soapAtts.SoapEnum = xSoapEnum;  
        mySoapAttributeOverrides.Add(typeof(GroupType), "small",   
        soapAtts);  
  
        // Overrides the Group type.  
        soapAtts = new SoapAttributes();  
        SoapTypeAttribute soapType = new SoapTypeAttribute();  
        soapType.TypeName = "Team";  
        soapAtts.SoapType = soapType;  
        mySoapAttributeOverrides.Add(typeof(Group),soapAtts);  
  
        // Creates an XmlTypeMapping that is used to create an instance   
        // of the XmlSerializer class. Then returns the XmlSerializer.  
        XmlTypeMapping myMapping = (new SoapReflectionImporter(  
        mySoapAttributeOverrides)).ImportTypeMapping(typeof(Group));  
  
        XmlSerializer ser = new XmlSerializer(myMapping);  
        return ser;  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [可控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
- [以 XML Web 服務進行 XML 序列化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
- [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [如何：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
