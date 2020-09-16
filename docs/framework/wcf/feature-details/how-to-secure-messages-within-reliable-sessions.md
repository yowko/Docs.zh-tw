---
title: 作法：保護可靠工作階段內的訊息
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: cec9356467886be022d05ead55d5cb6ccddcd838
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558676"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>作法：保護可靠工作階段內的訊息

本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。 使用程式碼或以宣告方式在設定檔中啟用安全可靠的會話。 此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。

此程序包含下列三項主要工作：

1. 指定用戶端與服務在可靠工作階段中交換訊息。

1. 可靠工作階段中需要訊息層級的安全性。

1. 指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。

在第一個工作中，端點設定專案所包含的 `bindingConfiguration` 屬性會參考名為 (的屬性，此範例) `MessageSecurity` 。 然後，設定專案會 [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) 參考此名稱，藉由將專案的屬性設定為，來啟用可靠會話 `enabled` [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) `true` 。 您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。

如需此設定程式所依據之範例的來源複本，請參閱 [WS 可靠會話](../samples/ws-reliable-session.md)。

第二個工作的基本專案是藉由將 `mode` **\<security>** 用戶端和服務的元素中包含之專案的屬性（attribute）設定 **\<binding>** 為來完成 `Message` 。

第三個工作的基本專案是藉由將 `clientCredentialType` **\<message>** 用戶端和服務的元素中包含之專案的屬性（attribute）設定 **\<security>** 為來完成 `Certificate` 。

> [!NOTE]
> 使用訊息安全性與可靠會話時，可靠的訊息會嘗試驗證未驗證的用戶端，直到發生超時，而不是在第一次失敗時擲回例外狀況。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>使用 WSHttpBinding 設定服務以使用可靠會話

[如何：在可靠的會話內交換訊息](how-to-exchange-messages-within-a-reliable-session.md)中會說明此程式。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>使用 WSHttpBinding 設定用戶端以使用可靠會話

[如何：在可靠的會話內交換訊息](how-to-exchange-messages-within-a-reliable-session.md)中會說明此程式。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>設定 configuration 中的模式和 ClientCredentialType

1. 將適當的繫結項目新增至 [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的元素中。 下列範例會新增 [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) 元素。

1. 新增 **\<binding>** 元素，並將其 `name` 屬性設定為適當的值。 此範例會使用此名稱 `MessageSecurity` 。

1. 新增 **\<security>** 元素，並將 `mode` 屬性設定為 `Message` 。

1. 在 **\<security>** 元素中，加入專案， **\<message>** 並將 `clientCredentialType` 屬性設定為 `Certificate` 。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
