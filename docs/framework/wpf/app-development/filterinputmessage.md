---
title: FilterInputMessage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e76f9863b68d5c7c34bca8adc872210527d6c17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="filterinputmessage"></a><span data-ttu-id="a148f-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="a148f-102">FilterInputMessage</span></span>
<span data-ttu-id="a148f-103">除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。</span><span class="sxs-lookup"><span data-stu-id="a148f-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a148f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a148f-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a148f-105">參數</span><span class="sxs-lookup"><span data-stu-id="a148f-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="a148f-106">[in] 傳送給正在取得未經處理輸入之視窗的 WM_INPUT 訊息。</span><span class="sxs-lookup"><span data-stu-id="a148f-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a148f-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="a148f-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="a148f-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="a148f-108">HRESULT:</span></span>  
  
 <span data-ttu-id="a148f-109">S_OK - 篩選未處理訊息，可能會進一步處理。</span><span class="sxs-lookup"><span data-stu-id="a148f-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="a148f-110">S_FALSE - 篩選已處理此訊息，應該不會進一步處理。</span><span class="sxs-lookup"><span data-stu-id="a148f-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="a148f-111">E_NOTIMPL – 如果此值會傳回， [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)不會再次呼叫。</span><span class="sxs-lookup"><span data-stu-id="a148f-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="a148f-112">這可能是從只想要提供自訂進度的主應用程式傳回，而 PresentationHost.exe 的錯誤使用者介面並不想要被從 PresentationHost.exe 轉送未經處理的輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="a148f-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a148f-113">備註</span><span class="sxs-lookup"><span data-stu-id="a148f-113">Remarks</span></span>  
 <span data-ttu-id="a148f-114">PresentationHost.exe 是各種未經處理輸入裝置 (包括鍵盤、滑鼠及遙控器) 的目標。</span><span class="sxs-lookup"><span data-stu-id="a148f-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="a148f-115">有時候，主應用程式中的行為取決於由 PresentationHost.exe 使用的輸入。</span><span class="sxs-lookup"><span data-stu-id="a148f-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="a148f-116">例如，主應用程式可能取決於接收特定輸入訊息來判斷是否要顯示特定使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="a148f-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="a148f-117">若要允許主應用程式接收必要的輸入的訊息，以提供這些行為，PresentationHost.exe 適當原始輸入將訊息轉寄至裝載的應用程式藉由呼叫[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)。</span><span class="sxs-lookup"><span data-stu-id="a148f-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="a148f-118">裝載的應用程式接收未經處理輸入的訊息向原始輸入裝置 （人性化介面裝置） 所傳回的集合[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)。</span><span class="sxs-lookup"><span data-stu-id="a148f-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a148f-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a148f-119">See Also</span></span>  
 [<span data-ttu-id="a148f-120">澗通知</span><span class="sxs-lookup"><span data-stu-id="a148f-120">WM_INPUT Notification</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
