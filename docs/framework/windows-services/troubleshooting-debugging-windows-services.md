---
title: "疑難排解：對 Windows 服務進行偵錯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a>疑難排解：對 Windows 服務進行偵錯
當您偵錯 Windows 服務應用程式，您的服務和**Windows Service Manager**互動。 **Service Manager**啟動您的服務，藉由呼叫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法，然後等候 30 秒<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法來傳回。 如果此方法不會傳回在這段，管理員會顯示錯誤，無法啟動服務。  
  
 當您偵錯<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法中所述[如何： 偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)，您必須知道這個 30 秒的時間。 如果您在中斷點<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法並在 30 秒內無法逐步執行它，管理員將不會啟動服務。  
  
## <a name="see-also"></a>請參閱  
 [如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
