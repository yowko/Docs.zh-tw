---
ms.openlocfilehash: 3506653bfc749ae3d8002715ca72ca89de7a681b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91024800"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>如果 addressHeader 項目為 Null，WCF AddressHeaderCollection 現在會擲回 ArgumentException

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.1 開始，如果其中一個項目是 `null`，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 建構函式會擲回 <xref:System.ArgumentException>。 在 .NET Framework 4.7 和舊版中，不會擲回任何例外狀況。

#### <a name="suggestion"></a>建議

如果您在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以將下列程式程式碼新增至 app.config 檔的區段，以退出宣告 `<runtime>` ：

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>
```

| Name    | 值   |
|:--------|:--------|
| 範圍   | Minor   |
| 版本 | 4.7.1   |
| 類型    | 執行階段 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
