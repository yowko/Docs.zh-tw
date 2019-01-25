---
title: System.ServiceModel.TxReleaseServiceInstanceOnCompletion
ms.date: 03/30/2017
ms.assetid: e167bad3-861f-43e4-9e78-9c275cf64a29
ms.openlocfilehash: 9c276fc60b14ad99c1b8deac0bdde2ecfe8a10cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631083"
---
# <a name="systemservicemodeltxreleaseserviceinstanceoncompletion"></a><span data-ttu-id="09785-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span><span class="sxs-lookup"><span data-stu-id="09785-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span></span>
<span data-ttu-id="09785-103">因為 ReleaseServiceInstanceOnTransactionComplete ServiceBehaviorAttribute 設定為 true，所以異動 '{0}' 完成時會釋放服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="09785-103">The service instance was released on the completion of the transaction '{0}' because the ReleaseServiceInstanceOnTransactionComplete ServiceBehaviorAttribute was set to true.</span></span>  
  
## <a name="description"></a><span data-ttu-id="09785-104">描述</span><span class="sxs-lookup"><span data-stu-id="09785-104">Description</span></span>  
 <span data-ttu-id="09785-105">在因為目前的現用異動完成、且 ReleaseServiceInstanceOnTransactionComplete 設定為 `true` 的情況下釋放或處置現行服務執行個體時，就會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="09785-105">Traced when the current service instance is released or disposed due to the completion of the current active transaction and ReleaseServiceInstanceOnTransactionComplete is set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09785-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09785-106">See also</span></span>
- [<span data-ttu-id="09785-107">追蹤</span><span class="sxs-lookup"><span data-stu-id="09785-107">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="09785-108">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="09785-108">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="09785-109">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="09785-109">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
