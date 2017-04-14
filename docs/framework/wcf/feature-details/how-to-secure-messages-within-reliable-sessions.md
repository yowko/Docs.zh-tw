---
title: "HOW TO：保護可靠工作階段內的訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# HOW TO：保護可靠工作階段內的訊息
本主題概要說明透過其中一個系統提供的繫結 \(此繫結支援此類工作階段，但非預設\) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。您可以命令式程式碼或宣告式組態檔來啟用安全、可靠的工作階段。此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。  
  
 此程序包含下列三項主要工作：  
  
1.  指定用戶端與服務在可靠工作階段中交換訊息。  
  
2.  可靠工作階段中需要訊息層級的安全性。  
  
3.  指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。  
  
 在第一個工作中，端點組態項目所包含 `bindingConfiguration` 屬性必須參考名為 "MessageSecurity" \(適用本範例\) 的繫結組態。[\<繫結\>](../../../../docs/framework/misc/binding.md) 組態項目可以接著參考此名稱並將 [reliableSession](http://msdn.microsoft.com/zh-tw/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 項目的 `enabled` 屬性設為 `true` 來啟用可靠工作階段。您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。  
  
 如需此組態程序的原始檔範例，請參閱 [WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。  
  
 您可以將 \<`security`\> 項目 \(包含在用戶端與服務的 \<`binding`\> 項目中\) 的 `mode` 屬性設為 `Message`，來完成第二項工作中的重要項目。  
  
 您可以將 \<`message`\> 項目 \(包含在用戶端與服務的 \<`security`\> 項目中\) 的 `clientCredentialType` 屬性設為 `Certificate`，來完成第三項工作中的重要項目。  
  
> [!NOTE]
>  在使用包含可靠工作階段的訊息安全性時，如果用戶端並未通過驗證，可信賴傳訊就會持續嘗試驗證用戶端，直到發生逾時為止，而不是在第一次失敗時就擲回例外狀況。  
  
### 若要將包含 WSHttpBinding 的服務設為使用可靠工作階段  
  
1.  這個程序會於 [HOW TO：在可靠的工作階段內交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)中說明。  
  
### 若要將包含 WSHttpBinding 的用戶端設為使用可靠工作階段  
  
1.  這個程序會於 [HOW TO：在可靠的工作階段內交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)中說明。  
  
### 若要在組態中設定模式與 ClientCredentialType 屬性  
  
1.  將適當的繫結項目新增至組態檔的 [\<繫結\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 項目中。下列範例會新增 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 項目。  
  
2.  新增 \<`binding`\> 項目，並將它的 `name` 屬性設為適當值。  
  
3.  加入 `<security>` 項目，然後將 `mode` 屬性設為 `Message`。  
  
     下列範例會將模式設為 `Message`，然後將 \<`message`\> 項目的 `clientCredentialType` 屬性設為 `Certificate`。  
  
    ```  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = " Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```