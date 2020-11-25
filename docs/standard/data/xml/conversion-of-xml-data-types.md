---
title: XML 資料型別轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: 108cfbf1ee8ff3d6fbe088d6dd14d0354750cb0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701493"
---
# <a name="conversion-of-xml-data-types"></a>XML 資料型別轉換

在 **XmlConvert** 類別中找到的大部分方法都是用來轉換字串與強型別格式之間的資料。 這些方法都和地區設定無關。 也就是說，它們在進行轉換時並不會考慮任何地區設定的設定。  
  
## <a name="reading-string-as-types"></a>將字串讀成型別  

 下列範例會讀取一個字串，並將它轉換成 **DateTime** 型別。  
  
 假設有以下的 XML 輸入：  
  
 **輸入**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 這個程式碼會將該字串轉換成 **DateTime** 格式：  
  
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

 下列範例會讀取一個 **Int32**，並將它轉換成一個字串。  
  
 假設有以下的 XML 輸入：  
  
 **輸入**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 這個程式碼會將 **Int32** 轉換成 **String**：  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>另請參閱

- [將字串轉換成 .NET Framework 資料型別](converting-strings-to-dotnet-data-types.md)
- [將 .NET Framework 型別轉換成字串](converting-dotnet-types-to-strings.md)
