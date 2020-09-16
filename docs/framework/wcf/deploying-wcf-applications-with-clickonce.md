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
# <a name="deploying-wcf-applications-with-clickonce"></a>使用 ClickOnce 來部署 WCF 應用程式
使用 Windows Communication Foundation (WCF) 的用戶端應用程式可以使用 ClickOnce 技術來部署。 這項技術讓應用程式能夠利用程式碼存取安全性提供的執行階段安全性保護，條件是它們必須使用受信任憑證完成數位簽署。 用來簽署 ClickOnce 應用程式的憑證必須位於信任的發行者存放區中，而且用戶端電腦上的本機安全性原則必須設定成對具有該發行者憑證之應用程式授與完全信任的權限。  
  
 如需有關設定 ClickOnce 應用程式和受信任發行者的詳細資訊，請參閱設定 [Clickonce 受信任的發行者](/previous-versions/dotnet/articles/ms996418(v=msdn.10))。  
  
## <a name="see-also"></a>另請參閱

- [受信任的應用程式部署總覽](/visualstudio/deployment/trusted-application-deployment-overview)
- [Windows Forms 應用程式的 ClickOnce 部署](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
