---
title: 加入上線與離線狀態
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 74b113d64003756982a6b5701d9601c3116a9046
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960651"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="dcf97-102">加入上線與離線狀態</span><span class="sxs-lookup"><span data-stu-id="dcf97-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="dcf97-103">在許多情況下，應用程式監視對等通道連線狀態的特定詳細資訊是很重要的工作。</span><span class="sxs-lookup"><span data-stu-id="dcf97-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="dcf97-104">您可以在 `GetProperty` 介面實作上呼叫 <xref:System.ServiceModel.IOnlineStatus> 方法，以取得此項資訊。</span><span class="sxs-lookup"><span data-stu-id="dcf97-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="dcf97-105">含有此介面實作的物件可以監視連線狀態或註冊事件處理常式 (例如 `OnOnline` 和 `OnOffline`)，並且在發生上線狀態變更時立即做出反應。</span><span class="sxs-lookup"><span data-stu-id="dcf97-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="dcf97-106">在對等通道基礎結構中，用戶端在已連接至少一個的對等用戶端時會被視為上線，否則為離線。</span><span class="sxs-lookup"><span data-stu-id="dcf97-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="dcf97-107">對於偵錯開發中之應用程式或是向終端使用者顯示詳細資訊，這項功能特別有用。</span><span class="sxs-lookup"><span data-stu-id="dcf97-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcf97-108">上線事件處理常式在傳送任何訊息之前，應先確認節點是否已開啟。</span><span class="sxs-lookup"><span data-stu-id="dcf97-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf97-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcf97-109">See also</span></span>

- [<span data-ttu-id="dcf97-110">建置對等通道應用程式</span><span class="sxs-lookup"><span data-stu-id="dcf97-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
