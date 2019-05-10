---
title: 探索版本控制
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 3f90fc5183e974b9045c156e0ae74099abfbc41a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626956"
---
# <a name="discovery-versioning"></a><span data-ttu-id="71c0a-102">探索版本控制</span><span class="sxs-lookup"><span data-stu-id="71c0a-102">Discovery Versioning</span></span>
<span data-ttu-id="71c0a-103">本主題簡要概述部分新探索功能的實作，</span><span class="sxs-lookup"><span data-stu-id="71c0a-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="71c0a-104">同時也概要說明如何選取要使用的探索版本。</span><span class="sxs-lookup"><span data-stu-id="71c0a-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="71c0a-105">探索版本控制</span><span class="sxs-lookup"><span data-stu-id="71c0a-105">Discovery Versioning</span></span>  
 <span data-ttu-id="71c0a-106">探索功能包括支援三種版本的 WS_Discovery 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="71c0a-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="71c0a-107">探索 API 可讓您選取要使用的通訊協定版本。</span><span class="sxs-lookup"><span data-stu-id="71c0a-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="71c0a-108">本文件簡要描述與版本控制相關的設定。</span><span class="sxs-lookup"><span data-stu-id="71c0a-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="71c0a-109">下列探索類別現在具有 <xref:System.ServiceModel.Discovery.DiscoveryVersion> 屬性，並且會在其建構函式中採用 <xref:System.ServiceModel.Discovery.DiscoveryVersion> 引數：</span><span class="sxs-lookup"><span data-stu-id="71c0a-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="71c0a-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="71c0a-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="71c0a-111">提供<xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005>為建構函式參數會使實作使用 April2005 版 Ws-discovery 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="71c0a-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="71c0a-112">這個版本對應至所發行的 WS-Discovery 通訊協定規格版本。</span><span class="sxs-lookup"><span data-stu-id="71c0a-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="71c0a-113">請使用這個版本與採用 April2005 版 WS-Discovery 的舊版應用程式交互操作。</span><span class="sxs-lookup"><span data-stu-id="71c0a-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="71c0a-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="71c0a-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="71c0a-115">Api 所使用的預設探索版本是<xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>。</span><span class="sxs-lookup"><span data-stu-id="71c0a-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="71c0a-116">這是最新的標準版 WS-Discovery 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="71c0a-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="71c0a-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="71c0a-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="71c0a-118">若提供 <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> 做為建構函式參數，會使實作使用 WS-Discovery 通訊協定的 Committee Draft 1 版。</span><span class="sxs-lookup"><span data-stu-id="71c0a-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="71c0a-119">請使用這個版本的通訊協定與執行 CD1 版 WS-Discovery 的實作交互操作。</span><span class="sxs-lookup"><span data-stu-id="71c0a-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="71c0a-120">支援在單一服務主機上進行不同探索版本的多個 UDP 探索端點</span><span class="sxs-lookup"><span data-stu-id="71c0a-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="71c0a-121">您可以在單一服務主機上公開多個不同探索版本的 UDP 探索端點。</span><span class="sxs-lookup"><span data-stu-id="71c0a-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="71c0a-122">若要這麼做，您必須為每個 UDP 探索端點指定一個唯一位址。</span><span class="sxs-lookup"><span data-stu-id="71c0a-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="71c0a-123">下列範例顯示如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="71c0a-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
