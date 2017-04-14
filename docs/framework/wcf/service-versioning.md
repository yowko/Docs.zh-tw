---
title: "服務版本控制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# 服務版本控制
在初始部署以及存留期間可能的數次部署之後，服務 \(以及公開的端點\) 可能因各種不同的原因而需要變更，例如變更業務需要、資訊技術需求，或解決其他問題等。每個變更都會產生新的服務版本。本主題將說明，如何考量 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 中的版本控制。  
  
## 四種服務變更的分類  
 可能需要的服務變更可分成四個分類：  
  
-   合約變更：例如，可能加入作業，或是可能加入或變更訊息中的資料項目。  
  
-   位址變更：例如，服務移到不同的位置，而使端點使用新的位址。  
  
-   繫結變更：例如，安全性機制變更或其設定變更。  
  
-   實作變更：例如，內部方法實作變更時。  
  
 其中某些變更稱為「中斷」，其他則稱為「非中斷」變更。在舊版中能夠成功處理的所有訊息，若也能在新版中成功處理，則這類變更就叫做「*非中斷*」。不符合上述規則的任何變更則稱為「*中斷*」\(Breaking\) 變更。  
  
## 服務方向與版本控制  
 其中一個服務方向的原則是，服務和用戶端都是自發的 \(或獨立的\)。除此之外，這還暗示服務開發人員不得假設其控制了，甚至了解所有服務用戶端。如此即可消除服務變更版本時，重新建置及部署所有用戶端的選擇。本主題假設服務符合這個原則，因此必須獨立於其用戶端進行變更或「版本控制」。  
  
 在發生非預期或無法避免的中斷變更情況下，應用程式可以選擇忽略這個原則，並且要求以新版服務重建及重新部署用戶端。  
  
## 合約版本控制  
 用戶端使用的合約不需要與服務使用的合約相同，兩者只需相容即可。  
  
 對於服務合約而言，相容性是指可以加入服務所公開的新作業，但是語意上不可移除或變更現有作業。  
  
 對於資料合約而言，相容性是指可以加入新的結構描述型別定義，但是不可以中斷的方式變更現有的結構描述型別定義。中斷變更可能包括移除資料成員，或是以不相容的方式變更其資料型別。這個功能為服務提供了一些變更其合約版本的空間，而不需中斷用戶端。以下兩章節將說明，可以對 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 資料和服務合約進行的非中斷和中斷變更。  
  
## 資料合約版本控制  
 本章節說明使用 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.DataContractAttribute> 類別時的資料版本控制。  
  
### 嚴格的版本控制  
 在許多變更版本會是問題的情況下，服務開發人員無法控制用戶端，因此無法假設用戶端對於訊息 XML 或結構描述中的變更會如何反應。在這些情況下，您必須保證新的訊息將對舊的結構描述驗證，原因有兩個：  
  
-   舊的用戶端是在結構描述不會變更的假設下開發。因此可能無法處理不屬於其設計目的的訊息。  
  
-   舊的用戶端甚至會在嘗試處理訊息之前，就先根據舊的結構描述執行實際結構描述驗證。  
  
 在這類情況下，建議的方法是將現有資料合約視為固定不變，並且以唯一的 XML 限定名稱建立新合約。接著服務開發人員會將新方法加入至現有服務合約中，或是建立新的服務合約，其中包含使用新資料合約的方法。  
  
 一般常見的情況是，服務開發人員需要寫入一些商務邏輯，這些邏輯應在所有資料合約版本以及每一個資料合約版本的版本專屬商務程式碼內執行。本主題最後的附錄將說明，如何使用介面滿足這項需要。  
  
### Lax 版本控制  
 在其他許多情況中，服務開發人員可能假設，加入新的選擇性成員至資料合約將不會中斷現有用戶端。這需要服務開發人員調查現有用戶端是否未執行結構描述驗證，以及他們是否忽略未知的資料成員。在這些情況中，可能會利用資料合約功能以非中斷的方式加入新成員。如果進行版本控制的資料合約功能在服務的第一個版本就已使用，那麼服務開發人員就可以很有信心地進行這項假設。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]、ASP.NET Web 服務及許多其他 Web 服務堆疊都支援「*lax 版本控制*」：也就是說，它們不會針對所收到之資料中新的未知資料成員擲回例外狀況。  
  
 一般很容易誤信，加入新成員不會中斷現有用戶端。如果您不確定所有用戶端都能處理 lax 版本控制，則建議您使用嚴格版本控制方針，並且將資料合約視為固定不變。  
  
 如需資料合約的 lax 與嚴格版本控制的詳細方針，請參閱[最佳做法：資料合約版本控制](../../../docs/framework/wcf/best-practices-data-contract-versioning.md)。  
  
