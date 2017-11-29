---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f3963fe28ccaf55b3946254e395b770619c8f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageclosedagain"></a>System.ServiceModel.MessageClosedAgain
System.ServiceModel.MessageClosedAgain  
  
## <a name="description"></a>描述  
 已再次關閉訊息。  
  
 訊息應該只關閉一次。 如果在使用者延伸程式碼中發出這個追蹤，就表示使用者延伸程式碼正在關閉一個已經關閉的訊息。 如果是透過產品代碼發出這個追蹤，就表示使用者延伸程式碼可能太早關閉訊息。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤來疑難排解您的應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
