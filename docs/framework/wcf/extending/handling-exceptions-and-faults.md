---
title: "處理例外狀況和錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a69acb9b640c17e6641efc6c30798e3856ef6e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="handling-exceptions-and-faults"></a>處理例外狀況和錯誤
例外狀況是用來在本機上傳送服務或用戶端實作內發生的錯誤。 另一方面，錯誤 (Fault) 是用來傳送跨越服務界限 (例如從伺服器到用戶端，反之亦然) 發生的錯誤 (Error)。 除了錯誤 (Fault) 以外，傳輸通道也經常會使用傳輸特定的機制來傳送傳輸層級的錯誤 (Error)。 例如，HTTP 傳輸會使用 404 等狀態碼來傳送不存在的端點 URL (表示沒有端點可傳回錯誤)。 本文件包含的三個章節都提供指引給自訂通道作者。 第一個章節會提供關於何時與如何定義及擲回例外狀況的指引， 而第二個章節會提供關於產生和使用錯誤的指引， 第三個章節則會說明如何提供追蹤資訊，以協助自訂通道的使用者針對執行中的應用程式進行疑難排解。  
  
## <a name="exceptions"></a>例外狀況  
 在擲回例外狀況時必須記住兩件事。首先，例外狀況的類型必須可讓使用者撰寫可適當回應此例外狀況的正確程式碼。 其次，例外狀況必須提供足夠的資訊，讓使用者瞭解何處出錯、失敗的影響以及如何進行修正。 下列章節會提供關於 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 通道之例外狀況類型與訊息的指引。 在＜例外狀況的設計方針＞文件中，也有關於 .NET 例外狀況的一般指引。  
  
### <a name="exception-types"></a>例外狀況類型  
 由通道擲回的所有例外狀況都必須是 <xref:System.TimeoutException?displayProperty=nameWithType>、<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>，或是從 <xref:System.ServiceModel.CommunicationException> 衍生的類型。 系統可能也會擲回 <xref:System.ObjectDisposedException> 等例外狀況，不過這只是用來表示呼叫的程式碼誤用通道。 如果正確使用通道，它一定只會擲回指定的例外狀況。) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的七個例外狀況型別是衍生自 <xref:System.ServiceModel.CommunicationException>，而且是設計給通道使用。 還有其他 <xref:System.ServiceModel.CommunicationException>衍生的例外狀況是設計用來讓系統的其他部分使用。 這些例外狀況類型包括：  
  