### 分辨資料合約與 .NET 型別  
 .NET 類別或結構可藉由將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至該類別，而予以投射為資料合約。.NET 型別及其資料合約規劃是兩件不同的事。您可以擁有多個 .NET 型別使用相同的資料合約規劃。這項分別相當實用，可讓您在變更 .NET 型別的同時維持規劃的資料合約，甚至在用字嚴格的情況下也能藉此維持與現有用戶端的相容性。若要維持 .NET 型別和資料合約之間的這項區別，有兩件事您務必要做到：  
  
-   請指定 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 和 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>。您務必要指定資料合約的名稱和命名空間，以避免在合約中公開 .NET 型別的名稱和命名空間。如此一來，即使您之後決定變更 .NET 命名空間或型別名稱，資料合約仍會維持不變。  
  
-   請指定 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>。您務必要指定資料成員的名稱，以避免在合約中公開 .NET 成員的名稱。如此一來，即使您之後決定變更成員的 .NET 名稱，資料合約仍會維持不變。  
  
### 變更或移除成員  
 即使在允許 lax 版本控制的情況下，變更成員的名稱或資料，或是移除資料成員即屬於中斷變更。如果這是必要的，請建立新的資料合約。  
  
 如果服務相容性相當重要，您或許會考慮忽略程式碼中未使用的資料成員，並讓它們留在原處。如果要將資料成員分割成多個成員，您或許會考慮保留現有的成員，做為可執行低階用戶端 \(未升級為最新版本的用戶端\) 所需分割及重新彙總的屬性。  
  
 資料合約名稱或命名空間的變更同樣是中斷變更。  
  
### 反覆存取未知的資料  
 在某些情況下，會需要「反覆存取」來自新版本中所加入之成員的未知資料。例如，"versionNew" 服務會將包含新加入之成員的資料傳送至 "versionOld" 用戶端。用戶端會在處理訊息時忽略新加入的成員，但是會將包括新加入之成員的相同資料再次傳送回 versionNew 服務。這種情況常見的案例為資料更新，其中資料會從服務擷取、變更，再傳回。  
  
 若要啟用特定類型的往返，類型必須實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面，這個介面包含一個屬性 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>，會傳回 <xref:System.Runtime.Serialization.ExtensionDataObject> 型別。這個屬性是用來儲存資料合約未來版本中的任何資料，而此資料合約對目前版本來說是未知的。這個資料不會讓用戶端看見，但是當執行個體序列化時，就會將其餘資料合約成員的資料寫入 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 屬性的內容。  
  
 建議所有的型別都實作此介面，以納入新的和未知的未來成員。  
  
### 資料合約程式庫  
 資料合約的程式庫可能存在，合約會在其中發行至中央儲存機制，而服務和型別實作器會從該儲存機制實作和公開資料合約。在此情況下，將資料合約發行至儲存機制時，您無法控制誰會建立實作該合約之型別。因此，一旦合約發行之後，就無法進行修改，而產生有效的固定不變狀態。  
  
### 使用 XmlSerializer  
 使用 <xref:System.Xml.Serialization.XmlSerializer> 類別時適用相同的版本控制準則。需要嚴格版本控制時，請將資料合約視為固定不變，並且以唯一的限定名稱為新版本建立新的資料合約。如果您確定可以使用 lax 版本控制，則可在新版本中加入新的可序列化成員，但是不變更或移除現有成員。  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> 會使用 <xref:System.Xml.Serialization.XmlAnyElementAttribute> 和 <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> 屬性支援未知資料的反覆存取。  
  
## 訊息合約版本控制  
 訊息合約版本控制的方針與資料合約版本控制十分相似。如果需要嚴格版本控制，則不應變更訊息本文，而是以唯一的限定名稱建立新的訊息合約。如果您確認可以使用 lax 版本控制，則可以加入新的訊息本文部分，但不變更或移除現有部分。本指引同時適用不包裝和包裝的訊息合約。  
  
 即使使用嚴格版本控制，仍可以加入訊息標頭。MustUnderstand 旗標可能會影響版本控制。一般而言，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中標頭的版本控制模型就如 SOAP 規格中所述。  
  
## 服務合約版本控制  
 服務合約版本控制與資料合約版本控制相似，同樣包含加入、變更和移除作業。  
  
### 指定名稱、命名空間和動作  
 根據預設，服務合約的名稱即是介面的名稱。其預設的命名空間為 "http:\/\/tempuri.org"，而各項作業的動作為 "http:\/\/tempuri.org\/contractname\/methodname"。建議您明確指定服務合約的名稱和命名空間及各項作業的動作，以避免使用 "http:\/\/tempuri.org"，同時避免在服務合約中公開介面和方法名稱。  
  
### 加入參數和作業  
 加入服務所公開的服務作業為非中斷變更，因為現有用戶端不需考量這些新作業。  
  
> [!NOTE]
>  將作業加入至雙工回呼合約為中斷變更。  
  
### 變更作業參數或傳回型別  
 一般來說，變更參數或傳回型別是中斷變更，除非新型別與舊型別實作的資料合約相同。若要進行這類變更，請將新作業加入服務合約或定義新的服務合約。  
  
