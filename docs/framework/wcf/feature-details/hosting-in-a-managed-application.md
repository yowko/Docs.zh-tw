---
title: 在 Managed 應用程式中裝載
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 759257edf89d1af5c453bb98f41361b54cf113ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597341"
---
# <a name="hosting-in-a-managed-application"></a>在 Managed 應用程式中裝載
Windows Communication Foundation （WCF）服務可以裝載于任何 .NET Framework 應用程式中。 自我裝載服務是最彈性的裝載選項，因為它只需要最基本的基礎結構就可部署。 不過，它也是最不健全的裝載選項，因為 managed 應用程式不會在 WCF 中提供其他裝載選項的先進裝載和管理功能，例如 Internet Information Services （IIS）和 Windows 服務。  
  
 若要建立自我裝載服務，請建立並開啟 <xref:System.ServiceModel.ServiceHost>的執行個體，以便啟動服務來接聽訊息。 如需詳細資訊，請參閱[如何：在 Managed 應用程式中裝載 WCF 服務](../how-to-host-a-wcf-service-in-a-managed-application.md)。  
  
 如需如何定義合約、執行合約，以及在受控應用程式內裝載服務的完整範例，請參閱[消費者入門教學](../getting-started-tutorial.md)課程和[自我裝載](../samples/self-host.md)。  
  
 下列各節說明使用此裝載選項的常見案例。  
  
## <a name="console-applications"></a>主控台應用程式  
 自我裝載所啟用的常見案例是在主控台應用程式中執行的 WCF 服務。 在服務的開發階段，將 WCF 服務裝載于主控台應用程式中通常很有用。 這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。  
  
## <a name="rich-client-applications"></a>豐富型用戶端應用程式  
 其他自我裝載啟用的常見案例是豐富型用戶端應用程式，例如以 Windows Presentation Foundation （WPF）或 Windows Forms （WinForms）為基礎的應用程式。 此裝載選項也可讓豐富型用戶端應用程式（例如 WPF 和 WinForms 應用程式）輕鬆地與外界進行通訊。 例如，對等共同作業用戶端會使用 WPF 做為其使用者介面，同時裝載 WCF 服務，以允許其他用戶端與其連線並共用資訊。  
  
## <a name="see-also"></a>請參閱

- [裝載服務](../hosting-services.md)
- [消費者入門教學課程](../getting-started-tutorial.md)
