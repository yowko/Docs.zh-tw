---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: d8edb8e916578247e62e3a3eb3b11b80f93416cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286951"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException

關閉此連線集區中的連線時發生例外狀況。  
  
## <a name="description"></a>描述  

 這個錯誤層級追蹤指出，關閉 Windows Communication Foundation (WCF) 的連接共用功能所使用的連接集區時發生錯誤。 可能是因為 CloseTimeout 內的某個共用連線或某組共用連線未成功關閉。 擲回此例外狀況時，同集區內其餘未關閉的連線都會中止，其他集區內未關閉的連線則會被放棄。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
