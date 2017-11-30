---
title: "將 .NET 遠端處理應用程式移轉到 WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dff06fbc52c0f4371abf0bcc465fd6a6d8be5859
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="521d6-102">將 .NET 遠端處理應用程式移轉到 WCF</span><span class="sxs-lookup"><span data-stu-id="521d6-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="521d6-103">**本主題專門說明一項為了在現有應用程式中提供回溯相容性而保留的舊有技術，不建議用於新的開發工作。分散式應用程式現在應該可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發。**</span><span class="sxs-lookup"><span data-stu-id="521d6-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="521d6-104">有兩種方法可以利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 搭配現有的 .NET 遠端處理應用程式：整合與移轉。</span><span class="sxs-lookup"><span data-stu-id="521d6-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="521d6-105">整合可以讓您同時執行 .Net Remoting 2.0 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，以便能同時公開兩種技術的相同商務物件，而不需要修改現有的 .Net Remoting 2.0 程式碼。</span><span class="sxs-lookup"><span data-stu-id="521d6-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="521d6-106">整合需要在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 (含) 以上版本執行。</span><span class="sxs-lookup"><span data-stu-id="521d6-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="521d6-107">如果您想要利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能，而且不需要與 Remoting 2.0 系統的網路相容性，可以將整個服務移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="521d6-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="521d6-108">從 .NET Remoting 2.0 移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需要變更遠端物件的介面及其組態設定。</span><span class="sxs-lookup"><span data-stu-id="521d6-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="521d6-109">這兩個主題中涵蓋[從遠端處理到 Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403)。</span><span class="sxs-lookup"><span data-stu-id="521d6-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="521d6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="521d6-110">See Also</span></span>  
 [<span data-ttu-id="521d6-111">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="521d6-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
