---
title: "XML 資料型別轉換"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a>XML 資料型別轉換
大部分的方法中找到**XmlConvert**類別用於字串和強型別格式之間轉換資料。 這些方法都和地區設定無關。 也就是說，它們在進行轉換時並不會考慮任何地區設定的設定。  
  
## <a name="reading-string-as-types"></a>將字串讀成型別  
 下列範例會讀取字串並轉換成**DateTime**型別。  
  
 假設有以下的 XML 輸入：  
  
 **輸入**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 此程式碼將字串轉換成**DateTime**格式：  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a>將字串寫成型別  
 下列範例會讀取**Int32**並將它轉換成字串。  
  
 假設有以下的 XML 輸入：  
  
 **輸入**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 此程式碼將轉換**Int32**到**字串**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>另請參閱  
 [將字串轉換為.NET Framework 資料型別](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [將.NET Framework 型別轉換為字串](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
