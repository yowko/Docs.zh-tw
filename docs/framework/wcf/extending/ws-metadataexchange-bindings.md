---
title: WS-MetadataExchange 繫結
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767344"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="438cc-102">WS-MetadataExchange 繫結</span><span class="sxs-lookup"><span data-stu-id="438cc-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="438cc-103">本主題會說明如何為各種傳輸建構預設中繼資料交換繫結。</span><span class="sxs-lookup"><span data-stu-id="438cc-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="438cc-104">預設繫結</span><span class="sxs-lookup"><span data-stu-id="438cc-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="438cc-105">預設繫結名稱</span><span class="sxs-lookup"><span data-stu-id="438cc-105">Default Binding Name</span></span>|<span data-ttu-id="438cc-106">繫結的建構方式</span><span class="sxs-lookup"><span data-stu-id="438cc-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="438cc-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="438cc-107">mexHttpBinding</span></span>|<span data-ttu-id="438cc-108">已停用傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="438cc-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="438cc-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="438cc-109">mexHttpsBinding</span></span>|<span data-ttu-id="438cc-110">支援傳輸層級安全性的 <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="438cc-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="438cc-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="438cc-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="438cc-112">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>的 。</span><span class="sxs-lookup"><span data-stu-id="438cc-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="438cc-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="438cc-113">mexTcpBinding</span></span>|<span data-ttu-id="438cc-114">具有使用預設值之 <xref:System.ServiceModel.Channels.CustomBinding> 的 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="438cc-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
