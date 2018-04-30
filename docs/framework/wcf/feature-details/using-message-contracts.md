---
title: 使用訊息合約
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 600d938b8981ddfabcb79028ae66b5b9d02107b7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="using-message-contracts"></a>使用訊息合約
通常當建置 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式時，程式開發人員會特別注意資料結構與序列化的問題，並且本身不需要考慮傳送資料的訊息結構。 針對這類應用程式，建立參數的資料合約或傳回值是很明確的。 (如需詳細資訊，請參閱[在服務合約中指定資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。)  
  
 但是，有時候完整控制 SOAP 訊息的結構與控制其內容一樣重要。 當互通性很重要，或是要具體控制在訊息層級或訊息部分的安全性問題時，這就顯得特別重要。 在這些情況下，您可以建立*訊息合約*，可讓您指定所需的精確 SOAP 訊息的結構。  
  
 此主題會討論如何使用各種訊息合約屬性，以建立作業的特定訊息合約。  
  
## <a name="using-message-contracts-in-operations"></a>在作業中使用訊息合約  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援在建立模型的作業*遠端程序呼叫 (RPC) 樣式*或*傳訊樣式*。 在 RPC 樣式作業中，您可以使用任何可序列化類型，並且有存取本機呼叫的功能，例如多個參數以及 `ref` 與 `out` 參數。 在這個樣式中，選擇的序列化形式會控制基礎訊息中的資料結構，並且 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段會建立訊息以支援作業。 這可以讓不熟悉 SOAP 和 SOAP 訊息的程式開發人員，快速而輕鬆地建立與使用服務應用程式。  
  
 下列程式碼範例顯示根據 RPC 樣式建立模型的服務作業。  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 通常資料合約已足夠定義訊息的結構描述。 例如，在之前的範例中，如果 `BankingTransaction` 和 `BankingTransactionResponse` 都有定義基礎 SOAP 訊息內容的資料合約，對大部分的應用程式來說就已足夠。 如需資料合約的詳細資訊，請參閱[使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
 但是，偶爾也會需要精確控制透過網路傳輸 SOAP 訊息結構的方式。 最常見的案例是插入自訂 SOAP 標頭。 另一個常見的案例是定義訊息標頭與本文的安全性屬性，也就是決定是否要數位簽署或加密這些項目。 最後，某些協力廠商 SOAP 堆疊會要求訊息使用特定的格式。 訊息樣式作業提供這項控制。  
  
 訊息樣式作業最多只有一個參數和一個傳回值，並且兩者都是訊息類型；也就是它們會直接序列化至指定的 SOAP 訊息結構中。 這可能是使用 <xref:System.ServiceModel.MessageContractAttribute> 或 <xref:System.ServiceModel.Channels.Message> 類型標記的任何類型。 下列程式碼範例顯示類似之前 RCP 樣式的作業，但是使用訊息樣式。  
  
 例如，如果 `BankingTransaction` 和 `BankingTransactionResponse` 都是訊息合約的類型，則下列作業中的程式碼就有效。  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 但是，下列程式碼無效。  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 包含不遵循其中一種有效模式之訊息合約類型的任何作業都會發生例外狀況。 當然，不包含訊息合約類型的作業則不受這些限制。  
  
 如果類型同時是訊息合約與資料合約，當在作業中使用類型時只會考量其訊息合約。  
  
## <a name="defining-message-contracts"></a>定義訊息合約  
 若要定義類型的訊息合約 (也就是定義類型與 SOAP 封套之間的對應)，請將 <xref:System.ServiceModel.MessageContractAttribute> 套用至類型。 然後將 <xref:System.ServiceModel.MessageHeaderAttribute> 套用至想要當做 SOAP 標頭之類型的成員，再將 <xref:System.ServiceModel.MessageBodyMemberAttribute> 套用至想要當做訊息之 SOAP 本文部分的成員。  
  
 下列程式碼提供使用訊息合約的範例。  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 使用這個類型做為作業參數時，會產生下列 SOAP envelope：  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 請注意，`operation` 和 `transactionDate` 會顯示為 SOAP 標頭，而 SOAP 本文是由包含 `BankingTransaction`、`sourceAccount` 和 `targetAccount` 的 `amount` 包裝函式元素所組成。  
  
 您可以將 <xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 套用至所有欄位、屬性和事件 (不論其是否屬於公開、私用、保護或內部)。  
  
 <xref:System.ServiceModel.MessageContractAttribute> 可讓您指定 WrapperName 和 WrapperNamespace 屬性，用來控制 SOAP 訊息本文中包裝函式元素的名稱。 預設訊息合約的名稱類型會使用包裝函式和命名空間定義的訊息合約`HYPERLINK "http://tempuri.org/" http://tempuri.org/`做為預設命名空間。  
  
> [!NOTE]
>  在訊息合約中會忽略 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。 如果需要 <xref:System.Runtime.Serialization.KnownTypeAttribute>，請將其置於使用有問題之訊息合約的作業。  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>控制標頭和本文部分的名稱與命名空間  
 在訊息合約的 SOAP 表示法中，每個標頭和本文部分會對應至擁有名稱與命名空間的 XML 項目。  
  
 根據預設，命名空間與訊息參與之服務合約的命名空間相同，並且名稱是由套用 <xref:System.ServiceModel.MessageHeaderAttribute> 或 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性的成員名稱來判定。  
  
 您可以藉由管理 <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> 和  <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (在  <xref:System.ServiceModel.MessageHeaderAttribute> 和  <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性的父類別上) 以變更這些預設值。  
  
 請考量下列程式碼範例中的類別。  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 在這個範例中，`IsAudited` 標頭在程式碼指定的命名空間內，而表示 `theData` 成員的本文部分則是由名為 `transactionData` 的 XML 項目所表示。 以下顯示本訊息合約產生的 XML。  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>控制是否要包裝 SOAP 本文部分  
 根據預設，SOAP 本文部分會在已包裝的項目內序列化。 例如，下列程式碼顯示產生自 `HelloGreetingMessage` 訊息之訊息合約中，<xref:System.ServiceModel.MessageContractAttribute> 型別名稱的 `HelloGreetingMessage` 包裝函式項目。  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 若要隱藏包裝函式項目，請將 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 屬性設定為 `false`。 若要控制包裝函式項目的名稱與命名空間，請使用 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 和 <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> 屬性。  
  
> [!NOTE]
>  在訊息中如果有一個以上未包裝的訊息本文部分，就不符合 WS-I Basic Profile 1.1 並且不建議在設計新訊息合約時使用。 但是，在某些特定互通性案例中，可能會需要有一個以上未包裝的訊息本文部分。 如果您要在訊息本文中傳輸一段以上的資料，建議您使用預設 (包裝) 模式。 在未包裝訊息中有一個以上的訊息標頭是完全可接受的。  
  
## <a name="using-custom-types-inside-message-contracts"></a>在訊息合約中使用自訂類型  
 每個個別訊息標頭與訊息本文部分，會針對使用訊息的服務合約，使用選擇的序列化引擎進行序列化 (轉變成 XML)。 預設的序列化引擎 `XmlFormatter` 能夠處理擁有資料合約的任何類型，不論是使用明確的方式 (藉由擁有 <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) 或隱含的方式 (藉由成為基本型別、擁有 <xref:System.SerializableAttribute?displayProperty=nameWithType> 等等)。 如需詳細資訊，請參閱[使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
 在之前的範例中，`Operation` 和 `BankingTransactionData` 型別必須擁有資料合約，並且 `transactionDate` 是可序列化的，因為 <xref:System.DateTime> 是基本型別 (並且擁有隱含資料合約)。  
  
 但是，也有可能切換為不同的序列化引擎 `XmlSerializer`。 如果您進行這類切換，就應該確定訊息標頭和本文部分所使用的所有型別都能夠使用 `XmlSerializer` 進行序列化。  
  
## <a name="using-arrays-inside-message-contracts"></a>在訊息合約中使用陣列  
 您可以利用下列兩種方式在訊息合約中使用重複項目的陣列。  
  
 第一個是在陣列上直接使用 <xref:System.ServiceModel.MessageHeaderAttribute> 或 <xref:System.ServiceModel.MessageBodyMemberAttribute>。 在此例中，整個陣列會序列化當做使用多個子項目的單一項目 (也就是單一標頭或單一本文部分)。 請考量下列範例中的類別。  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 SOAP 標頭中的這個結果類似下列所示。  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 其替代方案是使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute>。 在此例中，每個陣列項目會獨立序列化，所以每個陣列項目都有一個標頭，類似下列所示。  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 陣列項目的預設名稱為套用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 屬性的成員名稱。  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 屬性繼承自 <xref:System.ServiceModel.MessageHeaderAttribute>。 它與非陣列屬性擁有相同的功能集合，例如，您可以使用與設定單一標頭相同的方式，設定標頭陣列的順序、名稱與命名空間。 當您在陣列使用 `Order` 屬性時，就會套用至整個陣列。  
  
 您可以將 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 只套用至陣列而不是集合上。  
  
## <a name="using-byte-arrays-in-message-contracts"></a>在訊息合約中使用位元組陣列  
 當搭配非陣列屬性 (<xref:System.ServiceModel.MessageBodyMemberAttribute> 和 <xref:System.ServiceModel.MessageHeaderAttribute>) 使用位元組陣列時，就不會將位元組陣列視為陣列，而是視為在產生之 XML 中以 Base64 編碼之資料表示的特殊基本型別。  
  
 當您搭配陣列屬性 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 使用位元組陣列時，結果會根據所使用的序列化程式而不同。 當使用預設序列化程式時，陣列會以每個位元組的個別項目表示。 但是，當選取 `XmlSerializer` 時 (在服務合約使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute>)，不論是否使用陣列或非陣列屬性，都會將位元組陣列視為 Base64 資料。  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>簽署和加密部分訊息  
 訊息合約可以表示是否應該數位簽署與加密訊息的標頭和/或本文。  
  
 藉由設定 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性 (Attribute) 的 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性 (Property) 可以達到此目的。 這個型別是 <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> 型別的列舉，並且可以設定為 <xref:System.Net.Security.ProtectionLevel.None> (無加密或簽章)、<xref:System.Net.Security.ProtectionLevel.Sign> (只有數位簽章) 或 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (同時使用加密和數位簽章)。 預設值為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>。  
  
 若要讓這些安全性功能運作，您必須正確設定繫結與行為。 如果沒有透過正確的組態 (例如，嘗試在不提供認證的情況下簽署訊息) 使用這些安全性功能，就會在驗證階段發生例外狀況。  
  
 針對訊息標頭，保護層級是針對每一個標頭個別決定的。  
  
 對於訊息本文部分而言，可以將保護層級視為「最低保護層級」。 無論有多少個本文部分，本文都只有一個保護層級。 本文保護層級是由所有本文部分的最高層 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> 屬性設定所決定。 但是，您應該將每個本文部分的保護層級，設定為實際的最低必要保護層級。  
  
 請考量下列程式碼範例中的類別。  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 在這個範例中，`recordID` 標頭不受保護，`patientName` 已經過 `signed`，而 `SSN` 已經過加密並簽署。 至少有一個本文部分 `medicalHistory` 已套用 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>，因此即使註解和診斷本文部分指定較低的保護層級，仍然會加密並簽署整個訊息本文。  
  
## <a name="soap-action"></a>SOAP 動作  
 SOAP 與相關的 Web 服務標準會定義稱為 `Action` 的屬性，可能存在於每個已傳送的 SOAP 訊息中。 作業的 <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> 屬性會控制此屬性的值。  
  
## <a name="soap-header-attributes"></a>SOAP 標頭屬性  
 SOAP 標準會定義下列可能存在於標頭的屬性：  
  
-   `Actor/Role` (在 SOAP 1.1 中為 `Actor`，在 SOAP 1.2 中為 `Role`)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` 或 `Role` 屬性會定義指定標頭想要之節點的統一資源識別元 (URI)。 `MustUnderstand` 屬性會指定處理標頭的節點是否必須識別它。 `Relay` 屬性會指定標頭是否要轉送至下游節點。 除了 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 屬性外，`MustUnderstand` 不會對傳入訊息上的這些屬性執行任何處理，如本主題稍後＜訊息合約版本控制＞一節中所述。 但是，它允許您依需要讀取和寫入這些屬性，如同下列所描述。  
  
 當傳送訊息時，根據預設不會發出這些屬性。 變更這項作業的方法有兩種： 首先，您可以藉由變更 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>、<xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> 屬性 (Property)，使用靜態方式將屬性 (Attribute) 設定為任何需要的值，如下列程式碼範例所示。 (請注意並沒有 `Role` 屬性 (Property)；如果您使用 SOAP 1.2，設定 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> 屬性 (Property) 會發出 `Role` 屬性 (Attribute))。  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 第二種方法是透過程式碼以動態方式控制這些屬性。 您可以藉由將需要的標頭類型包裝在 <xref:System.ServiceModel.MessageHeader%601> 型別中 (請不要將此型別與非泛型版本混淆)，以及同時使用型別與 <xref:System.ServiceModel.MessageHeaderAttribute> 來達到這個目的。 然後可以在 <xref:System.ServiceModel.MessageHeader%601> 使用屬性 (Property) 以設定 SOAP 屬性 (Attribute)，如同下列程式碼範例所示。  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 如果您同時使用動態與靜態控制機制，則靜態設定會用來當做預設，但稍後可以使用動態機制加以覆寫，如同下列程式碼所示。  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 允許您使用動態屬性控制建立重複的標頭，如同下列程式碼所示。  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 在接收端，只能在針對型別中標頭使用 <xref:System.ServiceModel.MessageHeader%601> 類別的情況下，才能讀取這些 SOAP 屬性。 您可以檢查 `Actor` 型別標頭的 `Relay`、`MustUnderstand` 或 <xref:System.ServiceModel.MessageHeader%601> 屬性 (Property)，探索所接收訊息的屬性 (Attribute) 設定。  
  
 當接收到訊息然後傳回訊息時，SOAP 屬性設定只會為 <xref:System.ServiceModel.MessageHeader%601> 型別的標頭而往返。  
  
## <a name="order-of-soap-body-parts"></a>SOAP 本文部分的順序  
 在某些情況下，您會需要控制本文部分的順序。 根據預設，本文項目的順序是依字母順序排列，但是可以透過 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 屬性控制。 這個屬性與 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> 屬性有相同的語意，除了在繼承案例中的行為有所不同 (在訊息合約中，基底型別本文成員不會排序在衍生型別本文成員之前)。 如需詳細資訊，請參閱[資料成員順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)。  
  
 在下列程式碼範例中，`amount` 通常會第一個出現 (因為依字母順序它是第一個)。 但是，<xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> 屬性會將它放在第三位。  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a>訊息合約版本控制  
 您偶爾也會需要變更訊息合約。 例如，新版應用程式可能會將額外的標頭新增至訊息中。 然後當從新版應用程式傳送至舊版時，系統就必須處理額外的標頭；而從舊版傳送至新版時則要處理缺少標頭的狀況。  
  
 下列規則會套用至版本控制標頭：  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不會拒絕處理缺少標頭的狀況—對應的成員則會保留其預設值。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也會忽略未預期的額外標頭。 這個規則的其中一個例外狀況是，如果在傳入 SOAP 訊息中的額外標頭將 `MustUnderstand` 屬性設定為 `true`，在這樣的情況下，因為無法處理必須解讀的標頭而會發生例外狀況。  
  
 訊息本文有類似的版本控制規則：缺少與額外的訊息本文部分都會受到忽略。  
  
## <a name="inheritance-considerations"></a>繼承考量  
 只要基底型別也有訊息合約，訊息合約類型就可以繼承自其他類型。  
  
 當使用繼承自其他訊息合約類型的訊息合約類型建立或存取訊息時，則適用下列規則：  
  
-   繼承階層架構中的所有訊息標頭都會收集在一起，以形成訊息標頭的完整集合。  
  
-   繼承階層架構中的所有訊息本文部分都會收集在一起，以形成完整的訊息本文。 本文部分會根據常用排序規則 (根據 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 屬性，然後再根據字母順序) 進行排序，並且與它們在繼承階層架構中的位置無關。 強烈建議不要在繼承樹狀結構之多個層級中發生訊息本文部分的情況下，使用訊息合約繼承。 如果基底類別和衍生類別使用相同名稱定義標頭或本文部分，則會使用來自最底層類別的成員儲存該標頭或本文部分的值。  
  
 請考量下列程式碼範例中的類別。  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 `PatientRecord` 類別描述使用稱為 `ID` 標頭的訊息。 這個標頭對應至 `personID` 而不是 `patientID` 成員，因為已選擇最底層成員。 因此，在此例中已經用不到 `patientID` 欄位。 訊息本文包含之後跟隨 `diagnosis` 項目的 `patientName` 項目，因為這是依字母順序排列。 請注意，該範例顯示強烈建議不要遵循的模式：基底與衍生訊息合約都有訊息本文部分。  
  
## <a name="wsdl-considerations"></a>WSDL 考慮事項  
 當從使用訊息合約的服務產生 Web 服務描述語言 (WSDL) 合約時，重要的是並非所有訊息合約功能都會反應在產生的 WSDL 中。 請考慮下列各點：  
  
-   WSDL 無法表達標頭陣列的概念。 當使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 建立搭配標頭陣列的訊息時，產生的 WSDL 只會反應一個標頭而不是陣列。  
  
-   產生的 WSDL 文件可能不會反應某些保護層級資訊。  
  
-   WSDL 中產生的訊息類型名稱，與訊息合約類型的類別名稱相同。  
  
-   當您在多個作業中使用相同的訊息合約時，在 WSDL 文件中會產生多個訊息類型。 藉由在後續使用時新增數字 "2"、"3" 等等，可以讓名稱具有唯一性。 當匯回 WSDL 時，會建立多個訊息合約類型，並且除了名稱以外都完全相同。  
  
## <a name="soap-encoding-considerations"></a>SOAP 編碼考量  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以讓您使用舊版的 XML SOAP 編碼樣式，但是不建議使用它。 當使用這個樣式時 (藉由將套用至服務合約之 `Use` 的 `Encoded` 屬性設定為 <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>)，則適用下列其他考量：  
  
-   不支援訊息標頭，這表示屬性 <xref:System.ServiceModel.MessageHeaderAttribute> 和陣列屬性 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 與 SOAP 編碼不相容。  
  
-   如果訊息合約並未包裝，也就是說如果屬性 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 設定為 `false`，訊息合約就只能有一個本文部分。  
  
-   要求訊息合約的包裝函式項目名稱必須符合作業名稱。 對此請使用訊息合約的 `WrapperName` 屬性。  
  
-   回應訊息合約的包裝函式項目名稱必須與後置字元為 'Response' 的作業名稱相同。 對此請使用訊息合約的 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 屬性。  
  
-   SOAP 編碼會保留物件參考。 例如，試想下列程式碼。  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 在使用 SOAP 編碼序列化訊息後，`changedFrom` 和 `changedTo` 並未包含專屬的 `p` 複本，而是指向 `changedBy` 項目內的複本。  
  
## <a name="performance-considerations"></a>效能考量  
 每個訊息標頭和訊息本文部分會各自獨立的序列化。 因此，可以針對每個標頭和本文部分再次宣告相同的命名空間。 若要改善效能，特別是針對在網路上傳輸的訊息大小，可以將多個標頭和本文部分合併至單一標頭或本文部分。 例如，不要使用下列程式碼：  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 使用這段程式碼。  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a>事件架構非同步和訊息合約  
 事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。 這麼做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。  
  
 如果您要接收訊息物件做為 `Result` 屬性，並讓傳回的值做為該物件的屬性，則使用 `/messageContract` 命令選項。 這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。 然後，所有的內部傳回值都成為回應訊息物件的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [設計與實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)
