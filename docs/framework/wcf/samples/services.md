---
title: 服務範例
ms.date: 03/30/2017
ms.assetid: 462a2218-f8c6-4fb7-95bc-64765459c429
ms.openlocfilehash: a225d9bfb4d0ab70904a6e03c22269d69122f00b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591454"
---
# <a name="services"></a><span data-ttu-id="33723-102">服務</span><span class="sxs-lookup"><span data-stu-id="33723-102">Services</span></span>

<span data-ttu-id="33723-103">本節包含示範 Windows Communication Foundation （WCF）服務的範例。</span><span class="sxs-lookup"><span data-stu-id="33723-103">This section contains samples that demonstrate Windows Communication Foundation (WCF) services.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="33723-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="33723-104">In this section</span></span>

- <span data-ttu-id="33723-105">[放置](../feature-details/hosting.md)</span><span class="sxs-lookup"><span data-stu-id="33723-105">[Hosting](../feature-details/hosting.md)</span></span>\
<span data-ttu-id="33723-106">示範如何裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="33723-106">Demonstrates hosting WCF services.</span></span>

- <span data-ttu-id="33723-107">[服務互通性](service-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="33723-107">[Service Interoperability](service-interoperability.md)</span></span>\
<span data-ttu-id="33723-108">示範 WCF 與其他服務技術之間的互動。</span><span class="sxs-lookup"><span data-stu-id="33723-108">Demonstrates interaction between WCF and other service technologies.</span></span>

- <span data-ttu-id="33723-109">[問題](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="33723-109">[Behaviors](behaviors.md)</span></span>\
<span data-ttu-id="33723-110">示範 WCF 服務行為。</span><span class="sxs-lookup"><span data-stu-id="33723-110">Demonstrates WCF service behaviors.</span></span>

- <span data-ttu-id="33723-111">[服務安全性](service-security.md)</span><span class="sxs-lookup"><span data-stu-id="33723-111">[Service Security](service-security.md)</span></span>\
<span data-ttu-id="33723-112">示範 WCF 服務安全性。</span><span class="sxs-lookup"><span data-stu-id="33723-112">Demonstrates WCF service security.</span></span>

- <span data-ttu-id="33723-113">[WCF 服務的簡化設定](simplified-configuration-for-wcf-services.md)</span><span class="sxs-lookup"><span data-stu-id="33723-113">[Simplified Configuration for WCF Services](simplified-configuration-for-wcf-services.md)</span></span>\
<span data-ttu-id="33723-114">示範如何使用 WCF 來執行和設定一般服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="33723-114">Demonstrates how to implement and configure a typical service and client using WCF.</span></span>

- <span data-ttu-id="33723-115">[使用標準端點](usage-of-standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="33723-115">[Usage of Standard Endpoints](usage-of-standard-endpoints.md)</span></span>\
<span data-ttu-id="33723-116">示範如何在服務組態檔中使用標準端點。</span><span class="sxs-lookup"><span data-stu-id="33723-116">Demonstrates how to use standard endpoints in service configuration files.</span></span>

- <span data-ttu-id="33723-117">[延伸保護原則](extended-protection-policy.md)</span><span class="sxs-lookup"><span data-stu-id="33723-117">[Extended Protection Policy](extended-protection-policy.md)</span></span>\
<span data-ttu-id="33723-118">示範延伸保護，這是防止中間人 (MITM) 攻擊的一項安全性方案。</span><span class="sxs-lookup"><span data-stu-id="33723-118">Demonstrates Extended Protection, a security initiative for protecting against man-in-the-middle (MITM) attacks.</span></span>

- <span data-ttu-id="33723-119">[設定通道處理站](configuration-channel-factory.md)</span><span class="sxs-lookup"><span data-stu-id="33723-119">[Configuration Channel Factory](configuration-channel-factory.md)</span></span>\
<span data-ttu-id="33723-120">示範 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="33723-120">Demonstrates the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span>

- <span data-ttu-id="33723-121">[根源](addressing.md)</span><span class="sxs-lookup"><span data-stu-id="33723-121">[Addressing](addressing.md)</span></span>\
<span data-ttu-id="33723-122">示範端點位址的各方面與功能。</span><span class="sxs-lookup"><span data-stu-id="33723-122">Demonstrates various aspects and features of endpoint addresses.</span></span>

- <span data-ttu-id="33723-123">[首先](imperative.md)</span><span class="sxs-lookup"><span data-stu-id="33723-123">[Imperative](imperative.md)</span></span>\
<span data-ttu-id="33723-124">示範如何使用程式碼定義服務的 <xref:System.ServiceModel.WSHttpBinding>，而不是定義組態中的 `wsHttpBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="33723-124">Demonstrates how to define a <xref:System.ServiceModel.WSHttpBinding> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span>

- <span data-ttu-id="33723-125">[多個合約](multiple-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="33723-125">[Multiple Contracts](multiple-contracts.md)</span></span>\
<span data-ttu-id="33723-126">示範如何在服務實作一個以上的合約，以及如何設定要與每個已實作合約進行通訊的端點。</span><span class="sxs-lookup"><span data-stu-id="33723-126">Demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span>

- <span data-ttu-id="33723-127">[多個端點](multiple-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="33723-127">[Multiple Endpoints](multiple-endpoints.md)</span></span>\
<span data-ttu-id="33723-128">示範如何在服務上設定多個端點，以及如何從用戶端與每個端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="33723-128">Demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span>

- <span data-ttu-id="33723-129">[單一 ListenUri 的多個端點](multiple-endpoints-at-a-single-listenuri.md)</span><span class="sxs-lookup"><span data-stu-id="33723-129">[Multiple Endpoints at a Single ListenUri](multiple-endpoints-at-a-single-listenuri.md)</span></span>\
<span data-ttu-id="33723-130">示範在單一 `ListenUri` 裝載多個端點的服務。</span><span class="sxs-lookup"><span data-stu-id="33723-130">Demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span>

- <span data-ttu-id="33723-131">[OperationCoNtextScope](operationcontextscope.md)</span><span class="sxs-lookup"><span data-stu-id="33723-131">[OperationContextScope](operationcontextscope.md)</span></span>\
<span data-ttu-id="33723-132">示範如何使用標頭在 WCF 呼叫上傳送額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="33723-132">Demonstrates how to send extra information on a WCF call using headers.</span></span>

- <span data-ttu-id="33723-133">[服務描述](service-description.md)</span><span class="sxs-lookup"><span data-stu-id="33723-133">[Service Description](service-description.md)</span></span>\
<span data-ttu-id="33723-134">示範服務如何在執行階段擷取其服務描述資訊。</span><span class="sxs-lookup"><span data-stu-id="33723-134">Demonstrates how a service can retrieve its service description information at runtime.</span></span>

- <span data-ttu-id="33723-135">[ConcurrencyMode](concurrencymode-reentrant.md)</span><span class="sxs-lookup"><span data-stu-id="33723-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)</span></span>\
<span data-ttu-id="33723-136">示範如何在服務實作上使用可重新進入的並行模式。</span><span class="sxs-lookup"><span data-stu-id="33723-136">Demonstrates how to use the Reentrant concurrency mode on a service implementation.</span></span>
