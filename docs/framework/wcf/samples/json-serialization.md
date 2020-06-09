---
title: DataContractJsonSerializer 範例
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 4aa0ee679ae424251000b14abfbacf0590a6ccd3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592017"
---
# <a name="datacontractjsonserializer-sample"></a>DataContractJsonSerializer 範例

> [!NOTE]
> 這個範例適用于 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 。 對於涉及序列化和還原序列化 JSON 的大部分案例，我們建議在 system.string[命名空間](../../../standard/serialization/system-text-json-overview.md)中的 api。

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 與 <xref:System.Runtime.Serialization.DataContractSerializer> 支援相同的型別。 當撰寫 Asynchronous JavaScript and XML (AJAX) 型 Web 應用程式時，JSON 資料格式特別有用。 Windows Communication Foundation （WCF）中的 AJAX 支援已優化，可透過 ScriptManager 控制項與 ASP.NET AJAX 搭配使用。 如需如何搭配使用 Windows Communication Foundation （WCF）與 ASP.NET AJAX 的範例，請參閱[AJAX 範例](ajax.md)。  
  
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
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要設定、建置及執行範例  
  
1. 如[建立 Windows Communication Foundation 範例](building-the-samples.md)中所述，建立方案 JsonSerialization。  
  
2. 執行產生的主控台應用程式。  
