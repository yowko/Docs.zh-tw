---
title: HOW TO：保護可靠工作階段內的訊息
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141673"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>HOW TO：保護可靠工作階段內的訊息

本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。 在設定檔中使用程式碼或以宣告方式啟用安全可靠的會話。 此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。

此程序包含下列三項主要工作：

1. 指定用戶端與服務在可靠工作階段中交換訊息。

1. 可靠工作階段中需要訊息層級的安全性。

1. 指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。

在第一個工作中，端點設定元素包含參考名為之系結設定（在此範例中為） `MessageSecurity`的 `bindingConfiguration` 屬性，這一點很重要。 \<系結[ **>** ](../../configure-apps/file-schema/wcf/bindings.md) configuration 專案接著會參考此名稱，藉由將[ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))專案的 `enabled` 屬性設定為 [`true`] 來啟用可靠會話。 您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。

如需以此設定程式為基礎之範例的來源複本，請參閱[WS 可靠會話](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。

第二個工作的基本專案是藉由將用戶端和服務的\<系結 **>** 元素中所包含之 **\<安全性 >** 專案的 `mode` 屬性設定為 [`Message`] 來完成。

第三個工作的基本專案，就是將用戶端和服務的 **\<security >** 元素中包含的 **\<message >** 元素的 `clientCredentialType` 屬性設定為 `Certificate`。

> [!NOTE]
> 在可靠會話中使用訊息安全性時，可靠的訊息會嘗試驗證未經驗證的用戶端，直到發生超時，而不是在第一次失敗時擲回例外狀況。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>以 WSHttpBinding 設定服務以使用可靠會話

此程式的說明請參閱[如何：在可靠會話中交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>以 WSHttpBinding 設定用戶端以使用可靠會話

此程式的說明請參閱[如何：在可靠會話中交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>設定中的模式和 ClientCredentialType

1. 將適當的繫結項目新增至設定檔的\<系結[ **>** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)元素。 下列範例會將[ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)元素。

1. 將\<系結加入 **>** 元素，並將其 `name` 屬性設定為適當的值。 此範例會使用 `MessageSecurity`的名稱。

1. 新增 **\<安全性 >** 元素，並將 `mode` 屬性設定為 `Message`。

1. 在 **\<安全性 >** 元素中，新增 **\<訊息 >** 專案，並將 `clientCredentialType` 屬性設定為 [`Certificate`]。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
