---
title: 資料合同Jon序列化器樣品
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144626"
---
# <a name="datacontractjsonserializer-sample"></a>資料合同Jon序列化器樣品

> [!NOTE]
> 此示例用於<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。 對於大多數涉及序列化和反序列化 JSON 的方案，我們建議[在系統中使用 API。](../../../standard/serialization/system-text-json-overview.md)

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 與 <xref:System.Runtime.Serialization.DataContractSerializer> 支援相同的型別。 當撰寫 Asynchronous JavaScript and XML (AJAX) 型 Web 應用程式時，JSON 資料格式特別有用。 Windows 通信基礎 （WCF） 中的 AJAX 支援經過優化，可通過腳本管理器控制項與ASP.NET AJAX 一起使用。 有關如何將 Windows 通信基礎 （WCF） 與 ASP.NET AJAX 一起使用的示例，請參閱[AJAX 示例](ajax.md)。  
  
此範例的安裝程序與建置指示位於本主題的結尾。  
  
此範例會使用 `Person` 資料合約以示範序列化與還原序列化。  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 若要將 `Person` 型別的執行個體序列化為 JSON，請先建立 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，然後使用 `WriteObject` 方法將 JSON 資料寫入資料流。  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 這個記憶體資料流包含有效的 JSON 資料。
  
```json  
{"age":42,"name":"John"}  
```  
  
 此範例會示範從 JSON 資料還原序列化為物件。 接下來，您要倒轉資料流並呼叫 `ReadObject`。  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 檢查 `p2` 物件，便可顯示 JSON 資料是否已正確地還原序列化。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要設定、建置及執行範例  
  
1. 生成解決方案 Json 序列化.sln，如[構建 Windows 通信基礎示例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述。  
  
2. 執行產生的主控台應用程式。  
