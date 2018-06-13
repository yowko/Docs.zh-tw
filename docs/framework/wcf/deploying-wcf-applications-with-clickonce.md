---
title: 使用 ClickOnce 來部署 WCF 應用程式
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: ceb652eed1a7cc377538f5d693dcb85ed99da4b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456692"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="15859-102">使用 ClickOnce 來部署 WCF 應用程式</span><span class="sxs-lookup"><span data-stu-id="15859-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="15859-103">使用 Windows Communication Foundation (WCF) 用戶端應用程式可能會使用 ClickOnce 技術來部署。</span><span class="sxs-lookup"><span data-stu-id="15859-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="15859-104">這項技術讓應用程式能夠利用程式碼存取安全性提供的執行階段安全性保護，條件是它們必須使用受信任憑證完成數位簽署。</span><span class="sxs-lookup"><span data-stu-id="15859-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="15859-105">用來簽署 ClickOnce 應用程式的憑證必須位於信任的發行者存放區中，而且用戶端電腦上的本機安全性原則必須設定成對具有該發行者憑證之應用程式授與完全信任的權限。</span><span class="sxs-lookup"><span data-stu-id="15859-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="15859-106">如需設定 ClickOnce 應用程式和受信任的發行者資訊，請參閱[設定 ClickOnce 信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)。</span><span class="sxs-lookup"><span data-stu-id="15859-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15859-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15859-107">See Also</span></span>  
 [<span data-ttu-id="15859-108">受信任的應用程式部署概觀</span><span class="sxs-lookup"><span data-stu-id="15859-108">Trusted Application Deployment Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="15859-109">ClickOnce 部署適用於 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="15859-109">ClickOnce Deployment for Windows Forms Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=94776)
