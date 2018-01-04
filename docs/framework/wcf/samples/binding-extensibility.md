---
title: "繫結擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13f17264aa1c82f882d799e6b69a974e8abdb133
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="binding-extensibility"></a><span data-ttu-id="510c4-102">繫結擴充性</span><span class="sxs-lookup"><span data-stu-id="510c4-102">Binding Extensibility</span></span>

<span data-ttu-id="510c4-103">本節包含示範 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中自訂繫結的範例。</span><span class="sxs-lookup"><span data-stu-id="510c4-103">This section contains samples that demonstrate custom binding in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="510c4-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="510c4-104">In This Section</span></span>  
 <xref:System.ServiceModel.NetHttpBinding>  
 <span data-ttu-id="510c4-105">示範如何實作在 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 之上堆疊 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> 或 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> 的繫結。</span><span class="sxs-lookup"><span data-stu-id="510c4-105">Demonstrates how to implement a binding that stacks <xref:System.ServiceModel.Channels.HttpTransportBindingElement> or the <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> on top of the <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span></span>  
  
 [<span data-ttu-id="510c4-106">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="510c4-106">WSStreamedHttpBinding</span></span>](wsstreamedhttpbinding.md)  
 <span data-ttu-id="510c4-107">示範如何在使用 HTTP 時，建立針對支援資料流案例而設計的繫結。</span><span class="sxs-lookup"><span data-stu-id="510c4-107">Demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
