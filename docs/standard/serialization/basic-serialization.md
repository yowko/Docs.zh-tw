---
title: 基本序列化
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: cb42c265d9057ea4fdb76e72fc9cdb2368309cae
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743839"
---
# <a name="basic-serialization"></a>基本序列化

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

要讓類別可序列化的最簡單方式就是以 <xref:System.SerializableAttribute> 加以標示，如下所示。  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
下列程式碼範例示範如何將此類別的執行個體序列化成檔案。  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
此範例使用二進位格式子進行序列化。 您只需要建立資料流執行個體以及想要使用的格式子，然後在格式子上呼叫 **Serialize** 方法。 將要序列化的資料流及物件，當做參數提供給此呼叫。 雖然在此範例中未明確示範，不過類別的所有成員變數都將序列化，即使是標示為私用的變數亦然。 在這方面，二進位序列化與 <xref:System.Xml.Serialization.XmlSerializer> 類別不同，後者只會序列化公用欄位。 如需從二進位序列化排除成員變數的資訊，請參閱[選擇式序列化](selective-serialization.md)。  
  
將物件還原成其先前的狀態也一樣容易。 首先，建立供讀取的資料流和 <xref:System.Runtime.Serialization.Formatter>，然後指示格式子對物件還原序列化。 下列程式碼範例會示範其做法。  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
上述使用的 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 非常有效率，可產生精簡的位元組資料流。 利用此格式子序列化的所有物件也可以用它來還原序列化，所以此格式子是理想的工具，可以在 .NET Framework 上對將要還原序列化的物件進行序列化。 務必注意，物件還原序列化時，不會呼叫建構函式。 還原序列化有此限制是基於效能的考量。 然而，這樣違反了執行階段與物件寫入器之間建立的某些一般合約，開發人員應確定他們了解將物件標示為可序列化時，可能出現的後果。  
  
如果要求可攜性，請改為使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>。 只要將上述程式碼中的 **BinaryFormatter** 取代為 **SoapFormatter**，並如之前一樣呼叫 **Serialize** 和 **Deserialize** 即可。 在上述範例中使用的此格式子會產生下列輸出。  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:SOAP- ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP- ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
請注意，無法繼承 [Serializable](xref:System.SerializableAttribute) 屬性。 若您從 `MyObject` 衍生新類別，新類別必須也用該屬性標示，否則無法將其序列化。 例如，當您嘗試序列化下列類別的執行個體時，會出現 <xref:System.Runtime.Serialization.SerializationException> 通知您 `MyStuff` 類型未標示為可序列化。  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 使用 [Serializable](xref:System.SerializableAttribute) 屬性十分方便，但有上述限制。 如需何時應將類別標示為序列化的資訊，請參閱[序列化方針](serialization-guidelines.md)。 類別在編譯後即無法在其中新增序列化。  
  
## <a name="see-also"></a>另請參閱

- [二進位序列化](binary-serialization.md)  
- [XML 和 SOAP 序列化](xml-and-soap-serialization.md)
