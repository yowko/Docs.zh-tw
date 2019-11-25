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
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="5865c-102">HOW TO：保護可靠工作階段內的訊息</span><span class="sxs-lookup"><span data-stu-id="5865c-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="5865c-103">本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="5865c-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="5865c-104">在設定檔中使用程式碼或以宣告方式啟用安全可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="5865c-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="5865c-105">此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="5865c-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="5865c-106">此程序包含下列三項主要工作：</span><span class="sxs-lookup"><span data-stu-id="5865c-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="5865c-107">指定用戶端與服務在可靠工作階段中交換訊息。</span><span class="sxs-lookup"><span data-stu-id="5865c-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="5865c-108">可靠工作階段中需要訊息層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="5865c-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="5865c-109">指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="5865c-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="5865c-110">在第一個工作中，端點設定元素包含參考名為之系結設定（在此範例中為） `MessageSecurity`的 `bindingConfiguration` 屬性，這一點很重要。</span><span class="sxs-lookup"><span data-stu-id="5865c-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="5865c-111">\<系結[ **>** ](../../configure-apps/file-schema/wcf/bindings.md) configuration 專案接著會參考此名稱，藉由將[ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))專案的 `enabled` 屬性設定為 [`true`] 來啟用可靠會話。</span><span class="sxs-lookup"><span data-stu-id="5865c-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="5865c-112">您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。</span><span class="sxs-lookup"><span data-stu-id="5865c-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="5865c-113">如需以此設定程式為基礎之範例的來源複本，請參閱[WS 可靠會話](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="5865c-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="5865c-114">第二個工作的基本專案是藉由將用戶端和服務的\<系結 **>** 元素中所包含之 **\<安全性 >** 專案的 `mode` 屬性設定為 [`Message`] 來完成。</span><span class="sxs-lookup"><span data-stu-id="5865c-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="5865c-115">第三個工作的基本專案，就是將用戶端和服務的 **\<security >** 元素中包含的 **\<message >** 元素的 `clientCredentialType` 屬性設定為 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="5865c-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="5865c-116">在可靠會話中使用訊息安全性時，可靠的訊息會嘗試驗證未經驗證的用戶端，直到發生超時，而不是在第一次失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5865c-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="5865c-117">以 WSHttpBinding 設定服務以使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="5865c-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="5865c-118">此程式的說明請參閱[如何：在可靠會話中交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="5865c-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="5865c-119">以 WSHttpBinding 設定用戶端以使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="5865c-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="5865c-120">此程式的說明請參閱[如何：在可靠會話中交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="5865c-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="5865c-121">設定中的模式和 ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5865c-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="5865c-122">將適當的繫結項目新增至設定檔的\<系結[ **>** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5865c-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="5865c-123">下列範例會將[ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5865c-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="5865c-124">將\<系結加入 **>** 元素，並將其 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="5865c-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="5865c-125">此範例會使用 `MessageSecurity`的名稱。</span><span class="sxs-lookup"><span data-stu-id="5865c-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="5865c-126">新增 **\<安全性 >** 元素，並將 `mode` 屬性設定為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="5865c-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="5865c-127">在 **\<安全性 >** 元素中，新增 **\<訊息 >** 專案，並將 `clientCredentialType` 屬性設定為 [`Certificate`]。</span><span class="sxs-lookup"><span data-stu-id="5865c-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
