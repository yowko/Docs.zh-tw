---
title: WS-MetadataExchange 繫結
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795469"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="14e44-102">WS-MetadataExchange 繫結</span><span class="sxs-lookup"><span data-stu-id="14e44-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="14e44-103">本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。</span><span class="sxs-lookup"><span data-stu-id="14e44-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="14e44-104">預設繫結</span><span class="sxs-lookup"><span data-stu-id="14e44-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="14e44-105">預設繫結名稱</span><span class="sxs-lookup"><span data-stu-id="14e44-105">Default Binding Name</span></span>|<span data-ttu-id="14e44-106">繫結的建構方式</span><span class="sxs-lookup"><span data-stu-id="14e44-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="14e44-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="14e44-107">mexHttpBinding</span></span>|<span data-ttu-id="14e44-108">已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="14e44-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="14e44-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="14e44-109">mexHttpsBinding</span></span>|<span data-ttu-id="14e44-110">支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="14e44-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="14e44-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="14e44-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="14e44-112">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。</span><span class="sxs-lookup"><span data-stu-id="14e44-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="14e44-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="14e44-113">mexTcpBinding</span></span>|<span data-ttu-id="14e44-114">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="14e44-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
