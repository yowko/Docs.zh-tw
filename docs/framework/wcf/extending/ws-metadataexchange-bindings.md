---
title: WS-MetadataExchange 繫結
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488620"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="19502-102">WS-MetadataExchange 繫結</span><span class="sxs-lookup"><span data-stu-id="19502-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="19502-103">本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。</span><span class="sxs-lookup"><span data-stu-id="19502-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="19502-104">預設繫結</span><span class="sxs-lookup"><span data-stu-id="19502-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="19502-105">預設繫結名稱</span><span class="sxs-lookup"><span data-stu-id="19502-105">Default Binding Name</span></span>|<span data-ttu-id="19502-106">繫結的建構方式</span><span class="sxs-lookup"><span data-stu-id="19502-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="19502-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="19502-107">MexHttpBinding</span></span>|<span data-ttu-id="19502-108">已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="19502-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="19502-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="19502-109">MexHttpsBinding</span></span>|<span data-ttu-id="19502-110">支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="19502-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="19502-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="19502-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="19502-112">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。</span><span class="sxs-lookup"><span data-stu-id="19502-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="19502-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="19502-113">MexTcpBinding</span></span>|<span data-ttu-id="19502-114">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="19502-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
