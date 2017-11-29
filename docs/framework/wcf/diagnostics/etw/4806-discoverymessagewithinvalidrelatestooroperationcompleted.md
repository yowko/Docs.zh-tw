---
title: 4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19e9a660-25f3-4332-b716-a12a59f2cbbb
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c55d45936a001df2c5da519e4ab79e7f8a2d470
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4806---discoverymessagewithinvalidrelatestooroperationcompleted"></a><span data-ttu-id="0eefe-102">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="0eefe-102">4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="0eefe-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0eefe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0eefe-104">ID</span><span class="sxs-lookup"><span data-stu-id="0eefe-104">ID</span></span>|<span data-ttu-id="0eefe-105">4806</span><span class="sxs-lookup"><span data-stu-id="0eefe-105">4806</span></span>|  
|<span data-ttu-id="0eefe-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0eefe-106">Keywords</span></span>|<span data-ttu-id="0eefe-107">探索</span><span class="sxs-lookup"><span data-stu-id="0eefe-107">Discovery</span></span>|  
|<span data-ttu-id="0eefe-108">層級</span><span class="sxs-lookup"><span data-stu-id="0eefe-108">Level</span></span>|<span data-ttu-id="0eefe-109">警告</span><span class="sxs-lookup"><span data-stu-id="0eefe-109">Warning</span></span>|  
|<span data-ttu-id="0eefe-110">通道</span><span class="sxs-lookup"><span data-stu-id="0eefe-110">Channel</span></span>|<span data-ttu-id="0eefe-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0eefe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0eefe-112">描述</span><span class="sxs-lookup"><span data-stu-id="0eefe-112">Description</span></span>  
 <span data-ttu-id="0eefe-113">當對應的作業已完成，或是 relatesTo 值無效，導致探索訊息已由 DiscoveryClient 丟棄時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="0eefe-113">This event is emitted when the discovery message was dropped by the DiscoveryClient because either the corresponding operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0eefe-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0eefe-114">Message</span></span>  
 <span data-ttu-id="0eefe-115">messageId='%2' 且 relatesTo='%3' 的 %1 訊息已由 DiscoveryClient 丟棄，因為對應的 %4 作業已完成，或是 relatesTo 值無效。</span><span class="sxs-lookup"><span data-stu-id="0eefe-115">A %1 message with messageId='%2' and relatesTo='%3' was dropped by the DiscoveryClient because either the corresponding %4 operation was completed or the relatesTo value is invalid.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0eefe-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0eefe-116">Details</span></span>
