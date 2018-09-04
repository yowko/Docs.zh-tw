---
title: HOW TO：保護可靠工作階段內的訊息
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1592c9429e6cd425b86fa2b72bfebe977e18b048
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505078"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>HOW TO：保護可靠工作階段內的訊息

本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。 透過命令式程式碼或是宣告式組態檔中，請啟用安全、 可靠工作階段。 此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。

此程序包含下列三項主要工作：

1. 指定用戶端與服務在可靠工作階段中交換訊息。

1. 可靠工作階段中需要訊息層級的安全性。

1. 指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。

請務必在第一個工作中的端點組態項目包含`bindingConfiguration`參考 （在此範例中） 名為繫結組態的屬性`MessageSecurity`。 [ **\<繫結 >** ](../../../../docs/framework/misc/binding.md)組態項目接著會參考此名稱，藉此啟用可靠工作階段`enabled`屬性[  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)項目`true`。 您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。

如需此組態程序為基礎的範例的原始檔複本，請參閱 < [WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。

第二項工作的重要項目藉由設定來完成`mode`的屬性**\<安全性 >** 中所包含的項目**\<繫結 >** 用戶端和服務的項目`Message`。

第三個工作的重要項目藉由設定來完成`clientCredentialType`的屬性**\<訊息 >** 中所包含的項目**\<安全性 >** 用戶端和服務的項目`Certificate`。

> [!NOTE]
> 當使用訊息安全性可靠工作階段，可靠的傳訊嘗試驗證的未驗證的用戶端，而不是擲回的例外狀況，在第一次失敗時，發生逾時之前。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>透過 WSHttpBinding 使用可靠工作階段設定服務

此程序所述[如何： Exchange 訊息在可靠工作階段](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>透過 WSHttpBinding 使用可靠工作階段設定的用戶端

此程序所述[如何： Exchange 訊息在可靠工作階段](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>在組態中設定模式與 clientcredentialtype 屬性

1. 加入至適當的繫結項目[ **\<繫結 >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)組態檔的項目。 下列範例會將[  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。

1. 新增**\<繫結 >** 項目並將其`name`屬性設為適當的值。 此範例會使用名稱`MessageSecurity`。

1. 新增**\<安全性 >** 項目並將`mode`屬性設定為`Message`。

1. 內**\<安全性 >** 項目，新增**\<訊息 >** 項目並將`clientCredentialType`屬性設定為`Certificate`。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
