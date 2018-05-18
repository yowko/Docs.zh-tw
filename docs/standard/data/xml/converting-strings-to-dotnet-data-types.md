---
title: 將字串轉換成 .NET Framework 資料型別
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5954a580ca9b7f00f6339f70d0df9d20ba96715e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="converting-strings-to-net-framework-data-types"></a>將字串轉換成 .NET Framework 資料型別
若要將一個字串轉換成 .NET Framework 資料型別，請使用符合應用程式需求的 **XmlConvert** 方法。 如需所有可用於 **XmlConvert** 類別的轉換方法清單，請參閱 <xref:System.Xml.XmlConvert>。  
  
 **ToString** 方法所傳回的字串是所傳入之資料的字串版本。 此外，還有幾個 .NET Framework 型別是用 **XmlConvert** 類別來轉換，而不是使用 **System.Convert** 類別中的方法進行轉換。 **XmlConvert** 類別符合 XML 結構描述 (XSD) 資料型別規格，且擁有一個 **XmlConvert** 可對應的資料型別。  
  
 下列表格列出使用 XML 結構描述 (XSD) 資料型別對應所傳回的 .NET Framework 資料型別和字串型別。 這些 .NET Framework 型別無法以 **System.Convert** 來處理。  
  
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
>  若使用 **ToString** 方法將上表所列的任何 .NET Framework 型別轉換成字串，則傳回的字串將會是 XML 結構描述 (XSD) 字串型別，而不是基底型別。  
  
 **DateTime** 和 **Timespan** 數值型別的差別在於，**DateTime** 代表某一個時間，而 **TimeSpan** 代表時間間隔。 **DateTime** 和 **Timespan** 格式已指定於 XML 結構描述 (XSD) 資料型別規格中。 例如:   
  
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
  
 不過，如果您將字串轉換成 **Boolean**、**Single** 或 **Double**，則傳回的 .NET Framework 型別就會不同於使用 **System.Convert** 類別時所傳回的型別。  
  
## <a name="string-to-boolean"></a>字串轉成 Boolean  
 下列表格說明使用 **ToBoolean** 方法將字串轉換成 **Boolean** 時，給定的輸入字串會產生哪種型別。  
  
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
  
 這兩者都可由下列程式碼辨識，其中 **bvalue** 為 **System.Boolean.True**：  
  
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
 下列表格說明使用 **ToSingle** 方法將字串轉換成 **Single**，給定的輸入字串會產生哪些型別。  
  
|有效的字串輸入參數|.NET Framework 輸出型別|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>字串轉成 Double  
 下列表格說明使用 **ToDouble** 方法將字串轉換成 **Single**，給定的輸入字串會產生哪些型別。  
  
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
  
## <a name="see-also"></a>請參閱  
 [XML 資料類型轉換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [將 .NET Framework 類型轉換成字串](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
