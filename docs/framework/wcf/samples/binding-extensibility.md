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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61c8ae647012c5f1fffe5cf65c63b64cde62af1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="binding-extensibility"></a><span data-ttu-id="6e463-102">繫結擴充性</span><span class="sxs-lookup"><span data-stu-id="6e463-102">Binding Extensibility</span></span>
<span data-ttu-id="6e463-103">本節包含示範 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中自訂繫結的範例。</span><span class="sxs-lookup"><span data-stu-id="6e463-103">This section contains samples that demonstrate custom binding in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e463-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6e463-104">In This Section</span></span>  
 <xref:System.ServiceModel.NetHttpBinding>  
 <span data-ttu-id="6e463-105">示範如何實作在 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 之上堆疊 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> 或 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> 的繫結。</span><span class="sxs-lookup"><span data-stu-id="6e463-105">Demonstrates how to implement a binding that stacks <xref:System.ServiceModel.Channels.HttpTransportBindingElement> or the <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> on top of the <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span></span>  
  
 <!--zz <xref:System.ServiceModel.WSStreamedHttpBinding> --> `System.ServiceModel.WSStreamedHttpBinding` 
 <span data-ttu-id="6e463-106">示範如何在使用 HTTP 時，建立針對支援資料流案例而設計的繫結。</span><span class="sxs-lookup"><span data-stu-id="6e463-106">Demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>
