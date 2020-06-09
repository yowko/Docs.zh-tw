---
title: HOW TO：保護可靠工作階段內的訊息
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596951"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>HOW TO：保護可靠工作階段內的訊息

本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。 在設定檔中使用程式碼或以宣告方式啟用安全可靠的會話。 此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。

此程序包含下列三項主要工作：

1. 指定用戶端與服務在可靠工作階段中交換訊息。

1. 可靠工作階段中需要訊息層級的安全性。

1. 指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。

在第一個工作中，端點設定元素包含參考名為之系結設定的 `bindingConfiguration` 屬性（在此範例中為），這一點很重要 `MessageSecurity` 。 [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)然後，configuration 元素會參考此名稱，藉由將專案的屬性設定為來啟用可靠會話 `enabled` [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true` 。 您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。

如需以此設定程式為基礎之範例的來源複本，請參閱[WS 可靠會話](../samples/ws-reliable-session.md)。

第二個工作的基本專案是藉由將 `mode` **\<security>** 用戶端和服務之專案中包含的元素屬性設定 **\<binding>** 為來完成 `Message` 。

第三個工作的基本專案是藉由將 `clientCredentialType` **\<message>** 用戶端和服務的元素中包含之專案的屬性設定 **\<security>** 為來完成 `Certificate` 。

> [!NOTE]
> 在可靠會話中使用訊息安全性時，可靠的訊息會嘗試驗證未經驗證的用戶端，直到發生超時，而不是在第一次失敗時擲回例外狀況。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>以 WSHttpBinding 設定服務以使用可靠會話

此程式的說明請參閱[如何：在可靠會話中交換訊息](how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>以 WSHttpBinding 設定用戶端以使用可靠會話

此程式的說明請參閱[如何：在可靠會話中交換訊息](how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>設定中的模式和 ClientCredentialType

1. 將適當的繫結項目新增至 [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的元素。 下列範例會加入 [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) 元素。

1. 新增專案 **\<binding>** ，並將其 `name` 屬性設定為適當的值。 此範例使用名稱 `MessageSecurity` 。

1. 加入 **\<security>** 元素，並將 `mode` 屬性設定為 `Message` 。

1. 在 **\<security>** 元素內，加入專案， **\<message>** 並將 `clientCredentialType` 屬性設定為 `Certificate` 。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
