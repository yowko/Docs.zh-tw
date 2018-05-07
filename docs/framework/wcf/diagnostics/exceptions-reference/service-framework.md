---
title: 服務架構
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="service-framework"></a>服務架構
此主題會列出服務架構資料產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|繫結執行個體已經加以關聯，以接聽指定的統一資源識別元。 如果兩個端點想要共用相同的 ListenUniform 資源指示器，則它們也必須共用相同的繫結物件執行個體。 兩個衝突的端點會在 AddServiceEndpoint() 呼叫、組態檔或 AddServiceEndpoint() 呼叫與組態的組合中加以指定。|  
|AChannelServiceEndpointIsNull0|通道或服務端點為 Null。|  
|AChannelServiceEndpointSContractSNameIsNull0|通道/服務端點合約名稱為 Null 或空的。|  
|AChannelServiceEndpointSContractSNamespace0|通道/服務端點合約命名空間為 Null。|  
|BaseAddressCannotHaveFragment|起始位址無法包含統一資源識別元片段。|  
|BaseAddressCannotHaveQuery|起始位址無法包含統一資源識別元查詢字串。|  
|BaseAddressCannotHaveUserInfo|起始位址無法包含統一資源識別元使用者資訊區段。|  
|BaseAddressDuplicateScheme|此集合已包含具有指定配置的位址。 在此集合中，每個配置只允許一個位址。|  
|BaseAddressMustBeAbsolute|只有一個絕對的統一資源識別元可以用來當做起始位址。|  
|BindingDoesnTSupportAnyChannelTypes1|指定的繫結不支援建立任何通道類型。 自訂繫結中的繫結項目堆疊方式有誤或堆疊順序不正確。 傳輸是堆疊最下方的必要項。 繫結程序項目的建議順序為：TransactionFlow、ReliableSession、Security、CompositeDuplex、OneWay、StreamSecurity、MessageEncoding、Transport。|  
|BindingDoesnTSupportDuplexButContractRequires1|合約需要 Duplex。 指定的繫結不支援它，或是未正確設定來支援它。|  
|BindingDoesnTSupportOneWayButContractRequires1|合約需要 OneWay。 指定的繫結不支援它，或是未正確設定來支援它。|  
|BindingDoesnTSupportRequestReplyButContract1|合約需要 Request/Reply。 指定的繫結不支援它，或是未正確設定來支援它。|  
|BindingDoesnTSupportSessionButContractRequires1|合約需要 Session。  指定的繫結不支援它，或是未正確設定來支援它。|  
|BindingDoesnTSupportTwoWayButContractRequires1|合約需要 Two-Way (可以是要求-回覆或雙工)。 指定的繫結不支援它，或是未正確設定來支援它。|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute 不允許 QueuedDelivery。 內含指定之合約的端點繫結支援它。|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute 需要 QueuedDelivery。 內含指定之合約的端點繫結不支援它，或是並未正確設定來支援它。|  
|channelDoesNotHaveADuplexSession0|目前通道不支援關閉輸出工作階段。 此通道未實作 ISessionChannel\<IDuplexSession >。|  
|ClientRuntimeRequiresFormatter0|指定的 ClientOperation 需要格式器，因為 SerializeRequest 與 DeserializeReply 並非同為 false。|  
|CommunicationObjectAborted1|由於指定的通訊物件已停止，因此無法用來通訊。|  
|CommunicationObjectAbortedStack2|指定的通訊物件無法用於通訊，因為它已停止： {1}|  
|CommunicationObjectBaseClassMethodNotCalled|指定的通訊物件已覆寫虛擬函式{1}但未呼叫基底類別中定義的版本。|  
|ContractIsNotSelfConsistentItHasOneOrMore2|指定的合約具有一或多個 IsTerminating 或 non-IsInitiating 作業。 它並未將 SessionMode 屬性設為 SessionMode.Required。 IsInitiating 和 IsTerminating 屬性只能用在工作階段內容中。|  
|CouldnTCreateChannelForChannelType2|已要求指定的通道類型，但是指定的繫結不支援它或是未正確設定來支援它。|  
|DispatchRuntimeRequiresFormatter0|指定的 DispatchOperation 需要格式器，因為 DeserializeRequest 和 SerializeReply 並非同為 false。|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|使用 IAsyncResult 設計模式時，不可將 End 方法與 OperationContractAttribute 一起使用。 只有對應的 Begin 方法可以和 OperationContractAttribute 一起使用。 該屬性會套用至方法的 Begin-End 配對。|  
|EndpointListenerRequirementsCannotBeMetBy3|由於合約需要對這些指定的通道類型之一提供支援，指定之繫結的 IChannelListener 將無法滿足 ChannelDispatcher 需求。 但是繫結僅支援這些指定的通道類型。|  
|EndpointsMustHaveAValidBinding0|端點必須具備有效繫結。|  
|InvalidOrUnrecognizedAction|因為指定的動作無效或無法辨識，因此無法處理訊息。|  
|MultipleMebesInParameters|在 BindingContext 的 BindingParameters 中找到一個以上的 MessageEncodingBindingElement。 CustomBinding 無法包含多個 MessageEncodingBindingElements。 請移除全部項目，只留下其中一個項目。|  
|MultipleStreamUpgradeProvidersInParameters|在 BindingContext 的 BindingParameters 中找到一個以上的 IStreamUpgradeProviderElement。 CustomBinding 只能包含一個 IStreamUpgradeProviderElements。 請移除全部項目，只留下其中一個項目。|  
|NoChannelBuilderAvailable|由於繫結並未包含 TransportBindingElement，因此無法用來建立通道處理站或通道接聽項。 每一個繫結都至少必須有一個衍生自 TransportBindingElement 的繫結項目。|  
|NotAllBindingElementsBuilt|在建置通道處理站與通道接聽項時，並未採用此繫結中的某些繫結項目。 繫結項目的順序不正確。 繫結程序項目的建議順序為：TransactionFlow、ReliableSession、Security、CompositeDuplex、OneWay、StreamSecurity、MessageEncoding、Transport。  請注意，TransportBindingElement 必須排在最後一個。 尚未建置指定的繫結項目。|  
|RuntimeRequiresInvoker0|分派作業需要 Invoker。|  
|ServiceHasZeroAppEndpoints|指定的 Service 不包含應用程式 (非基礎結構) 端點。 這是因為找不到應用程式的任何組態檔，或者因為組態檔中找不到任何符合服務名稱的服務項目，又或因為服務項目中未定義任何端點所導致。|  
|SFxActionMismatch|因為動作不符而無法建立具型別的訊息。 預期發生指定的動作但卻發生另一個動作。|  
|SFxAnonymousTypeNotSupported|由於指定之訊息中的指定部分為匿名類型，因此無法使用 RPC 來匯出，或是進行編碼。|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|運用組態區段中 serviceMetadata 區段的 ExternalMetadataLocation 屬性 (Property) 或 externalMetadataLocation 屬性 (Attribute) 提供給 ServiceMetadataBehavior 的 URL 是一種相對 URL，而且沒有可用來加以解析的起始位址。|  
|SFxBadMetadataMustBePolicy|必須提供具有指定之命名空間與名稱的原則 XmlElement。 此 XmlElement 具有指定的命名空間與名稱。|  
|SFxBodyObjectTypeCannotBeInherited|指定的類型無法從任何類別繼承，只能繼承自將做為 RPC 樣式之本文物件來使用的物件。|  
|SFxBodyObjectTypeCannotBeInterface|指定的類型會實作指定的介面，但是 RPC 樣式的內文物件不支援此介面。|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute 只能在端點上透過雙工合約，當做行為來執行。 指定的合約不是雙工，而且未包含任何回呼作業。|  
|SFxCallbackRequestReplyInOrder1|在目前的訊息處理完畢之前，無法從此作業接收回覆。 若要允許不按照順序的訊息處理，請在指定項目上將 ConcurrencyMode 指定為 Reentrant 或 Multiple。|  
|SfxCallbackTypeCannotBeNull|為了搭配 DuplexChannelFactory 來使用指定的合約，合約必須指定有效的回呼合約。 如果您的合約不具有回呼合約，請使用 ChannelFactory 而不要使用 DuplexChannelFactory。|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient 只能從 HTTP 與 HTTPS MetadataLocations 取得中繼資料。 它無法從指定項目中取得中繼資料。|  
|SFxCannotHttpGetMetadataFromAddress|當 MetadataExchangeClient 使用 MetadataExchangeClientMode HttpGet 時，只能從 HTTP 或 HTTPS 位址取得中繼資料。 它無法從指定項目中取得中繼資料。|  
|SFxCannotImportAsParameters_Bare|由於指定的作業既不是 RPC 也不是包裝的文件，正在產生訊息合約。|  
|SFxCannotImportAsParameters_DifferentWrapperName|由於指定之訊息的包裝函式名稱不符合預設值，正在產生訊息合約。|  
|SFxCannotImportAsParameters_DifferentWrapperNs|由於指定之訊息的包裝函式命名空間不符合預設值，正在產生訊息合約。|  
|SFxCannotImportAsParameters_ElementIsNotNillable|由於指定之命名空間的指定項目名稱未標示為 nillable，正在產生訊息合約。|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|由於指定的訊息具有標頭，正在產生訊息合約。|  
|SFxCannotImportAsParameters_Message|由於指定的作業以不具型別的訊息做為引數或傳回型別，正在產生訊息合約。|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|由於指定的訊息需要保護，正在產生訊息合約。|  
|SFxCannotImportAsParameters_NamespaceMismatch|由於指定之訊息的部分命名空間不符合預設值，正在產生訊息合約。|  
|SFxCannotRequireBothSessionAndDatagram3|指定的合約會指定 SessionMode.NotAllowed，而指定的合約會指定 SessionMode.Required。 為每個端點變更其中一個 SessionMode 值或指定不同的位址或是 ListenURI。|  
|SFxCannotSetExtensionsByIndex|此集合不支援按索引來設定延伸。 請使用 InsertItem 或 RemoveItem 方法。|  
|SFxChannelDispatcherDifferentHost0|ChannelDispatcher 目前並未附加到所提供的 ServiceHost。|  
|SFxChannelDispatcherMultipleHost0|ChannelDispatcher 無法新增至一個以上的 ServiceHost。|  
|SFxChannelDispatcherNoHost0|ChannelDispatcher 無法開啟，因為尚未附加到 ServiceHost。|  
|SfxChannelFactoryDisposed|此 ChannelFactory 無法開啟，因為已經處置 ChannelFactory。 在使用 ChannelFactory 之前再建立它一次。|  
|SFxChannelFactoryNoBinding|無法開啟 ChannelFactory，因為尚未將繫結與其端點相關聯。 使用建構函式或端點屬性來指定繫結。|  
|SFxChannelTerminated0|已在此通道上叫用標示為 IsTerminating 的作業，導致通道連線終止。 無法在此通道上再叫用任何作業。 請重新建立通道來繼續通訊。|  
|SFxCloseTimedOut1|在指定項目之後，停止 ServiceHost 關閉作業。 這可能是因為用戶端無法在要求的時間內關閉工作階段通道所造成。 分配給此作業的時間，可能是較長逾時的一部分。|  
|SfxCloseTimedOutWaitingForDispatchToComplete|關閉處理序在等待服務分派完成時逾時。|  
|SFxCodeGenIsNotAssignableFrom|無法指派指定的項目。|  
|SFxConfigChannelConfigurationNotFound|在 ServiceModel 用戶端組態區段中找不到使用指定之名稱與合約的端點項目。|  
|SFxConflictingGlobalElement|在指定的命名空間中，具有指定名稱的最上層可延伸標記語言 (XML) 項目無法參考指定的類型。 它已經參考了不同類型。 使用不同的作業名稱或 MessageBodyAttribute，為訊息或訊息部分指定不同的名稱。|  
|SFxContractHasZeroInitiatingOperations|合約至少必須包含一個 IsInitiating=true 作業。|  
|SFxContractHasZeroOperations|合約至少必須包含一個作業。|  
|SFxContractInheritanceRequiresInterfaces|指定之類型的服務類別會定義 ServiceContract 並從指定的類型繼承 ServiceContract。 合約繼承僅能用於介面類型。 如果類別標示為 ServiceContractAttribute，則它必須是階層架構中具有 ServiceContractAttribute 的唯一類型。  請將指定之類型上的 ServiceContractAttribute 移至指定之類型所實作的個別介面上。|  
|SFxCreateDuplexChannel1|指定之合約的回呼合約既不存在，也無法定義任何作業。 如果這不是一份雙工合約，請使用 ChannelFactory，而不要使用 DuplexChannelFactory。|  
|SFxCreateDuplexChannelNoCallback|這個 CreateChannel 多載無法在這個 DuplexChannelFactory 的執行個體上呼叫。 DuplexChannelFactory 並未使用 InstanceContext 來初始化。 呼叫採用 InstanceContext 的 CreateChannel 多載。|  
|SFxCreateDuplexChannelNoCallback1|這個 CreateChannel 多載無法在這個 DuplexChannelFactory 的執行個體上呼叫。 DuplexChannelFactory 使用 Type 來初始化，且未提供有效的 InstanceContext。 呼叫採用 InstanceContext 的 CreateChannel 多載。|  
|SFxCreateDuplexChannelNoCallbackUserObject|這個 CreateChannel 多載無法在這個 DuplexChannelFactory 的執行個體上呼叫。 提供給 DuplexChannelFactory 的 InstanceContext 未包含有效的 UserObject。|  
|SFxCreateNonDuplexChannel1|ChannelFactory 不支援指定的合約。 ChannelFactory 使用一或多項作業來定義回呼合約。 請使用 DuplexChannelFactory，而不要使用 ChannelFactory。|  
|SFxCustomBindingNeedsTransport1|ServiceEndpoint 上具有指定之合約的 CustomBinding 未包含 TransportBindingElement。 每一個繫結都至少必須有一個衍生自 TransportBindingElement 的繫結項目。|  
|SFxCustomBindingWithoutTransport|無法計算此自訂繫結的 Scheme，因為此自訂繫結缺少 TransportBindingElement。 每一個繫結都至少必須有一個衍生自 TransportBindingElement 的繫結項目。|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer 不支援指定之項目上所指定的集合。|  
|SFxDictionaryIsEmpty|字典空白，因此無法執行作業。|  
|SFxDocEncodedNotSupported|反映指定項目的錯誤。 不支援 Document-Encoded。 請將 'Use' 變更為 Literal 或將 'Style' 變更為 RPC。|  
|SFxDuplicateInitiatingActionAtSameVia|此服務中有多個端點在指定項目上接聽。 這些端點共用相同的指定初始化動作。 由於發送器無法判斷處理訊息所需的正確端點，因此會捨棄具有此動作的訊息。|  
|SFXEndpointBehaviorUsedOnWrongSide|指定的 IEndpointBehavior 無法用在伺服器上。 此行為只能套用到用戶端。|  
|SFxEndpointNoMatchingScheme|找不到符合具有指定繫結之端點的指定配置的起始位址。 已指定註冊的起始位址配置。|  
|SFxErrorCreatingMtomReader|建立訊息傳輸最佳化機制訊息的讀取器時發生錯誤。|  
|SFxErrorDeserializingFault|伺服器傳回一個無效的簡單物件存取通訊協定錯誤。 如需詳細資訊，請參閱 InnerException。|  
|SFxErrorDeserializingHeader|還原序列化指定之訊息的其中一個標頭時發生錯誤。 如需詳細資訊，請參閱 InnerException。|  
|SFxErrorReflectingOnMethod3|在指定的方法上以指定的類型載入指定屬性時發生錯誤。  如需詳細資訊，請參閱 InnerException。|  
|SFxErrorReflectingOnParameter4|在指定之方法的指定參數上以指定的類型載入指定屬性時發生錯誤。 如需詳細資訊，請參閱 InnerException。|  
|SFxErrorReflectingOnType2|在指定的類型上載入指定屬性時發生錯誤。  如需詳細資訊，請參閱 InnerException。|  
|SFxErrorSerializingBody|序列化指定之訊息的本文時發生錯誤。 如需詳細資訊，請參閱 InnerException。|  
|SFxErrorSerializingHeader|序列化指定之訊息的其中一個標頭時發生錯誤。 如需詳細資訊，請參閱 InnerException。|  
|SFxExpectedIMethodCallMessage|內部錯誤。 訊息必須是有效的 IMethodCallMessage。|  
|SFxExportMustHaveType|由於指定之作業中的指定部分未包含有效的 CLR 類型，因此無法匯出。|  
|SFxHeaderNotUnderstood|訊息尚未處理。 來自指定之命名空間的指定標頭無法被此訊息的收件者所理解。 此錯誤通常表示此訊息的寄件人已啟用接收者無法處理的通訊協定。 請確定用戶端繫結的組態與服務的繫結一致。|  
|SFxHeadersAreNotSupportedInEncoded|指定的訊息不可具有遠端程序呼叫編碼樣式中所使用的標頭。|  
|SFxInconsistentWsdlOperationStyleInMessageParts|指定之作業中的所有訊息部分必須包含類型或項目。|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|從指定之作業中的訊息推斷的指定樣式與透過繫結指定的預期樣式不符。|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult 尚未提供或為錯誤的類型。|  
|SFxInvalidMessageBody|OperationFormatter 發生無效的訊息本文。 預期具有指定之名稱與命名空間的 'Element' 節點類型。 找到具有指定之名稱與命名空間的指定節點類型。|  
|SFxInvalidMessageBodyEmptyMessage|OperationFormatter 無法還原序列化任何來自訊息的資訊，因為訊息是空的。|  
|SFxInvalidMessageBodyErrorDeserializingParameter|嘗試還原序列化指定的參數時發生錯誤。 如需詳細資訊，請參閱 InnerException。|  
|SFxInvalidMessageBodyErrorSerializingParameter|嘗試序列化指定的參數時發生錯誤。 已指定 InnerException 訊息。  如需詳細資訊，請參閱 InnerException。|  
|SFxInvalidMessageBodyUnexpectedNode|還原序列化參數時，發生來自指定命名空間之指定的未預期節點。|  
|SFxInvalidMessageContractSignature|指定的作業可能包含參數，或是標示為 MessageContractAttribute 的傳回型別。 使用訊息合約來代表要求訊息時，作業必須具有標示為 MessageContractAttribute 的單一參數。 使用訊息合約來代表回應訊息時，作業的傳回值必須是標示為 MessageContractAttribute 的類型。 作業不可具有任何 'out' 或 'ref' 參數。|  
|SFxInvalidReplyAction|作業的傳出回覆訊息已經指定 Action，但是該作業的合約卻指定另一個 ReplyAction。 訊息中指定的 Action 必須符合合約中的 ReplyAction，或者作業合約必須指定 ReplyAction='*'。|  
|SFxInvalidRequestAction|作業的傳出要求訊息已經指定 Action，但是該作業的合約卻指定另一個 RequestAction。 訊息中指定的 Action 必須符合合約中的 RequestAction，或者作業合約必須指定 RequestAction='*'。|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|靜態 CreateChannel 方法不能與指定的合約一起使用，因為該合約會定義回呼合約。 使用其中一個靜態 CreateChannel 多載上 DuplexChannelFactory\<TChannel >。|  
|SFxInvalidStreamInRequest|若要讓指定之作業中的要求成為資料流，作業必須包含 Stream 類型的單一參數。|  
|SFxInvalidStreamInResponse|若要讓指定之作業中的回應成為資料流，作業必須包含 Stream 類型的單一 out 參數或傳回值。|  
|SFxInvalidStreamInTypedMessage|若要使用資料流來搭配 Message Contract 程式設計模型，指定的類型必須包含 Stream 類型的單一 MessageBody 成員。|  
|SFxInvalidUseOfPrimitiveOperationFormatter|PrimitiveOperationFormatter 被指定了本身不支援的參數或傳回值。|  
|SFxMessageContractBaseTypeNotValid|指定的類型會定義 MessageContract 並衍生自無法定義 MessageContract 的指定類型。 指定之繼承階層架構中的所有物件都必須定義 MessageContract。|  
|SFxMethodNotSupported1|此物件不支援指定的方法。 如果方法未標示為 OperationContractAttribute 或者如果介面類型未標示為 ServiceContractAttribute，就可能發生這種情況。|  
|SFxMethodNotSupportedByType2|指定的 ServiceHost 實作型別無法實作指定的服務合約。|  
|SFxMethodNotSupportedOnCallback1|不支援指定的回呼方法。 如果方法未標示為 OperationContractAttribute 或者如果其介面類型不是 ServiceContractAttribute CallbackContract 的目標，就可能發生這種情況。|  
|SFxMismatchedOperationParent|DispatchOperation 或 ClientOperation 只能各自新增至本身的父代 DispatchRuntime 或 ClientRuntime。|  
|SFxNameCannotBeEmpty|Name 屬性不可以是空字串。|  
|SfxNoTypeSpecifiedForParameter|參數未指定 CLR 類型，以避免產生作業。|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute 只能在服務類別上執行， 無法置於 ServiceContract 介面上。 指定之類型上的指定方法違反此規則。|  
|SFxOperationContractOnNonServiceContract|指定的方法已標示為 OperationContractAttribute，但是內含的指定類型未標示為 ServiceContractAttribute。 OperationContractAttribute 只能用於 ServiceContractAttribute 類型或它們的 CallbackContract 類型的方法上。|  
|SFxParameterCountMismatch|提供的引數數量與預期的引數數量之間出現不符情況。 特別的是，指定的引數包含指定的項目數，而預期的引數則包含指定的項目數。|  
|SFxPartNameMustBeUniqueInRpc|指定的訊息部分名稱在遠端程序呼叫訊息中並不是唯一。|  
|SFxReplyActionMismatch3|已接收到指定之作業 (包含指定的動作) 的回覆訊息。 然而，您的用戶端程式碼需要指定的動作。|  
|SFxRequestReplyNone|收到具有 WS-Addressing ReplyTo 或 FaultTo 標頭，目標為 "None" 位址的訊息。 這些值對於要求-回覆作業無效。 請考慮使用單向作業，或者若需要支援 "None" 的 ReplyTo 或 FaultTo 值，請啟用 ManualAddressing。|  
|SFxRequestTimedOut1|此要求作業未在指定的設定時間內收到回覆。 分配給此作業的時間，可能是較長逾時的一部分。 這可能是因為服務仍然在處理作業，或服務無法傳送回覆訊息。|  
|SFxRequestTimedOut2|傳送至指定之位置的要求作業未在指定的設定時間內收到回覆。 分配給此作業的時間，可能是較長逾時的一部分。 這可能是因為服務仍然在處理作業，或服務無法傳送回覆訊息。|  
|SFxSchemaDoesNotContainType|具有指定之目標命名空間的配置未包含具有指定名稱的類型。|  
|SfxServiceContractAttributeNotFound|指定的合約類型未以 ServiceContractAttribute 賦予屬性。 若要定義有效合約，指定的類型必須以 ServiceContractAttribute 賦予屬性。 此類型可以是合約介面或是服務類別。|  
|SFxServiceContractGeneratorConfigRequired|為了使用 GenerateServiceEndpoint 方法來產生組態資訊，必須以有效 Configuration 物件來初始化 ServiceContractGenerator 執行個體。|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|當 ServiceHost 處於下列其中一種狀態之後，就無法新增端點：<br /><br /> 開啟<br />-發生錯誤<br />終止<br />關閉|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|在初始化 Description 屬性之前，無法新增端點。|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|ServiceMetadataBehavior 的 HttpGetEnabled 屬性已設為 true 而 HttpGetUrl 屬性則是相對位址，但是不包含 HTTP 初始位址。 請提供 HTTP 初始位址，或是將 HttpGetUrl 設為絕對位址。|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|ServiceMetadataBehavior 的 HttpsGetEnabled 屬性已設為 true 而 HttpsGetUrl 屬性則是相對位址，但是不包含 HTTPS 初始位址。 請提供 HTTPS 初始位址，或是將 HttpsGetUrl 設為絕對位址。|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|行為 URL 必須是具有指定配置的相對統一資源識別元或是絕對統一資源識別元。 指定的 URL 是具有指定配置的絕對統一資源識別元。|  
|SFxStreamRequestMessageClosed|已關閉包含此資料流的訊息。 當服務作業傳回後，將無法存取要求資料流。|  
|SFxStreamResponseMessageClosed|已關閉包含此資料流的訊息。|  
|SFxTerminateRequestProcessingException|作業管線中的延伸必須結束處理此訊息。|  
|SFxTerminatingOperationAlreadyCalled1|此通道不會傳送更多的訊息，因為已呼叫 IsTerminating 作業。|  
|SFxThrottleLimitMustBeGreaterThanZero0|節流閥限制必須大於零。 若要停用節流閥限制，請將值設為 Int32.MaxValue。|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|使用 RPC 編碼的樣式時，訊息合約類型或 System.ServiceModel.Channels.Message 類型在作業不包含參數或具有 void 傳回值時將無法使用。 請將空白的訊息合約類型當成參數或傳回型別，新增至指定的作業中。|  
|SFxUserCodeThrewException|指定的使用者作業已擲回使用者程式碼中未處理的例外狀況。 如果這個問題重複發生，可能代表在實作指定的方法時出現錯誤。|  
|SfxUseTypedMessageForCustomAttributes|指定的參數無法對應至作業參數，因為它需要額外的屬性。|  
|SFxVersionMismatchInOperationContextAndMessage2|無法將傳出的標頭新增至訊息，因為 OperationContext.Current 中的 MessageVersion 與正在處理的訊息標頭版本不符。|  
|SFxWellKnownNonSingleton0|若要使用採用服務執行個體的某個 ServiceHost 建構函式，必須將服務的 InstanceContextMode 設為 InstanceContextMode.Single。 您可以透過 ServiceBehaviorAttribute 來進行這項設定。 否則，請使用採用 Type 引數的 ServiceHost 建構函式。|  
|SFxWrapperTypeHasMultipleNamespaces|無法將指定之訊息的包裝函式類型投射為資料合約類型，因為它具有多個命名空間。 請使用 XmlSerializer。|  
|UriMustBeAbsolute|URI 必須是絕對的。|
