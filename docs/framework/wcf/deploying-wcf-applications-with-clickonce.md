---
title: 使用 ClickOnce 來部署 WCF 應用程式
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 52657c5f3b5bc6c57c59f4ef23e73089f3c681eb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550367"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="538b8-102">使用 ClickOnce 來部署 WCF 應用程式</span><span class="sxs-lookup"><span data-stu-id="538b8-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="538b8-103">使用 Windows Communication Foundation (WCF) 的用戶端應用程式可以使用 ClickOnce 技術來部署。</span><span class="sxs-lookup"><span data-stu-id="538b8-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="538b8-104">這項技術讓應用程式能夠利用程式碼存取安全性提供的執行階段安全性保護，條件是它們必須使用受信任憑證完成數位簽署。</span><span class="sxs-lookup"><span data-stu-id="538b8-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="538b8-105">用來簽署 ClickOnce 應用程式的憑證必須位於信任的發行者存放區中，而且用戶端電腦上的本機安全性原則必須設定成對具有該發行者憑證之應用程式授與完全信任的權限。</span><span class="sxs-lookup"><span data-stu-id="538b8-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="538b8-106">如需有關設定 ClickOnce 應用程式和受信任發行者的詳細資訊，請參閱設定 [Clickonce 受信任的發行者](/previous-versions/dotnet/articles/ms996418(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="538b8-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538b8-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="538b8-107">See also</span></span>

- [<span data-ttu-id="538b8-108">受信任的應用程式部署總覽</span><span class="sxs-lookup"><span data-stu-id="538b8-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="538b8-109">[Windows Forms 應用程式的 ClickOnce 部署](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="538b8-109">[ClickOnce Deployment for Windows Forms Applications](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>