|例外狀況類型|意義|內部例外狀況內容|復原策略|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|指定用於接聽的端點位址已在使用中。|如果有的話，則提供造成此例外狀況之傳輸錯誤的詳細資料。 例如： <xref:System.IO.PipeException>、<xref:System.Net.HttpListenerException> 或 <xref:System.Net.Sockets.SocketException>。|嘗試不同的位址。|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|此處理序不可以存取指定用於接聽的端點位址。|如果有的話，則提供造成此例外狀況之傳輸錯誤的詳細資料。 例如，<xref:System.IO.PipeException> 或 <xref:System.Net.HttpListenerException>。|嘗試使用不同的認證。|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject>正處於 Faulted 狀態 (如需詳細資訊，請參閱[了解狀態變更](../../../../docs/framework/wcf/extending/understanding-state-changes.md))。 請注意，當具有多個擱置呼叫的物件轉換為「錯誤」狀態時，只有一個呼叫會擲回與該失敗相關的例外狀況，而其餘的呼叫會擲回 <xref:System.ServiceModel.CommunicationObjectFaultedException>。 這個例外狀況的擲回原因，通常是因為應用程式忽略某個例外狀況，而且嘗試在可能不同於攔截原始例外狀況之執行緒上使用已經出錯的物件。|如果有的話，則提供此內部例外狀況的詳細資料。|建立新的物件。 請注意，視當初造成 <xref:System.ServiceModel.ICommunicationObject> 出錯的原因而定，可能會需要進行其他工作來復原。|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject>中止正在使用 (如需詳細資訊，請參閱[了解狀態變更](../../../../docs/framework/wcf/extending/understanding-state-changes.md))。 類似於 <xref:System.ServiceModel.CommunicationObjectFaultedException>，此例外狀況表示應用程式已對可能來自其他執行緒的物件呼叫 <xref:System.ServiceModel.ICommunicationObject.Abort%2A>，該物件因此而無法再使用。|如果有的話，則提供此內部例外狀況的詳細資料。|建立新的物件。 請注意，視當初造成 <xref:System.ServiceModel.ICommunicationObject> 中止的原因而定，可能會需要進行其他工作來復原。|  
|<xref:System.ServiceModel.EndpointNotFoundException>|目標遠端端點未接聽。 這可能是由於端點位址的某個部分不正確、無法解析，或是端點已關閉。 範例包括 DNS 錯誤、無法使用佇列管理員，以及未執行服務。|內部例外狀況會提供詳細資料 (通常是透過基礎傳輸)。|嘗試不同的位址。 或者，如果服務已關閉，傳送者可以稍後再試一次|  
|<xref:System.ServiceModel.ProtocolException>|端點原則所描述的通訊協定在端點之間彼此不相符。 例如，框架處理內容類型不符，或是超出最大的訊息大小。|如果有的話，則提供特定通訊協定錯誤的詳細資料。 例如，如果錯誤原因是超過 MaxReceivedMessageSize，則 <xref:System.ServiceModel.QuotaExceededException> 是內部例外狀況。|復原：確定傳送者和接收的通訊協定設定相符。 若要這麼做，其中一個方法就是重新匯入服務端點的中繼資料 (原則)，並使用產生的繫結來重新建立通道。|  
|<xref:System.ServiceModel.ServerTooBusyException>|遠端端點正在接聽，但是尚未準備進行處理訊息。|如果有的話，內部例外狀況就會提供 SOAP 錯誤 (Fault) 或傳輸層級錯誤 (Error) 的詳細資料。|復原：稍候並重新嘗試進行作業。|  
|<xref:System.TimeoutException>|作業無法在逾時期限內完成。|可提供逾時的詳細資料。|稍候並重新嘗試進行作業。|  
  
 只有在類型對應至不同於任何現有例外狀況類型的特定復原策略時，才會定義新的例外狀況類型。 如果確實要定義新的例外狀況類型，該類型就必須衍生自 <xref:System.ServiceModel.CommunicationException> 或是其所衍生的一個類別。  
  
### <a name="exception-messages"></a>例外狀況訊息  
 例外狀況訊息的對象是使用者而不是程式，所以這類訊息應該提供充分的資訊，協助使用者瞭解並解決問題。 良好的例外狀況訊息包括三個重要部分：  
  
 發生的情況。 使用與使用者切身操作相關的術語，提供清楚的問題描述。 例如，「無效的組態區段」就是不好的例外狀況訊息。 這個訊息會讓使用者猜測究竟是哪個組態區段不正確，以及為什麼不正確。 改良的訊息會是 「 無效的組態區段\<customBinding > 」。 而更好的訊息會是「無法將名為 myTransport 的傳輸新增至名為 myBinding 的繫結，因為該繫結已經具有名為 myTransport 的傳輸」。 這是非常仔細的訊息，使用者可以在應用程式組態檔中輕鬆識別這個訊息使用的術語和名稱。 不過，這個訊息還漏掉了一些關鍵部分。  
  
 錯誤的重要性。 除非訊息清楚表示錯誤的意義，不然使用者可能會猜想這個錯誤是否為嚴重錯誤，或者是否可以忽略。 一般而言，訊息的開頭應該要提供錯誤的意義或重要性。 若要改進先前的範例，訊息可以改成「ServiceHost 無法開啟，這是因為發生以下組態錯誤：無法將名為 myTransport 的傳輸新增到名為 myBinding 的繫結，因為繫結已經具有名為 myTransport 的傳輸」。  
  
 使用者應該如何修正問題。 訊息最重要的部分就是協助使用者修正問題， 所以應該包含一些關於要檢查或修正哪些項目以補救問題的指引或提示。 例如，「ServiceHost 無法開啟，這是因為發生以下組態錯誤：無法將名為 myTransport 的傳輸新增到名為 myBinding 的繫結，因為繫結已經具有名為 myTransport 的傳輸。 請確定繫結中只有一個傳輸」。  
  
