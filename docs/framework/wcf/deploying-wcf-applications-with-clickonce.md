---
title: "使用 ClickOnce 來部署 WCF 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 714e8341c58e5337d8e45bf61b48137d33fa51b9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-wcf-applications-with-clickonce"></a>使用 ClickOnce 來部署 WCF 應用程式
使用 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 的用戶端應用程式都可以運用 ClickOnce 技術來進行部署。 這項技術讓應用程式能夠利用程式碼存取安全性提供的執行階段安全性保護，條件是它們必須使用受信任憑證完成數位簽署。 用來簽署 ClickOnce 應用程式的憑證必須位於信任的發行者存放區中，而且用戶端電腦上的本機安全性原則必須設定成對具有該發行者憑證之應用程式授與完全信任的權限。  
  
 如需設定 ClickOnce 應用程式和受信任的發行者資訊，請參閱[設定 ClickOnce 信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="see-also"></a>另請參閱  
 [受信任的應用程式部署概觀](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [ClickOnce 部署適用於 Windows Forms 應用程式](http://go.microsoft.com/fwlink/?LinkId=94776)
