---
title: "WS-MetadataExchange 繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="2f777-102">WS-MetadataExchange 繫結</span><span class="sxs-lookup"><span data-stu-id="2f777-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="2f777-103">本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。</span><span class="sxs-lookup"><span data-stu-id="2f777-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="2f777-104">預設繫結</span><span class="sxs-lookup"><span data-stu-id="2f777-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="2f777-105">預設繫結名稱</span><span class="sxs-lookup"><span data-stu-id="2f777-105">Default Binding Name</span></span>|<span data-ttu-id="2f777-106">繫結的建構方式</span><span class="sxs-lookup"><span data-stu-id="2f777-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="2f777-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2f777-107">MexHttpBinding</span></span>|<span data-ttu-id="2f777-108">已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="2f777-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="2f777-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="2f777-109">MexHttpsBinding</span></span>|<span data-ttu-id="2f777-110">支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="2f777-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="2f777-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="2f777-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="2f777-112">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。</span><span class="sxs-lookup"><span data-stu-id="2f777-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="2f777-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="2f777-113">MexTcpBinding</span></span>|<span data-ttu-id="2f777-114">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="2f777-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