## <a name="communicating-faults"></a>傳送錯誤  
 SOAP 1.1 和 SOAP 1.2 都會定義錯誤的特定結構。 這兩種規格之間雖有某些差異，但一般而言，Message 和 MessageFault 類型都是用來建立和使用錯誤。  
  
 ![處理例外狀況和錯誤](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SOAP 1.2 錯誤 (左邊) 和 SOAP 1.1 錯誤 (右邊)。 請注意，在 SOAP 1.1 中，只有「錯誤」項目符合命名空間。  
  
 SOAP 會將錯誤訊息定義為只包含錯誤項目 (名稱為 `<env:Fault>` 的項目) 做為 `<env:Body>` 之子系的訊息。 此錯誤項目的內容在 SOAP 1.1 與 SOAP 1.2 之間稍有不同，如圖 1 所示。 不過，<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> 類別會將這些差異都正規化到一個物件模型中：  
  
```  
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 `Code` 屬性會對應到 `env:Code` (或是 SOAP 1.1 中的 `faultCode`)，並且會識別該錯誤的類型。 SOAP 1.2 針對 `faultCode` 定義五種可允許的值 (例如，Sender 和 Receiver)，並且定義可以包含任何子代碼值的 `Subcode` 項目  (請參閱[SOAP 1.2 規格](http://go.microsoft.com/fwlink/?LinkId=95176)可允許的錯誤代碼和其意義的清單。)SOAP 1.1 的機制稍微有些不同：它會定義四種 `faultCode` 值 (例如，Client 和 Server)，而這四個值可以藉由定義全新的值或使用點標記法建立更詳盡的 `faultCodes` (例如 Client.Authentication) 來擴充。  
  
 當您使用 MessageFault 來撰寫錯誤時，FaultCode.Name 和 FaultCode.Namespace 便會對應至 SOAP 1.2 `env:Code` 或 SOAP 1.1 `faultCode` 的名稱和命名空間。 在 SOAP 1.2 中，FaultCode.SubCode 會對應至 `env:Subcode`，若在 SOAP 1.1 則會對應至 null。  
  
 如果需要以程式設計的方式來區別錯誤，您就應該建立新的錯誤子代碼 (如果是使用 SOAP 1.1 則是建立新的錯誤代碼)。 這種做法類似於建立新的例外狀況類型。 您應該避免搭配 SOAP 1.1 錯誤代碼使用點標記法  ( [WS-Basic profile](http://go.microsoft.com/fwlink/?LinkId=95177)也阻止錯誤點標記法使用。)  
  
```  
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 `Reason` 屬性會對應至 `env:Reason` (或是 SOAP 1.1 的 `faultString`)，這是人們可讀取的 (Human-Readable) 錯誤條件描述，類似於例外狀況的訊息。 `FaultReason` 類別 (以及 SOAP 的 `env:Reason/faultString`) 內建的支援適用在全球化時進行多種翻譯。  
  
```  
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations   
    {   
       get;   
    }  
  
 }  
```  
  
 錯誤詳細資料內容會公開在 MessageFault 使用各種方法，包括`GetDetail` \<T > 和`GetReaderAtDetailContents`（)。 錯誤詳細資料是一種不透明項目，用來夾帶有關錯誤的其他詳細資料。 如果您要隨錯誤夾帶某些任意的結構化詳細資料，這種資料就會非常有用。  
  
