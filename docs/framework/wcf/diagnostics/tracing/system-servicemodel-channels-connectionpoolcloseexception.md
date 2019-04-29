---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666829"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
關閉此連線集區中的連線時發生例外狀況。  
  
## <a name="description"></a>描述  
 這個錯誤層級追蹤指出錯誤發生時關閉共用功能的 Windows Communication Foundation (WCF) 的連接所使用的連接集區。 可能是因為 CloseTimeout 內的某個共用連線或某組共用連線未成功關閉。 擲回此例外狀況時，同集區內其餘未關閉的連線都會中止，其他集區內未關閉的連線則會被放棄。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
