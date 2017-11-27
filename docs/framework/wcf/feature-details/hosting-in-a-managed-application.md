---
title: "在 Managed 應用程式中裝載"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 30d531d436937bf5183ac0c28d59425ea71762e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-in-a-managed-application"></a>在 Managed 應用程式中裝載
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務可以裝載於任何 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式中。 自我裝載服務是最彈性的裝載選項，因為它只需要最基本的基礎結構就可部署。 但是，它同時也是最不穩固的裝載選項，因為 Managed 應用程式無法在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]中提供其他裝載選項的進階裝載與管理功能，例如網際網路資訊服務 (IIS) 和 Windows 服務。  
  
 若要建立自我裝載服務，請建立並開啟 <xref:System.ServiceModel.ServiceHost>的執行個體，以便啟動服務來接聽訊息。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][How to： 將 WCF 服務裝載於 Managed 應用程式](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)。  
  
 如需如何定義合約、 實作合約，以及裝載內部的受管理的應用程式服務的完整範例，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)和[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)。  
  
 下列各節說明使用此裝載選項的常見案例。  
  
## <a name="console-applications"></a>主控台應用程式  
 自我裝載所啟用的常見案例為在主控台應用程式中執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。 在服務的開發階段，於主控台應用程式中裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務一般來說是很有用的方式。 這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。  
  
## <a name="rich-client-applications"></a>豐富型用戶端應用程式  
 其他自我裝載選項所啟用的常見案例包括豐富型用戶端應用程式，例如以 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 為基礎的應用程式，或是 Windows Forms (WinForms)。 這個裝載選項同時可讓豐富型用戶端應用程式 (例如， [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 和 WinForms 應用程式) 更容易與外界通訊。 例如，使用 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 做為使用者介面，並同時裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務以允許其他用戶端與其連線並共用資訊的對等共同作業用戶端。  
  
## <a name="see-also"></a>另請參閱  
 [裝載服務](../../../../docs/framework/wcf/hosting-services.md)  
 [快速入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)
