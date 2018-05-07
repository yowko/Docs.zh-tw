---
title: 在 Managed 應用程式中裝載
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: f374c199fb1982ab8854e41c0c8308f46451d9d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-a-managed-application"></a>在 Managed 應用程式中裝載
Windows Communication Foundation (WCF) 服務可以裝載於任何[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式。 自我裝載服務是最彈性的裝載選項，因為它只需要最基本的基礎結構就可部署。 但是，它也會至少穩固的裝載選項，因為 managed 應用程式不提供的進階裝載和管理功能，例如網際網路資訊服務 (IIS) 和 Windows 服務在 WCF 中，其他裝載選項。  
  
 若要建立自我裝載服務，請建立並開啟 <xref:System.ServiceModel.ServiceHost>的執行個體，以便啟動服務來接聽訊息。 如需詳細資訊，請參閱[How to： 裝載中受管理的應用程式的 WCF 服務](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)。  
  
 如需如何定義合約、 實作合約，以及裝載內部的受管理的應用程式服務的完整範例，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)和[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)。  
  
 下列各節說明使用此裝載選項的常見案例。  
  
## <a name="console-applications"></a>主控台應用程式  
 在主控台應用程式內執行的 WCF 服務進行自我裝載啟用的常見案例。 裝載於主控台應用程式的 WCF 服務適合通常在開發階段的服務。 這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。  
  
## <a name="rich-client-applications"></a>豐富型用戶端應用程式  
 其他自我裝載啟用的常見案例是豐富型用戶端應用程式，例如 Windows Presentation Foundation (WPF) 或 Windows Forms (WinForms) 為基礎。 這個裝載選項同時可讓豐富型用戶端應用程式 (例如， [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 和 WinForms 應用程式) 更容易與外界通訊。 例如，使用的對等共同作業用戶端[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]作為其使用者介面，也會裝載 WCF 服務，可讓其他用戶端連接到它，並共用資訊。  
  
## <a name="see-also"></a>另請參閱  
 [裝載服務](../../../../docs/framework/wcf/hosting-services.md)  
 [快速入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)