### 移除作業  
 移除作業同樣屬於中斷變更。若要進行這類變更，請定義新的服務合約並且在新端點上公開。  
  
### 錯誤合約  
 <xref:System.ServiceModel.FaultContractAttribute> 屬性可讓服務合約開發人員指定可從合約作業傳回的錯誤資訊。  
  
 服務合約中所述的錯誤清單並不詳盡。作業可能隨時傳回未於其合約中說明的錯誤。因此，變更合約中所述的錯誤集不視為中斷。例如，使用 <xref:System.ServiceModel.FaultContractAttribute> 將新錯誤加入至合約中，或從合約中移除現有錯誤。  
  
### 服務合約程式庫  
 組織可能擁有合約的程式庫，合約會在其中發行至中央儲存機制，而服務實作器會從該儲存機制實作合約。在此情況下，將服務合約發行至儲存機制時，您無法控制誰會建立實作該合約之服務。因此，一旦服務合約發行之後，就無法進行修改，形成實際上不可變的狀態。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 支援合約繼承，可用來建立擴充現有合約的新合約。若要使用此功能，請定義繼承自舊服務合約介面的新服務合約介面，然後將方法加入至新介面。接著將實作舊合約的服務變更為實作新合約，並且將 "versionOld" 端點定義變更為使用新的合約。對於 "versionOld" 用戶端而言，端點將隨公開 "versionOld" 合約繼續出現，而對於 "versionNew" 用戶端而言，端點將出現以公開 "versionNew" 合約。  
  
## 位址與繫結版本控制  
 端點位址和繫結的變更屬於中斷變更，除非用戶端能夠動態地發現新端點位址或繫結。實作此功能的一項機制是藉由使用通用探索、描述和整合 \(UDDI\) 登錄以及 UDDI 引動模式，其中用戶端會嘗試與端點進行通訊，並且在發生錯誤時，查詢已知 UDDI 登錄中目前端點的中繼資料。然後用戶端會使用來自這項中繼資料的位址和繫結與端點進行通訊。如果此通訊成功，用戶端就會快取位址和繫結資訊以供未來使用。  
  
## 路由服務與版本控制  
 如果對服務所做的變更是中斷變更，而且您必須同時執行兩個以上不同的服務版本，就可以使用 WCF 路由服務，將訊息路由傳送至適當的服務執行個體。WCF 路由服務會使用以內容為基礎的路由，換言之，它會使用訊息內部的資訊來判斷要路由傳送訊息的目標位置。[!INCLUDE[crabout](../../../includes/crabout-md.md)] WCF 路由服務的詳細資訊，請參閱[路由服務](../../../docs/framework/wcf/feature-details/routing-service.md)。如需如何使用 WCF 路由服務進行服務版本控制的範例，請參閱 [HOW TO：服務版本控制](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)。  
  
## 附錄  
 需要嚴格版本控制時的一般資料合約版本控制方針，是將資料合約視為固定不變，並且在需要變更時建立新的合約。您必須針對每個新的資料合約建立新類別，因此需要有機制避免採用根據舊資料合約類別撰寫的現有程式碼之後，還須再根據新資料合約類別重新撰寫。  
  
 這類機制的其中一種是使用介面定義各資料合約的成員，並且根據介面而非實作介面的資料合約類別，撰寫內部實作程式碼。以下第 1 版服務的程式碼示範 `IPurchaseOrderV1` 介面和 `PurchaseOrderV1`。  
  
```  
public interface IPurchaseOrderV1  
{  
    string OrderId { get; set; }  
    string CustomerId { get; set; }  
}  
  
[DataContract(  
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2005/10/PurchaseOrder")]  
public class PurchaseOrderV1 : IPurchaseOrderV1  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
}  
```  
  
 即使服務合約的作業可以根據 `PurchaseOrderV1` 撰寫，實際商務邏輯仍會根據 `IPurchaseOrderV1`。接著在第 2 版中，會有一個新的 `IPurchaseOrderV2` 介面和新的 `PurchaseOrderV2` 類別，如以下程式碼中所示：  
  
```  
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}  
[DataContract(   
Name = "PurchaseOrder ",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public DateTime OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 服務合約會更新，以加入根據 `PurchaseOrderV2` 所撰寫的新作業。根據 `IPurchaseOrderV1` 撰寫的現有商務邏輯會在 `PurchaseOrderV2` 中繼續運作，而需要 `OrderDate` 屬性的新商務邏輯則會根據 `IPurchaseOrderV2` 撰寫。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>   
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>   
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>   
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>   
 <xref:System.Runtime.Serialization.IExtensibleDataObject>   
 <xref:System.Runtime.Serialization.ExtensionDataObject>   
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>   
 <xref:System.Xml.Serialization.XmlSerializer>   
 [資料合約等價](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)   
 [版本相容序列化回呼](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)