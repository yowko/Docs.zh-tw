---
ms.openlocfilehash: e8b98e465228afd07432e737bb16aefb1b979973
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770897"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="5f841-101">如果 addressHeader 項目為 Null，WCF AddressHeaderCollection 現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="5f841-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="5f841-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5f841-102">Details</span></span>

<span data-ttu-id="5f841-103">從 .NET Framework 4.7.1 開始，如果其中一個項目是 `null`，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 建構函式會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="5f841-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="5f841-104">在 .NET Framework 4.7 和舊版中，不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5f841-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5f841-105">建議</span><span class="sxs-lookup"><span data-stu-id="5f841-105">Suggestion</span></span>

<span data-ttu-id="5f841-106">如果您在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以將下列程式程式碼新增至 app.config 檔的區段，以退出宣告 `<runtime>` ：</span><span class="sxs-lookup"><span data-stu-id="5f841-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
