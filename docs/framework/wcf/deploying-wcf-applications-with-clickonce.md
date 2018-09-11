---
title: 使用 ClickOnce 來部署 WCF 應用程式
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: d733c6f523393737418c6394707c1d4e6e9c1710
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365013"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>使用 ClickOnce 來部署 WCF 應用程式
使用 Windows Communication Foundation (WCF) 的用戶端應用程式可能會使用 ClickOnce 技術來部署。 這項技術讓應用程式能夠利用程式碼存取安全性提供的執行階段安全性保護，條件是它們必須使用受信任憑證完成數位簽署。 用來簽署 ClickOnce 應用程式的憑證必須位於信任的發行者存放區中，而且用戶端電腦上的本機安全性原則必須設定成對具有該發行者憑證之應用程式授與完全信任的權限。  
  
 如需設定 ClickOnce 應用程式和受信任的發行者資訊，請參閱[設定 ClickOnce 受信任的發行者](https://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="see-also"></a>另請參閱  
 [受信任的應用程式部署概觀](https://go.microsoft.com/fwlink/?LinkId=94775)  
 [ClickOnce 部署的 Windows Forms 應用程式](https://go.microsoft.com/fwlink/?LinkId=94776)
