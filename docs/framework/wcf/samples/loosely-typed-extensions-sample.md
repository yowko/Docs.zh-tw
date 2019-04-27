---
title: 鬆散型別延伸範例
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 2f80c3379ba9d7e0649a36c5dd1bd552c1da68c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006573"
---
# <a name="loosely-typed-extensions-sample"></a>鬆散型別延伸範例
新聞訂閱物件模型對使用延伸資料 (即以新聞訂閱摘要 XML 表示法呈現，但是尚未經由像是 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 等類別明確公開的資訊) 提供大量支援。 這個範例說明使用延伸資料的基本技術。  
  
 基於示範用途，此範例會使用 <xref:System.ServiceModel.Syndication.SyndicationFeed> 類別。 不過在此範例中所示範的模式，可以與所有支援延伸資料的新聞訂閱類別一起使用：  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>範例 XML  
 對於參考，這個範例使用下列 XML 文件。  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 這份文件包含下列延伸資料片段：  
  
-   `myAttribute` 元素的 `<feed>` 屬性。  
  
-   `<simpleString>` 項目。  
  
-   `<DataContractExtension>` 項目。  
  
-   `<XmlSerializerExtension>` 項目。  
  
-   `<xElementExtension>` 項目。  
  
## <a name="writing-extension-data"></a>撰寫延伸資料  
 將項目新增至 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 集合便可以建立屬性延申，如下列範例程式碼所示。  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 將項目新增至 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 集合便可以建立項目延伸。 這些延伸可以是像是字串、.NET Framework 物件的 XML 序列化 (Serialization) 或手動撰寫的 XML 節點等基本值。  
  
 下列範例程式碼會建立名為 `simpleString` 的延伸項目。  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 此元素的 XML 命名空間是空的命名空間 ("")，其值為文字節點，其中包含字串"hello，world ！"。  
  
 建立由許多巢狀項目所組成之複雜項目延伸的其中一種方法，便是使用 .NET Framework API 進行序列化 (同時支援<xref:System.Runtime.Serialization.DataContractSerializer><xref:System.Xml.Serialization.XmlSerializer> 和)，如下列範例所示。  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 在這個範例中，`DataContractExtension` 和 `XmlSerializerExtension` 是針對搭配序列化程式所撰寫的自訂型別。  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> 類別也可以用來建立 <xref:System.Xml.XmlReader> 執行個體的項目延伸。 這樣便可以與像是 <xref:System.Xml.Linq.XElement> 的 XML 處理 API 輕鬆整合，如下列範例程式碼所示。  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>讀取延伸資料  
 在 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 集合中根據 <xref:System.Xml.XmlQualifiedName> 查閱屬性，便可取得該屬性延伸的值，如下列範例程式碼所示。  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 項目延伸是使用 `ReadElementExtensions<T>` 方法來存取。  
  
```  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 使用 `XmlReader` 方法，也可以取得位在個別項目延伸的 <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>。  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>另請參閱

- [強型別延伸模組](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [WCF 摘要整合](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
