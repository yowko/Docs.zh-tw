---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182191"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="7fe6e-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="7fe6e-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="7fe6e-103">關閉此連線集區中的連線時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7fe6e-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7fe6e-104">描述</span><span class="sxs-lookup"><span data-stu-id="7fe6e-104">Description</span></span>  
 <span data-ttu-id="7fe6e-105">這個錯誤層級追蹤指出錯誤發生時關閉共用功能的 Windows Communication Foundation (WCF) 的連接所使用的連接集區。</span><span class="sxs-lookup"><span data-stu-id="7fe6e-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="7fe6e-106">可能是因為 CloseTimeout 內的某個共用連線或某組共用連線未成功關閉。</span><span class="sxs-lookup"><span data-stu-id="7fe6e-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="7fe6e-107">擲回此例外狀況時，同集區內其餘未關閉的連線都會中止，其他集區內未關閉的連線則會被放棄。</span><span class="sxs-lookup"><span data-stu-id="7fe6e-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe6e-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fe6e-108">See also</span></span>

- [<span data-ttu-id="7fe6e-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="7fe6e-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="7fe6e-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7fe6e-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7fe6e-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="7fe6e-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
