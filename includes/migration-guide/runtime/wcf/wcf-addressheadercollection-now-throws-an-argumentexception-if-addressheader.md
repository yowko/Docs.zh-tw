---
ms.openlocfilehash: 200c22a1b83149d833a083365ebb65d0e80bc31a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496352"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="85f83-101">如果 addressHeader 項目為 Null，WCF AddressHeaderCollection 現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="85f83-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="85f83-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="85f83-102">Details</span></span>

<span data-ttu-id="85f83-103">從 .NET Framework 4.7.1 開始，如果其中一個項目是 <code>null</code>，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 建構函式會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="85f83-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="85f83-104">在 .NET Framework 4.7 和舊版中，不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="85f83-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85f83-105">建議</span><span class="sxs-lookup"><span data-stu-id="85f83-105">Suggestion</span></span>

<span data-ttu-id="85f83-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="85f83-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="85f83-107">名稱</span><span class="sxs-lookup"><span data-stu-id="85f83-107">Name</span></span>    | <span data-ttu-id="85f83-108">值</span><span class="sxs-lookup"><span data-stu-id="85f83-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85f83-109">範圍</span><span class="sxs-lookup"><span data-stu-id="85f83-109">Scope</span></span>   |<span data-ttu-id="85f83-110">Minor</span><span class="sxs-lookup"><span data-stu-id="85f83-110">Minor</span></span>|
|<span data-ttu-id="85f83-111">版本</span><span class="sxs-lookup"><span data-stu-id="85f83-111">Version</span></span>|<span data-ttu-id="85f83-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="85f83-112">4.7.1</span></span>|
|<span data-ttu-id="85f83-113">類型</span><span class="sxs-lookup"><span data-stu-id="85f83-113">Type</span></span>|<span data-ttu-id="85f83-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="85f83-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="85f83-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="85f83-115">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
