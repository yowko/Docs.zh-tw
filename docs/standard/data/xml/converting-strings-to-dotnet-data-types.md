---
title: "將字串轉換成 .NET Framework 資料型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a>將字串轉換成 .NET Framework 資料型別
如果您想要將字串轉換為.NET Framework 資料型別，使用**XmlConvert**符合應用程式需求的方法。 如需所有使用中的轉換方法的清單**XmlConvert**類別，請參閱<xref:System.Xml.XmlConvert>。  
  
 傳回的字串**ToString**方法是傳入資料的字串版本。 此外，有幾種轉換使用的.NET Framework 類型**XmlConvert**類別，但它們不會使用中的方法**System.Convert**類別。 **XmlConvert**類別遵循的 XML 結構描述 (XSD) 資料型別規格，並具有的資料類型， **XmlConvert**可以對應至。  
  
 下列表格列出使用 XML 結構描述 (XSD) 資料型別對應所傳回的 .NET Framework 資料型別和字串型別。 這些.NET Framework 型別無法使用處理**System.Convert**。  
  
|.NET Framework 類型|傳回的字串|  
|-------------------------|---------------------|  
|Boolean|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|格式為 "yyyy-MM-ddTHH:mm:sszzzzzz" 及其子集。|  
|Timespan|格式為 PnYnMnTnHnMnS，即 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。|  
  
> [!NOTE]
>  如果任何.NET Framework 類型轉換表所列的字串，使用**ToString**方法，傳回的字串不是基底型別，而 XML 結構描述 (XSD) 字串型別。  
  
 **DateTime**和**Timespan**數值型別的差別在於**DateTime**表示時間的瞬間而**TimeSpan**表示時間間隔。 **DateTime**和**Timespan** XML 結構描述 (XSD) 資料型別規格中指定的格式。 例如:   
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **輸出**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 下列程式碼會將整數轉換成字串：  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **輸出**  
  
 `<Number>200</Number>`  
  
 不過，如果您想要轉換的字串**布林**，**單一**，或**Double**，就會傳回.NET Framework 型別不是使用時，傳回的類型相同**System.Convert**類別。  
  
## <a name="string-to-boolean"></a>字串轉成 Boolean  
 下表顯示當字串轉換成指定的輸入字串，請產生哪些型別**布林**使用**ToBoolean**方法。  
  
|有效的字串輸入參數|.NET Framework 輸出型別|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 例如，假設有以下的 XML：  
  
 **輸入**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 下列程式碼，同時可以理解和**bvalue**是**System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>字串轉成 Single  
 下表顯示當字串轉換成指定的輸入字串，請產生哪些型別**單一**使用**ToSingle**方法。  
  
|有效的字串輸入參數|.NET Framework 輸出型別|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>字串轉成 Double  
 下表顯示當字串轉換成指定的輸入字串，請產生哪些型別**單一**使用**ToDouble**方法。  
  
|有效的字串輸入參數|.NET Framework 輸出型別|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 下列程式碼寫入 `<Infinity>INF</Infinity>`：  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 資料型別轉換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [將.NET Framework 型別轉換為字串](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
