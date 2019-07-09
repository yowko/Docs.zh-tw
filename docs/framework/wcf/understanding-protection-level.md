---
title: 了解保護層級
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 4ebb93d3ed325c115dcf311c821b014532dffc11
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663947"
---
# <a name="understanding-protection-level"></a><span data-ttu-id="6e9a7-102">了解保護層級</span><span class="sxs-lookup"><span data-stu-id="6e9a7-102">Understanding Protection Level</span></span>

<span data-ttu-id="6e9a7-103">在許多不同的類別上都可找到 `ProtectionLevel` 屬性，例如 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 類別。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-103">The `ProtectionLevel` property is found on many different classes, such as the <xref:System.ServiceModel.ServiceContractAttribute> and the <xref:System.ServiceModel.OperationContractAttribute> classes.</span></span> <span data-ttu-id="6e9a7-104">此屬性會控制如何保護訊息的部分 (或全部) 內容。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-104">The property controls how a part (or whole) of a message is protected.</span></span> <span data-ttu-id="6e9a7-105">本主題說明 Windows Communication Foundation (WCF) 功能，以及其運作方式。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-105">This topic explains the Windows Communication Foundation (WCF) feature and how it works.</span></span>

<span data-ttu-id="6e9a7-106">如需設定保護層級的指示，請參閱[How to:設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-106">For instructions on setting the protection level, see [How to: Set the ProtectionLevel Property](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6e9a7-107">保護層級只能在程式碼中加以設定，而不能在組態中設定。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-107">Protection levels can be set only in code, not in configuration.</span></span>

## <a name="basics"></a><span data-ttu-id="6e9a7-108">基本概念</span><span class="sxs-lookup"><span data-stu-id="6e9a7-108">Basics</span></span>

<span data-ttu-id="6e9a7-109">請從下列適當的基本描述來了解保護層級功能：</span><span class="sxs-lookup"><span data-stu-id="6e9a7-109">To understand the protection level feature, the following basic statements apply:</span></span>

- <span data-ttu-id="6e9a7-110">訊息的任何部分都存在三個基本保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-110">Three basic levels of protection exist for any part of a message.</span></span> <span data-ttu-id="6e9a7-111">屬性 (無論其出現在任何位置) 會設定為其中一個 <xref:System.Net.Security.ProtectionLevel> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-111">The property (wherever it occurs) is set to one of the <xref:System.Net.Security.ProtectionLevel> enumeration values.</span></span> <span data-ttu-id="6e9a7-112">這些值包括如下 (依照遞增的保護順序)：</span><span class="sxs-lookup"><span data-stu-id="6e9a7-112">In ascending order of protection, they include:</span></span>

  - <span data-ttu-id="6e9a7-113">`None`.</span><span class="sxs-lookup"><span data-stu-id="6e9a7-113">`None`.</span></span>

  - <span data-ttu-id="6e9a7-114">`Sign`.</span><span class="sxs-lookup"><span data-stu-id="6e9a7-114">`Sign`.</span></span> <span data-ttu-id="6e9a7-115">保護的部分會以數位方式簽署。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-115">The protected part is digitally signed.</span></span> <span data-ttu-id="6e9a7-116">這樣可以確保偵測到保護訊息部分所受到的任何竄改。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-116">This ensures detection of any tampering with the protected message part.</span></span>

  - <span data-ttu-id="6e9a7-117">`EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="6e9a7-117">`EncryptAndSign`.</span></span> <span data-ttu-id="6e9a7-118">訊息部分會先加密以確保機密性，接著才進行簽署。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-118">The message part is encrypted to ensure confidentiality before it is signed.</span></span>

- <span data-ttu-id="6e9a7-119">您可以設定保護需求僅適用於*應用程式資料*透過這項功能。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-119">You can set protection requirements only for *application data* with this feature.</span></span> <span data-ttu-id="6e9a7-120">例如，WS-Addressing 標頭是基礎結構資料，因此不會受到 `ProtectionLevel` 影響。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-120">For example, WS-Addressing headers are infrastructure data and, therefore, are not affected by the `ProtectionLevel`.</span></span>

- <span data-ttu-id="6e9a7-121">當安全性模式設定為 `Transport` 時，整個訊息就會由傳輸機制保護。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-121">When the security mode is set to `Transport`, the entire message is protected by the transport mechanism.</span></span> <span data-ttu-id="6e9a7-122">因此，針對訊息的不同部分設定個別的保護層級不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-122">Therefore, setting a separate protection level for different parts of a message has no effect.</span></span>

- <span data-ttu-id="6e9a7-123">`ProtectionLevel`可讓開發人員設定*最低層級*繫結必須符合。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-123">The `ProtectionLevel` is a way for the developer to set the *minimum level* that a binding must comply with.</span></span> <span data-ttu-id="6e9a7-124">當服務完成部署之後，指定於組態中的實際繫結不一定會支援該最低層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-124">When a service is deployed, the actual binding specified in configuration may or may not support the minimum level.</span></span> <span data-ttu-id="6e9a7-125">例如，根據預設，<xref:System.ServiceModel.BasicHttpBinding> 類別不支援安全性 (雖然此選項可加以啟用)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-125">For example, by default, the <xref:System.ServiceModel.BasicHttpBinding> class does not supply security (although it can be enabled).</span></span> <span data-ttu-id="6e9a7-126">因此，搭配使用該類別與具有不同於 `None` 之任何設定的合約，將會造成例外狀況 (Exception) 的擲回。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-126">Therefore, using it with a contract that has any setting other than `None` will cause an exception to be thrown.</span></span>

- <span data-ttu-id="6e9a7-127">如果服務要求的最小`ProtectionLevel`針對所有的訊息是`Sign`，用戶端 （或許是由非 WCF 技術所建立） 可加密並簽署所有訊息 （此為多個所需的最小）。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-127">If the service requires that the minimum `ProtectionLevel` for all messages is `Sign`, a client (perhaps created by a non-WCF technology) can encrypt and sign all messages (which is more than the minimum required).</span></span> <span data-ttu-id="6e9a7-128">在此情況下，WCF 不會擲回例外狀況因為用戶端已經超過最小值。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-128">In this case, WCF will not throw an exception because the client has done more than the minimum.</span></span> <span data-ttu-id="6e9a7-129">不過請注意，WCF 應用程式 （服務或用戶端） 不會過度保護訊息部分可能的話，但會遵守最低層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-129">Note, however, that WCF applications (services or clients) will not over-secure a message part if possible but will comply with the minimum level.</span></span> <span data-ttu-id="6e9a7-130">並請注意，當使用 `Transport` 做為安全性模式時，由於傳輸層級在本質上無法提供更細微層級的安全保護，所以它可能會過度保護訊息資料流。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-130">Also note that when using `Transport` as the security mode, the transport may over-secure the message stream because it is inherently unable to secure at a more granular level.</span></span>

- <span data-ttu-id="6e9a7-131">若您明確地將 `ProtectionLevel` 明確設定為 `Sign` 或 `EncryptAndSign`，則您必須使用已啟用安全性的繫結，否則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-131">If you set the `ProtectionLevel` explicitly to either `Sign` or `EncryptAndSign`, then you must use a binding with security enabled or an exception will be thrown.</span></span>

- <span data-ttu-id="6e9a7-132">若您選擇了一個啟用安全性的繫結，卻沒有在合約中設定 `ProtectionLevel` 屬性，則所有應用程式資料都會加密與簽章。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-132">If you select a binding that enables security and you do not set the `ProtectionLevel` property anywhere on the contract, all application data will be encrypted and signed.</span></span>

- <span data-ttu-id="6e9a7-133">若您選擇了尚未啟用安全性的繫結 (例如，根據預設，`BasicHttpBinding` 類別會停用安全性)，又沒有明確設定 `ProtectionLevel`，則所有應用程式資料都不會受到保護。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-133">If you select a binding that does not have security enabled (for example, the `BasicHttpBinding` class has security disabled by default), and the `ProtectionLevel` is not explicitly set, then none of the application data will be protected.</span></span>

- <span data-ttu-id="6e9a7-134">如果您使用在傳輸層級套用安全性的繫結，此時將根據傳輸層級的能力來保護所有的應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-134">If you are using a binding that applies security at the transport level, all application data will be secured according to the capabilities of the transport.</span></span>

- <span data-ttu-id="6e9a7-135">如果您使用在訊息層級套用安全性的繫結，此時將根據設定於合約中的保護層級來保護應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-135">If you use a binding that applies security at the message level, then application data will be secured according to the protection levels set on the contract.</span></span> <span data-ttu-id="6e9a7-136">如果您沒有指定保護層級，則訊息中的所有應用程式資料都會加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-136">If you do not specify a protection level, then all application data in the messages will be encrypted and signed.</span></span>

- <span data-ttu-id="6e9a7-137">在不同的範圍層級上皆可設定 `ProtectionLevel`。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-137">The `ProtectionLevel` can be set at different scoping levels.</span></span> <span data-ttu-id="6e9a7-138">範圍設定有相關聯的階層，下一節內容將說明這一點。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-138">There is a hierarchy associated with scoping, which is explained in the next section.</span></span>

## <a name="scoping"></a><span data-ttu-id="6e9a7-139">範圍設定</span><span class="sxs-lookup"><span data-stu-id="6e9a7-139">Scoping</span></span>

<span data-ttu-id="6e9a7-140">在最上層 API 設定 `ProtectionLevel`，便會設定其下各層的保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-140">Setting the `ProtectionLevel` on the topmost API sets the level for all levels below it.</span></span> <span data-ttu-id="6e9a7-141">如果較低層的 `ProtectionLevel` 是設定為不同值，則階層中比該層還低的所有 API 就會重設為新的保護層級 (不過，比該層還高的 API 仍然是受最上層保護層級的影響)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-141">If the `ProtectionLevel` is set to a different value at a lower level, all APIs below that level in the hierarchy will now be reset to the new level (APIs above it, however, will still be affected by the topmost level).</span></span> <span data-ttu-id="6e9a7-142">階層如下所述。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-142">The hierarchy is as follows.</span></span> <span data-ttu-id="6e9a7-143">相同一層的屬性屬於對等。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-143">Attributes at the same level are peers.</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a><span data-ttu-id="6e9a7-144">程式設計 ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="6e9a7-144">Programming ProtectionLevel</span></span>

<span data-ttu-id="6e9a7-145">若要程式設計階層中任何一點的 `ProtectionLevel`，只要在套用屬性 (Attribute) 時將屬性 (Property) 設定為適當值即可。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-145">To program the `ProtectionLevel` at any point in the hierarchy, simply set the property to an appropriate value when applying the attribute.</span></span> <span data-ttu-id="6e9a7-146">如需範例，請參閱[如何：設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-146">For examples, see [How to: Set the ProtectionLevel Property](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6e9a7-147">設定錯誤和訊息合約上的屬性時，需要了解這些功能的運作方式。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-147">Setting the property on faults and message contracts requires understanding how those features work.</span></span> <span data-ttu-id="6e9a7-148">如需詳細資訊，請參閱[如何：設定 ProtectionLevel 屬性](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)並[使用訊息合約](../../../docs/framework/wcf/feature-details/using-message-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-148">For more information, see [How to: Set the ProtectionLevel Property](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) and [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>

## <a name="ws-addressing-dependency"></a><span data-ttu-id="6e9a7-149">WS-Addressing 相依性</span><span class="sxs-lookup"><span data-stu-id="6e9a7-149">WS-Addressing Dependency</span></span>

<span data-ttu-id="6e9a7-150">在大部分情況下，使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端可確保用戶端和服務的合約完全相同。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-150">In most cases, using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a client ensures that the client and service contracts are identical.</span></span> <span data-ttu-id="6e9a7-151">不過，似乎相同的合約可能會導致用戶端擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-151">However, seemingly identical contracts can cause the client to throw an exception.</span></span> <span data-ttu-id="6e9a7-152">每當有繫結不支援 WS-Addressing 規格，而且在合約中指定了多重的保護層級時，便會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-152">This occurs whenever a binding does not support the WS-Addressing specification and multiple levels of protection are specified on the contract.</span></span> <span data-ttu-id="6e9a7-153">例如，當 <xref:System.ServiceModel.BasicHttpBinding> 類別不支援此規格，或是您建立了不支援 WS-Addressing 的繫結。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-153">For example, the <xref:System.ServiceModel.BasicHttpBinding> class does not support the specification, or if you create a custom binding that does not support WS-Addressing.</span></span> <span data-ttu-id="6e9a7-154">`ProtectionLevel` 功能必須依賴 WS-Addressing 規格，才能在單一合約上啟用不同的保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-154">The `ProtectionLevel` feature relies on the WS-Addressing specification to enable different protection levels on a single contract.</span></span> <span data-ttu-id="6e9a7-155">如果繫結不支援 WS-Addressing 規格，則所有的層級都會設定為相同的保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-155">If the binding does not support the WS-Addressing specification, all levels will be set to the same protection level.</span></span> <span data-ttu-id="6e9a7-156">合約上所有範圍的有效保護層級，都會設定為在合約上使用的最強保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-156">The effective protection level for all scopes on the contract will be set to the strongest protection level used on the contract.</span></span>

<span data-ttu-id="6e9a7-157">這樣便可能造成無法一下子就完成偵錯的問題。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-157">This may cause a problem that is hard to debug at first glance.</span></span> <span data-ttu-id="6e9a7-158">您也可能建立包含適用於一個以上服務之方法的用戶端合約 (介面)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-158">It is possible to create a client contract (an interface) that includes methods for more than one service.</span></span> <span data-ttu-id="6e9a7-159">也就是說，這個相同的介面會用來建立與多個服務通訊的用戶端，而且這個單一介面會包含適用於所有服務的方法。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-159">That is, the same interface is used to create a client that communicates with many services, and the single interface contains methods for all services.</span></span> <span data-ttu-id="6e9a7-160">開發人員在處理此罕見案例時，必須非常謹慎地只叫用個別特定服務所適用的方法。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-160">The developer must take care in this rare scenario to invoke only those methods that are applicable for each particular service.</span></span> <span data-ttu-id="6e9a7-161">如果繫結是 <xref:System.ServiceModel.BasicHttpBinding> 類別，就會無法支援多重保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-161">If the binding is the <xref:System.ServiceModel.BasicHttpBinding> class, multiple protection levels cannot be supported.</span></span> <span data-ttu-id="6e9a7-162">不過，進行回覆該用戶端的服務可能會採用比需要層級還低的保護層級來回應用戶端。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-162">However, a service replying to the client might respond to a client with a lower protection level than required.</span></span> <span data-ttu-id="6e9a7-163">在此情況下，用戶端會擲回例外狀況，因為它預期的是較高的保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-163">In this case, the client will throw an exception because it expects a higher protection level.</span></span>

<span data-ttu-id="6e9a7-164">下列程式碼範例會說明這個問題。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-164">An example of the code illustrates this problem.</span></span> <span data-ttu-id="6e9a7-165">下例範例會示範服務和用戶端合約。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-165">The following example shows a service and a client contract.</span></span> <span data-ttu-id="6e9a7-166">假設繫結[ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-166">Assume that the binding is the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element.</span></span> <span data-ttu-id="6e9a7-167">因此，合約上的所有作業都具有相同的保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-167">Therefore, all operations on a contract have the same protection level.</span></span> <span data-ttu-id="6e9a7-168">這個一致的保護層級將被判定為所有作業的最低保護層級。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-168">This uniform protection level is determined as the maximum protection level across all operations.</span></span>

<span data-ttu-id="6e9a7-169">服務合約是：</span><span class="sxs-lookup"><span data-stu-id="6e9a7-169">The service contract is:</span></span>

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

<span data-ttu-id="6e9a7-170">下列程式碼會示範用戶端合約介面。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-170">The following code shows the client contract interface.</span></span> <span data-ttu-id="6e9a7-171">請注意，其中包含要搭配不同服務使用的 `Tax` 方法：</span><span class="sxs-lookup"><span data-stu-id="6e9a7-171">Note that it includes a `Tax` method that is intended to be used with a different service:</span></span>

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

<span data-ttu-id="6e9a7-172">當用戶端呼叫 `Price` 方法時，它會在從服務接收回覆時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-172">When the client calls the `Price` method, it throws an exception when it receives a reply from the service.</span></span> <span data-ttu-id="6e9a7-173">這個例外狀況的發生是因為用戶端沒有在 `ProtectionLevel` 上指定 `ServiceContractAttribute`，使得用戶端對包括 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> 方法的所有方法使用預設值 (`Price`)。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-173">This occurs because the client does not specify a `ProtectionLevel` on the `ServiceContractAttribute`, and therefore the client uses the default (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) for all methods, including the `Price` method.</span></span> <span data-ttu-id="6e9a7-174">然而，此服務會傳回使用 <xref:System.Net.Security.ProtectionLevel.Sign> 層級的值，因為服務合約會定義將其保護層級設定為 <xref:System.Net.Security.ProtectionLevel.Sign> 的單一方法。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-174">However, the service returns the value using the <xref:System.Net.Security.ProtectionLevel.Sign> level because the service contract defines a single method that has its protection level set to <xref:System.Net.Security.ProtectionLevel.Sign>.</span></span> <span data-ttu-id="6e9a7-175">在此情況下，在驗證來自於服務的回應時，用戶端便會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="6e9a7-175">In this case, the client will throw an error when validating the response from the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e9a7-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e9a7-176">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [<span data-ttu-id="6e9a7-177">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="6e9a7-177">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="6e9a7-178">如何：設定 ProtectionLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="6e9a7-178">How to: Set the ProtectionLevel Property</span></span>](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [<span data-ttu-id="6e9a7-179">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="6e9a7-179">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="6e9a7-180">使用訊息合約</span><span class="sxs-lookup"><span data-stu-id="6e9a7-180">Using Message Contracts</span></span>](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
