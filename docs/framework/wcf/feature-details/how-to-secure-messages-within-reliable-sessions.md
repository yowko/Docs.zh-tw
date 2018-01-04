---
title: "HOW TO：保護可靠工作階段內的訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 254cc241edf2d1c53ce9dd14eee41cd8bf6eaa76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="486b8-102">HOW TO：保護可靠工作階段內的訊息</span><span class="sxs-lookup"><span data-stu-id="486b8-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="486b8-103">本主題概要說明透過其中一個系統提供的繫結 (此繫結支援此類工作階段，但非預設) 啟用可靠工作階段中所交換訊息的訊息層級安全性所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="486b8-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="486b8-104">透過命令式程式碼或是宣告式組態檔，請啟用安全、 可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="486b8-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="486b8-105">此程序透過用戶端與服務組態檔來啟用安全、可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="486b8-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="486b8-106">此程序包含下列三項主要工作：</span><span class="sxs-lookup"><span data-stu-id="486b8-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="486b8-107">指定用戶端與服務在可靠工作階段中交換訊息。</span><span class="sxs-lookup"><span data-stu-id="486b8-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="486b8-108">可靠工作階段中需要訊息層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="486b8-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="486b8-109">指定要向服務驗證用戶端時，用戶端必須使用的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="486b8-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="486b8-110">請務必在第一個工作中，端點組態項目包含`bindingConfiguration`屬性必須參考名為 （在此範例中） 的繫結組態`MessageSecurity`。</span><span class="sxs-lookup"><span data-stu-id="486b8-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="486b8-111">[ **\<繫結 >** ](../../../../docs/framework/misc/binding.md)組態項目，然後參考此名稱，藉此啟用可靠工作階段`enabled`屬性[  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)元素`true`。</span><span class="sxs-lookup"><span data-stu-id="486b8-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="486b8-112">您可以將 `ordered` 屬性設為 `true`，要求在可靠工作階段中提供依順序遞送的保證。</span><span class="sxs-lookup"><span data-stu-id="486b8-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="486b8-113">此組態程序所依據的範例的來源副本，請參閱[WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="486b8-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="486b8-114">第二個工作的必要項目透過設定`mode`屬性**\<安全性 >**中所包含的項目**\<繫結 >**用戶端和服務的項目`Message`。</span><span class="sxs-lookup"><span data-stu-id="486b8-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="486b8-115">第三個工作的必要項目透過設定`clientCredentialType`屬性**\<訊息 >**中所包含的項目**\<安全性 >**用戶端和服務的項目`Certificate`。</span><span class="sxs-lookup"><span data-stu-id="486b8-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="486b8-116">當使用訊息安全性與可靠工作階段，可信賴傳訊嘗試驗證未驗證用戶端，而不是擲回的例外狀況，在第一次失敗時，發生逾時為止。</span><span class="sxs-lookup"><span data-stu-id="486b8-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="486b8-117">透過 WSHttpBinding 使用可靠工作階段設定服務</span><span class="sxs-lookup"><span data-stu-id="486b8-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="486b8-118">此程序所述[How to： 交換訊息在可靠工作階段](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="486b8-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="486b8-119">設定用戶端透過 WSHttpBinding 使用可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="486b8-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="486b8-120">此程序所述[How to： 交換訊息在可靠工作階段](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="486b8-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="486b8-121">在組態中設定模式與 clientcredentialtype 屬性</span><span class="sxs-lookup"><span data-stu-id="486b8-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="486b8-122">新增適當的繫結項目的[ **\<繫結 >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)組態檔元素。</span><span class="sxs-lookup"><span data-stu-id="486b8-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="486b8-123">下列範例會將[  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="486b8-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="486b8-124">新增**\<繫結 >**項目並設定其`name`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="486b8-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="486b8-125">此範例會使用名稱`MessageSecurity`。</span><span class="sxs-lookup"><span data-stu-id="486b8-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="486b8-126">新增**\<安全性 >**項目並設定`mode`屬性`Message`。</span><span class="sxs-lookup"><span data-stu-id="486b8-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="486b8-127">內**\<安全性 >**項目，加入**\<訊息 >**項目並設定`clientCredentialType`屬性`Certificate`。</span><span class="sxs-lookup"><span data-stu-id="486b8-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
