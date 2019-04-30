---
title: 服務範例-WCF
ms.date: 03/30/2017
ms.assetid: 462a2218-f8c6-4fb7-95bc-64765459c429
ms.openlocfilehash: 3fbca09a7b50a15299cb8e805ac84c60e4b78fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967540"
---
# <a name="services"></a><span data-ttu-id="281a0-102">服務</span><span class="sxs-lookup"><span data-stu-id="281a0-102">Services</span></span>

<span data-ttu-id="281a0-103">本節包含示範 Windows Communication Foundation (WCF) 服務的範例。</span><span class="sxs-lookup"><span data-stu-id="281a0-103">This section contains samples that demonstrate Windows Communication Foundation (WCF) services.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="281a0-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="281a0-104">In this section</span></span>

- <span data-ttu-id="281a0-105">[裝載](../../../../docs/framework/wcf/feature-details/hosting.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-105">[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)\\</span></span>
<span data-ttu-id="281a0-106">示範裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="281a0-106">Demonstrates hosting WCF services.</span></span>

- <span data-ttu-id="281a0-107">[服務互通性](service-interoperability.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-107">[Service Interoperability](service-interoperability.md)\\</span></span>
<span data-ttu-id="281a0-108">示範 WCF 與其他服務技術之間的互動。</span><span class="sxs-lookup"><span data-stu-id="281a0-108">Demonstrates interaction between WCF and other service technologies.</span></span>

- <span data-ttu-id="281a0-109">[行為](behaviors.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-109">[Behaviors](behaviors.md)\\</span></span>
<span data-ttu-id="281a0-110">示範 WCF 服務行為。</span><span class="sxs-lookup"><span data-stu-id="281a0-110">Demonstrates WCF service behaviors.</span></span>

- <span data-ttu-id="281a0-111">[服務安全性](service-security.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-111">[Service Security](service-security.md)\\</span></span>
<span data-ttu-id="281a0-112">示範 WCF 服務安全性。</span><span class="sxs-lookup"><span data-stu-id="281a0-112">Demonstrates WCF service security.</span></span>

- <span data-ttu-id="281a0-113">[WCF 服務的簡化的組態](simplified-configuration-for-wcf-services.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-113">[Simplified Configuration for WCF Services](simplified-configuration-for-wcf-services.md)\\</span></span>
<span data-ttu-id="281a0-114">示範如何實作與設定一般服務和用戶端使用 WCF。</span><span class="sxs-lookup"><span data-stu-id="281a0-114">Demonstrates how to implement and configure a typical service and client using WCF.</span></span>

- <span data-ttu-id="281a0-115">[使用標準端點](usage-of-standard-endpoints.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-115">[Usage of Standard Endoints](usage-of-standard-endpoints.md)\\</span></span>
<span data-ttu-id="281a0-116">示範如何在服務組態檔中使用標準端點。</span><span class="sxs-lookup"><span data-stu-id="281a0-116">Demonstrates how to use standard endpoints in service configuration files.</span></span>

- <span data-ttu-id="281a0-117">[延伸的保護原則](extended-protection-policy.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-117">[Extended Protection Policy](extended-protection-policy.md)\\</span></span>
<span data-ttu-id="281a0-118">示範延伸保護，這是防止中間人 (MITM) 攻擊的一項安全性方案。</span><span class="sxs-lookup"><span data-stu-id="281a0-118">Demonstrates Extended Protection, a security initiative for protecting against man-in-the-middle (MITM) attacks.</span></span>

- <span data-ttu-id="281a0-119">[組態通道處理站](configuration-channel-factory.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-119">[Configuration Channel Factory](configuration-channel-factory.md)\\</span></span>
<span data-ttu-id="281a0-120">示範 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="281a0-120">Demonstrates the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span>

- <span data-ttu-id="281a0-121">[定址](addressing.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-121">[Addressing](addressing.md)\\</span></span>
<span data-ttu-id="281a0-122">示範端點位址的各方面與功能。</span><span class="sxs-lookup"><span data-stu-id="281a0-122">Demonstrates various aspects and features of endpoint addresses.</span></span>

- <span data-ttu-id="281a0-123">[命令式](imperative.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-123">[Imperative](imperative.md)\\</span></span>
<span data-ttu-id="281a0-124">示範如何使用程式碼定義服務的 <xref:System.ServiceModel.WSHttpBinding>，而不是定義組態中的 `wsHttpBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="281a0-124">Demonstrates how to define a <xref:System.ServiceModel.WSHttpBinding> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span>

- <span data-ttu-id="281a0-125">[多個合約](multiple-contracts.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-125">[Multiple Contracts](multiple-contracts.md)\\</span></span>
<span data-ttu-id="281a0-126">示範如何在服務實作一個以上的合約，以及如何設定要與每個已實作合約進行通訊的端點。</span><span class="sxs-lookup"><span data-stu-id="281a0-126">Demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span>

- <span data-ttu-id="281a0-127">[多個端點](multiple-endpoints.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-127">[Multiple Endpoints](multiple-endpoints.md)\\</span></span>
<span data-ttu-id="281a0-128">示範如何在服務上設定多個端點，以及如何從用戶端與每個端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="281a0-128">Demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span>

- <span data-ttu-id="281a0-129">[單一 listenuri 的多個端點](multiple-endpoints-at-a-single-listenuri.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-129">[Multiple Endpoints at a Single ListenUri](multiple-endpoints-at-a-single-listenuri.md)\\</span></span>
<span data-ttu-id="281a0-130">示範在單一 `ListenUri` 裝載多個端點的服務。</span><span class="sxs-lookup"><span data-stu-id="281a0-130">Demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span>

- <span data-ttu-id="281a0-131">[OperationContextScope](operationcontextscope.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-131">[OperationContextScope](operationcontextscope.md)\\</span></span>
<span data-ttu-id="281a0-132">示範如何傳送上使用標頭的 WCF 呼叫的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="281a0-132">Demonstrates how to send extra information on a WCF call using headers.</span></span>

- <span data-ttu-id="281a0-133">[服務描述](service-description.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-133">[Service Description](service-description.md)\\</span></span>
<span data-ttu-id="281a0-134">示範服務如何在執行階段擷取其服務描述資訊。</span><span class="sxs-lookup"><span data-stu-id="281a0-134">Demonstrates how a service can retrieve its service description information at runtime.</span></span>

- <span data-ttu-id="281a0-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)\\</span><span class="sxs-lookup"><span data-stu-id="281a0-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)\\</span></span>
<span data-ttu-id="281a0-136">示範如何在服務實作上使用可重新進入的並行模式。</span><span class="sxs-lookup"><span data-stu-id="281a0-136">Demonstrates how to use the Reentrant concurrency mode on a service implementation.</span></span>