### <a name="generating-faults"></a>產生錯誤  
 本節說明的程序會產生錯誤 (Fault)，以回應通道或由通道建立之訊息屬性中偵測到的錯誤 (Error) 狀況。 例如，傳回錯誤以回應包含無效資料的要求訊息，這就是一種常見情況。  
  
 產生錯誤時，自訂通道不應直接傳送錯誤，而是應該擲回例外狀況，並讓上一層決定是否要將該例外狀況轉換成錯誤，以及使用何種方法進行傳送。 為了促進這項轉換，通道應該提供可將自訂通道擲回的例外狀況轉換成適當錯誤的 `FaultConverter` 實作。 `FaultConverter` 會定義為：  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
}  
```  
  
 每個產生自訂錯誤的通道都必須實作 `FaultConverter`，並藉由呼叫 `GetProperty<FaultConverter>` 來傳回它。 自訂的 `OnTryCreateFaultMessage` 實作必須將例外狀況轉換成錯誤，或是委派到內部通道的 `FaultConverter`。 如果通道是一項傳輸，就必須轉換例外狀況，或是委派到編碼器的 `FaultConverter` 或 `FaultConverter` 中提供的預設 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。 預設的 `FaultConverter` 會轉換與 WS-Addressing 和 SOAP 指定之錯誤 (Fault) 訊息相對應的錯誤 (Error)。 以下是 `OnTryCreateFaultMessage` 實作的範例。  
  
```  
public override bool OnTryCreateFaultMessage(Exception exception,   
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&               
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =   
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,   
                   out message);  
#else  
    FaultConverter inner =   
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 這個模式的含意在於，在各層之間針對要求錯誤 (Fault) 之錯誤 (Error) 情況而擲回的例外狀況必須包含足夠的資訊，讓對應的錯誤 (Fault) 產生器建立正確的錯誤 (Fault)。 身為自訂通道作者，如果還沒有某些例外狀況，您可以定義這些對應到不同錯誤情況的例外狀況類型。 請注意，周遊通道層的例外狀況應該傳送錯誤 (Error) 狀況，而非不透明的錯誤 (Fault) 資料。  
  
### <a name="fault-categories"></a>錯誤分類  
 錯誤通常有三種分類：  
  
1.  遍佈在整個堆疊中的錯誤。 這些錯誤可能會出現在通道堆疊的任何一層，例如 InvalidCardinalityAddressingException。  
  
2.  可能出現在堆疊中特定層上方任何位置的錯誤，例如某些與流動的交易或安全性角色有關的錯誤。  
  
3.  導向到堆疊中單一層的錯誤 (Fault) ，例如 WS-RM 序號錯誤 (Fault) 等錯誤 (Error)。  
  
 類別目錄 1。 錯誤通常是指 WS-Addressing 和 SOAP 錯誤。 `FaultConverter` 所提供的基底 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 類別會轉換與 WS-Addressing 和 SOAP 指定之錯誤 (Fault) 訊息相對應的錯誤 (Error)，所以您不需要自己處理這些例外狀況的轉換。  
  
 類別目錄 2。 當某一層將屬性加入到未完全使用與該層相關之訊息資訊的訊息時，就會出現錯誤。 如果有較高層要求此訊息屬性更進一步處理訊息資訊時，可能就會偵測出錯誤 (Error)。 這類通道應該實作先前指定的 `GetProperty`，以便讓較高層能夠傳回正確的錯誤 (Fault)。 TransactionMessageProperty 就是一個範例， 這個屬性會新增到訊息中，不會完整驗證標頭中的所有資料 (這麼做可能會涉及連絡分散式交易協調器 (DTC))。  
  
 分類 3。 錯誤只會由處理器中的單一層產生和傳送。 因此，所有的例外狀況都包含在該層內部。 若要改進通道間的一致性並簡化維護程序，您的自訂通道應該使用先前指定的模式來產生內部錯誤的錯誤訊息。  
  
### <a name="interpreting-received-faults"></a>解譯收到的錯誤  
 本節提供在接收錯誤訊息時產生適當例外狀況的指引。 以下是在堆疊中處理各層訊息的決策樹：  
  
1.  如果此層將訊息視為無效，則應該進行其「無效訊息」處理。 這類處理專用於此層，不過可以包含捨棄訊息、追蹤，或是擲回轉換為錯誤的例外狀況。 範例包括接收未適當保護安全之訊息的安全性，或是接收具序號錯誤之訊息的 RM。  
  
