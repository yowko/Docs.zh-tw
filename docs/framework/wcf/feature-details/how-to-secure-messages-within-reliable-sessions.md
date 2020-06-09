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
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="da544-102">HOW TO：保護可靠工作階段內的訊息</span><span class="sxs-lookup"><span data-stu-id="da544-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="da544-103">本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="da544-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="da544-104">在設定檔中使用程式碼或以宣告方式啟用安全可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="da544-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="da544-105">此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="da544-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="da544-106">此程序包含下列三項主要工作：</span><span class="sxs-lookup"><span data-stu-id="da544-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="da544-107">指定用戶端與服務在可靠工作階段中交換訊息。</span><span class="sxs-lookup"><span data-stu-id="da544-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="da544-108">可靠工作階段中需要訊息層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="da544-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="da544-109">指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="da544-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="da544-110">在第一個工作中，端點設定元素包含參考名為之系結設定的 `bindingConfiguration` 屬性（在此範例中為），這一點很重要 `MessageSecurity` 。</span><span class="sxs-lookup"><span data-stu-id="da544-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="da544-111">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)然後，configuration 元素會參考此名稱，藉由將專案的屬性設定為來啟用可靠會話 `enabled` [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true` 。</span><span class="sxs-lookup"><span data-stu-id="da544-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="da544-112">您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。</span><span class="sxs-lookup"><span data-stu-id="da544-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="da544-113">如需以此設定程式為基礎之範例的來源複本，請參閱[WS 可靠會話](../samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="da544-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="da544-114">第二個工作的基本專案是藉由將 `mode` **\<security>** 用戶端和服務之專案中包含的元素屬性設定 **\<binding>** 為來完成 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="da544-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="da544-115">第三個工作的基本專案是藉由將 `clientCredentialType` **\<message>** 用戶端和服務的元素中包含之專案的屬性設定 **\<security>** 為來完成 `Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="da544-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="da544-116">在可靠會話中使用訊息安全性時，可靠的訊息會嘗試驗證未經驗證的用戶端，直到發生超時，而不是在第一次失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da544-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="da544-117">以 WSHttpBinding 設定服務以使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="da544-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="da544-118">此程式的說明請參閱[如何：在可靠會話中交換訊息](how-to-exchange-messages-within-a-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="da544-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="da544-119">以 WSHttpBinding 設定用戶端以使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="da544-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="da544-120">此程式的說明請參閱[如何：在可靠會話中交換訊息](how-to-exchange-messages-within-a-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="da544-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="da544-121">設定中的模式和 ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="da544-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="da544-122">將適當的繫結項目新增至 [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) 設定檔的元素。</span><span class="sxs-lookup"><span data-stu-id="da544-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="da544-123">下列範例會加入 [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="da544-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="da544-124">新增專案 **\<binding>** ，並將其 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="da544-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="da544-125">此範例使用名稱 `MessageSecurity` 。</span><span class="sxs-lookup"><span data-stu-id="da544-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="da544-126">加入 **\<security>** 元素，並將 `mode` 屬性設定為 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="da544-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="da544-127">在 **\<security>** 元素內，加入專案， **\<message>** 並將 `clientCredentialType` 屬性設定為 `Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="da544-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
