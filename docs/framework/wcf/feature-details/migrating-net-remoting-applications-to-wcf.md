---
title: 將 .NET 遠端處理應用程式移轉到 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 2cfaebd064d10e5b331412d177929ecb20117a07
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248210"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="dfdfd-102">將 .NET 遠端處理應用程式移轉到 WCF</span><span class="sxs-lookup"><span data-stu-id="dfdfd-102">Migrating .NET Remoting Applications to WCF</span></span>

<span data-ttu-id="dfdfd-103">**本主題是針對與現有應用程式的回溯相容性而保留的舊版技術所特有，不建議用於新的開發。現在應該使用 WCF 開發分散式應用程式。**</span><span class="sxs-lookup"><span data-stu-id="dfdfd-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="dfdfd-104">有兩種方式可利用 WCF 與現有的 .NET 遠端應用程式：整合和遷移。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="dfdfd-105">整合可讓您讓 .NET 遠端處理2.0 和 WCF 並存執行，讓您同時公開兩種技術的相同商務物件，而不需要修改現有的 .NET Remoting 2.0 程式碼。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="dfdfd-106">您需要在 .NET Framework 2.0 或更高版本上執行整合。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="dfdfd-107">如果您想要利用 WCF 功能，而不需要與遠端2.0 系統的網路相容性，您可以將整個服務遷移至 WCF。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="dfdfd-108">從 .NET 遠端處理2.0 遷移至 WCF 需要變更遠端物件的介面及其設定。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="dfdfd-109">這兩個主題都涵蓋于 [從遠端處理至 Windows Communication Foundation](/previous-versions/aa730857(v=vs.80))。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdfd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfdfd-110">See also</span></span>

- [<span data-ttu-id="dfdfd-111">概觀說明</span><span class="sxs-lookup"><span data-stu-id="dfdfd-111">Conceptual Overview</span></span>](../conceptual-overview.md)
