---
title: "MSMQ 傳輸 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# MSMQ 傳輸
本主題會列出 MSMQ 傳輸產生的所有例外狀況。  
  
## 例外狀況清單  
  
|資源程式碼|資源字串|  
|-----------|----------|  
|MsmqActiveDirectoryRequiresNativeTransfer|訊息的繫結驗證失敗。用戶端無法傳送訊息。此失敗是由於繫結屬性中的衝突所造成。UseActiveDirectory 設定為 true，而 QueueTransferProtocol 設定為 Native。若要解決衝突，請更正其中一個屬性。|  
|MsmqAuthNoneRequiresProtectionNone|服務的繫結驗證失敗。無法啟動服務端點或用戶端。此失敗是由於繫結屬性中的衝突所造成。MsmqAuthenticationMode 設定為 None，但 MsmqProtectionLevel 未設定為 None。若要解決衝突，請更正其中一個屬性。|  
|MsmqCustomRequiresPerAddDLQ|訊息的繫結驗證失敗。用戶端無法傳送訊息。DeadLetterQueue 設定為 Custom，但未指定 CustomDeadLetterQueue。請為 CustomDeadLetterQueue 屬性中的每個應用程式指定寄不出的信件佇列之 URI。|  
|MsmqDeserializationError|將訊息還原序列化時發生錯誤。無法接收訊息，並捨棄訊息。|  
|MsmqDLQNotWriteable|用戶端的繫結驗證失敗。用戶端無法傳送訊息。指定的寄不出的信件佇列不存在或無法寫入。請確定佇列存在，且有適當的權限可寫入。|  
|MsmqGetPrivateComputerInformationError|版本檢查失敗，因為發生指定的錯誤。無法偵測 MSMQ 的版本。佇列通道上的所有作業將會失敗。請確定已安裝 MSMQ，且可供使用。|  
|MsmqNoAssurancesForVolatile|服務的繫結驗證失敗。無法啟動服務端點或用戶端。ExactlyOnce 屬性設定為 true，而 Durable 屬性設定為 false。不支援此一狀況。若要解決衝突，請更正其中一個屬性。|  
|MsmqNonTransactionalQueueNeeded|偵測到繫結與 MSMQ 佇列組態不符。無法啟動服務端點。ExactlyOnce 屬性設定為 false，且讀取訊息的來源佇列為交易式佇列。若要更正錯誤，請將 ExactlyOnce 屬性設為 true，或建立非交易式繫結。|  
|MsmqOpenError|開啟指定的佇列時發生錯誤。無法從佇列傳送或接收訊息。請確定 MSMQ 已安裝且在執行中。同時，請確定佇列可供使用，且能以必要的存取模式和授權來開啟。|  
|MsmqPathLookupError|將指定的佇列路徑名稱轉換成格式名稱時發生錯誤。佇列通道上的所有作業失敗。請確定佇列位址有效。必須在啟用並能存取 Active Directory 整合的情況下安裝 MSMQ。|  
|MsmqPerAppDLQRequiresCustom|用戶端上的繫結驗證失敗。用戶端無法傳送訊息。已設定 CustomDeadLetterQueue 屬性，但 DeadLetterQueue 屬性未設定為 Custom。請將 DeadLetterQueue 屬性設定為 Custom。|  
|MsmqPerAppDLQRequiresExactlyOnce|用戶端的繫結驗證失敗。用戶端無法傳送訊息。此失敗是由於繫結屬性中的衝突所造成。若要使用自訂寄不出的信件佇列，ExactlyOnce 必須設定為 true，才能解決衝突。|  
|MsmqPerAppDLQRequiresMsmq4|偵測到繫結與 MSMQ 組態不符。用戶端無法傳送訊息。若要使用自訂寄不出的信件佇列，必須具有 MSMQ 4.0 或更新的版本。若無 MSMQ 4.0 或更新的版本，請將 DeadLetterQueue 屬性設定為 System 或 None。|  
|MsmqReceiveError|從佇列接收訊息時發生錯誤。請確定 MSMQ 已安裝且在執行中。同時，請確定有可供接收的佇列。|  
|MsmqSameTransactionExpected|此工作階段發生交易錯誤。工作階段通道發生錯誤。無法傳送或接收工作階段中的訊息。佇列工作階段無法與一個以上的交易產生關聯。請確定使用單一交易來傳送或接收工作階段中的所有訊息。|  
|MsmqSendError|傳送至指定的佇列時發生錯誤。請確定 MSMQ 已安裝且在執行中。若是傳送至本機佇列，請確定佇列存在並具有必要的存取模式與授權。|  
|MsmqTimeSpanTooLarge|訊息存留時間過長。無法傳送訊息。訊息存留時間 \(TTL\) 不可超過 Int32 最大值。|  
|MsmqTokenProviderNeededForCertificates|找不到 X509SecurityTokenProvider。無法傳送訊息。憑證驗證模式需要 X.509 權杖提供者。請確定為已安裝的憑證提供可用的安全性權杖提供者。|  
|MsmqTransactedDLQExpected|繫結與 MSMQ 組態不相符。無法傳送訊息。繫結中指定的自訂寄不出的信件佇列必須是交易式佇列。請確定自訂寄不出的信件佇列位址正確，且佇列為交易式佇列。|  
|MsmqTransactionalQueueNeeded|繫結與 MSMQ 佇列組態不符。無法啟動服務端點。ExactlyOnce 屬性設定為 true，但讀取訊息的來源佇列不是交易式佇列。若要更正錯誤，請將 ExactlyOnce 屬性設定為 false，或為此繫結建立交易式佇列。|  
|MsmqTransactionCurrentRequired|工作階段中沒有交易可供傳送訊息。若要傳送佇列工作階段中的訊息，需要交易。請確定工作階段中已指定傳送訊息的交易範圍。|  
|MsmqTransactionRequired|需要交易，但沒有可用的交易。無法傳送或接收訊息。請確定已指定傳送或接收訊息的交易範圍。|  
|MsmqUnsupportedSerializationFormat|發生還原序列化錯誤。無法接收訊息，並捨棄訊息。不支援指定的序列化格式。|  
|MsmqWrongPrivateQueueSyntax|URL 無效。佇列的 URL 不可包含 '$' 字元。請使用 net.msmq:\/\/machine\/private\/queueName 中的語法，來定址私用佇列。|