2.  否則，如果訊息是專門套用至此層的錯誤訊息，而且訊息在此層的互動範圍以外不具任何意義，則此層應該要處理錯誤條件。 「RM 序列遭拒」錯誤就是一個範例，這個錯誤對 RM 通道上面的層級沒有任何意義，這表示將 RM 通道判定為失敗並將從擱置作業擲回。  
  
3.  否則，訊息應該從 Request() 或 Receive() 傳回。 例如，此層辨識出該錯誤，但錯誤只表示要求失敗，沒有表示將通道判定為失敗並將從擱置作業擲回。 若要改進這種情況下的可用性，此層應該實作 `GetProperty<FaultConverter>` 並傳回 `FaultConverter` 衍生類別，此類別可藉由覆寫 `OnTryCreateException` 將錯誤轉換成例外狀況。  
  
 下列物件模型支援將訊息轉換成例外狀況：  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
}  
```  
  
 通道層可以實作 `GetProperty<FaultConverter>`，以支援將錯誤訊息轉換成例外狀況。 若要這樣做，請覆寫 `OnTryCreateException` 並檢查錯誤訊息。 如果辨認成功就進行轉換，否則，要求內部通道來進行轉換。 傳輸通道應該要委派到 `FaultConverter.GetDefaultFaultConverter`，以取得預設的 SOAP/WS-Addressing FaultConverter。  
  
 一般的實作如下所示：  
  
```  
public override bool OnTryCreateException(  
                            Message message,   
                            MessageFault fault,   
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&   
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =   
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 如果是復原情形不同的特定錯誤情況，可考慮定義 `ProtocolException` 的衍生類別。  
  
### <a name="mustunderstand-processing"></a>MustUnderstand 處理  
 SOAP 會定義一般錯誤，表示接收者不瞭解必要標頭。 這個錯誤稱為 `mustUnderstand` 錯誤。 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，自訂通道永遠不會產生 `mustUnderstand` 錯誤， 反而是位於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通訊堆疊最上層的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 發送器會執行檢查，查看基礎堆疊是否瞭解所有已標記為 MustUndestand=true 的標頭。 如果全部都不瞭解，此時就會產生 `mustUnderstand` 錯誤。 使用者可以選擇關閉這個 `mustUnderstand` 處理，然後讓應用程式接收所有訊息標頭。 在這種情況下，應用程式便會負責執行 `mustUnderstand` 處理。產生的錯誤包括 NotUnderstood 標頭，其中包含堆疊不瞭解其 MustUnderstand=true 之標頭的名稱。  
  
 如果您的通訊協定通道傳送 MustUnderstand=true 的自訂標頭，並且收到 `mustUnderstand` 錯誤，則通道必須瞭解其傳送的標頭是否為該錯誤的成因。 `MessageFault` 類別上有兩個成員適用於這種情況：  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 如果錯誤是 `IsMustUnderstandFault` 錯誤，則 `true` 會傳回 `mustUnderstand`。 如果具有指定名稱和命名空間的標頭是當做 NotUnderstood 標頭加入到錯誤中，`WasHeaderNotUnderstood` 則會傳回 `true`。  否則它會傳回 `false`。  
  
 如果通道發出標記為 MustUnderstand = true 的標頭，則該層應同時實作「例外狀況產生 API」模式，而且應將該標頭造成的 `mustUnderstand` 錯誤轉換成更有用的例外狀況 (如前述)。  
  
## <a name="tracing"></a>追蹤  
 .NET Framework 提供一種追蹤程式執行的機制，如果無法直接附加偵錯工具並逐步執行程式碼，該機制有助於診斷實際執行應用程式或間歇性問題。 此機制的核心元件位於 <xref:System.Diagnostics?displayProperty=nameWithType> 命名空間，而且包含下列各項：  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>，這是要寫入之追蹤資訊的來源；<xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>，這是具體接聽項的抽象基底類別，這些具體接聽項會從 <xref:System.Diagnostics.TraceSource> 接收要追蹤的資訊，並將其輸出到接聽項特定的目的端。 例如，<xref:System.Diagnostics.XmlWriterTraceListener> 會將追蹤資訊輸出到 XML 檔。 最後一項是 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>，它可讓應用程式使用者控制追蹤詳細資訊，而且通常是在組態中指定。  
  
-   除了核心元件，您可以使用[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)檢視與搜尋[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]追蹤。 這個工具是專門設計用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 產生，並且使用 <xref:System.Diagnostics.XmlWriterTraceListener> 寫出的追蹤檔。 下圖顯示與追蹤有關的各種元件。  
  
 ![處理例外狀況和錯誤](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>從自訂通道追蹤  
 當偵錯工具無法附加到執行中的應用程式時，自訂通道便應該寫出追蹤訊息以協助診斷問題。 這涉及兩項高階工作：具現化 <xref:System.Diagnostics.TraceSource>，以及呼叫其方法來寫入追蹤。  
  
 當具現化 <xref:System.Diagnostics.TraceSource> 時，您所指定的字串會成為該來源的名稱。 這個名稱是用來設定 (啟用/停用/設定追蹤層級) 追蹤來源， 同時也會出現在追蹤輸出本身。 自訂通道應該使用唯一來源名稱，以利追蹤輸出的讀取器瞭解該追蹤資訊的來源為何。 使用將資訊寫入成為追蹤來源名稱之組件的名稱是常見的做法。 例如，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 System.ServiceModel 做為從 System.ServiceModel 組件寫入之資訊的追蹤來源。  
  
 有了追蹤來源之後，您可以呼叫其 <xref:System.Diagnostics.TraceSource.TraceData%2A>、<xref:System.Diagnostics.TraceSource.TraceEvent%2A> 或 <xref:System.Diagnostics.TraceSource.TraceInformation%2A> 方法，將追蹤項目寫入到追蹤接聽項中。 針對每一個您寫入的追蹤項目，您都需要將事件的型別分類為 <xref:System.Diagnostics.TraceEventType> 中定義的其中一個事件型別。 這個分類和組態中的追蹤層級設定會判斷追蹤項目是否要輸出到接聽項中。 例如，如果將組態中的追蹤層級設定為 `Warning`，就可以寫入 `Warning`、`Error` 和 `Critical` 追蹤項目，但會封鎖「資訊」和「詳細資訊」項目。 以下是具現化追蹤來源，並且在資訊層級寫出項目的範例：  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  強烈建議您指定自訂通道的唯一追蹤來源名稱，以利追蹤輸出讀取器瞭解輸出的來源。  
  
#### <a name="integrating-with-the-trace-viewer"></a>整合追蹤檢視器  
 您的通道所產生的追蹤可能會在所讀取的格式的輸出[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)使用<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>為追蹤接聽程式。 這並不是身為通道開發人員的您所需要做的事情， 反而是需要在應用程式組態檔中設定這個追蹤接聽項的應用程式使用者 (或是針對應用程式進行疑難排解的人員)，才需要做這件事。 例如，下列組態會從 <xref:System.ServiceModel?displayProperty=nameWithType> 和 `Microsoft.Samples.Udp` 兩者，將追蹤資訊輸出到名為 `TraceEventsFile.e2e` 的檔案中：  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"   
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a>追蹤結構化資料  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> 的 <xref:System.Diagnostics.TraceSource.TraceData%2A> 方法會使用包含在追蹤項目中的一或多個物件。 一般而言，會針對每個物件呼叫 <xref:System.Object.ToString%2A?displayProperty=nameWithType> 方法，並將產生的字串寫入成為追蹤項目的一部分。 使用 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> 輸出追蹤時，您可以將 <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> 當做資料物件傳遞到 <xref:System.Diagnostics.TraceSource.TraceData%2A>。 產生的追蹤項目包括 <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType> 所提供的 XML。 以下示範包含 XML 應用程式資料的項目：  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"   
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord   
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 追蹤檢視器會瞭解先前所示之 `TraceRecord` 項目的結構描述，並且從其子項目擷取資料，然後以表格格式顯示。 在追蹤結構化應用程式資料時，您的通道應該要使用此結構描述，以利 Svctraceviewer.exe 使用者讀取資料。
