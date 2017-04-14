---
title: "弱型別 JSON 序列化範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# 弱型別 JSON 序列化範例
當將使用者定義的型別序列化為指定的 Wire 格式，或是將 Wire 格式還原序列化為使用者定義的型別時，服務和用戶端都必須提供指定的使用者定義型別，以供使用。 一般而言，若要完成這項操作，<xref:System.Runtime.Serialization.DataContractAttribute> 屬性會套用至這些使用者定義的型別，而 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性會套用至其成員。 這個機制也適用於使用 JavaScript Object Notation \(JSON\) 物件的情況，如主題[HOW TO：序列化及還原序列化 JSON 資料](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)中所述。  
  
 在某些案例中，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務或用戶端必須存取不受開發人員控制的服務或用戶端所產生的 JSON 物件。 隨著更多的 Web 服務公開 JSON API，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發人員建構本機使用者定義的型別以在其中還原序列化任意 JSON 物件，會變得不切實際。 這個範例會提供機制，讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發人員可使用已還原序列化的任意 JSON 物件，而不需建立使用者定義的型別。 這稱為 JSON 物件的「*弱型別序列化*」\(Weakly\-Typed Serialization\)，因為在編譯時期尚不知 JSON 物件要還原序列化成何種型別。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 例如，公用 Web 服務 API 會傳回下列 JSON 物件，此物件描述有關服務的使用者的一些資訊。  
  
```  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 若要還原序列化這個物件，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端必須實作下列使用者定義的型別。  
  
```  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
  
```  
  
 這可能會很麻煩，特別是如果用戶端必須處理一種以上的 JSON 物件型別。  
  
 這個範例提供的 `JsonObject` 型別引入還原序列化 JSON 物件的弱式型別表示。`JsonObject` 需要依賴 JSON 物件與 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 字典之間的自然對應以及 JSON 陣列與 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 陣列之間的對應。 下列程式碼會顯示 `JsonObject` 型別。  
  
```  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 請注意，您可以「瀏覽」JSON 物件和陣列，而不需要在編譯時宣告它們的型別。 如需最上層 `["root"]` 物件之需求的說明，請參閱主題[JSON 和 XML 之間的對應](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)。  
  
> [!NOTE]
>  `JsonObject` 類別僅供做為範例之用。 它尚未經過徹底的測試，不應用於實際執行環境中。 弱型別 JSON 序列化有個明顯的含意存在，就是在使用 `JsonObject` 時，缺少型別安全性。  
  
 若要使用 `JsonObject` 型別，用戶端作業合約必須使用 <xref:System.ServiceModel.Channels.Message> 做為其傳回型別。  
  
```  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
  
```  
  
 然後，`JsonObject` 會具現化，如下列程式碼所示。  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
  
```  
  
 `JsonObject` 建構函式會採用透過 <xref:System.Xml.XmlDictionaryReader> 方法取得的 <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>。 讀取器包含用戶端所接收之 JSON 訊息的 XML 表示。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][JSON 和 XML 之間的對應](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) 主題。  
  
 此程式會產生下列輸出：  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### 若要安裝、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  依照[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)所述，建置方案 WeaklyTypedJson.sln。  
  
3.  執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation \(WCF\) and Windows Workflow Foundation \(WF\) Samples for .NET Framework 4  \(適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例\)](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## 請參閱