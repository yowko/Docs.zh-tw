---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5229eb7e72b63f3e44f67dc750d49acbf44410da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getrawinputdevices"></a><span data-ttu-id="8807a-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="8807a-102">GetRawInputDevices</span></span>
<span data-ttu-id="8807a-103">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="8807a-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8807a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8807a-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8807a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8807a-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="8807a-106">[out]指標[IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)列舉未經處理的輸入的裝置。</span><span class="sxs-lookup"><span data-stu-id="8807a-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="8807a-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="8807a-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="8807a-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="8807a-108">HRESULT:</span></span>  
  
 <span data-ttu-id="8807a-109">S_OK- [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)將只會由 PresentationHost.exe 若傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8807a-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="8807a-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8807a-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8807a-111">備註</span><span class="sxs-lookup"><span data-stu-id="8807a-111">Remarks</span></span>  
 <span data-ttu-id="8807a-112">未經處理輸入裝置是輸入裝置的集合，包括鍵盤、滑鼠及較不傳統的裝置，例如遙控器。</span><span class="sxs-lookup"><span data-stu-id="8807a-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="8807a-113">擷取未經處理輸入裝置的清單之後，PresentationHost.exe 會向裝置註冊，以接收 WM_INPUT 通知訊息。</span><span class="sxs-lookup"><span data-stu-id="8807a-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8807a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8807a-114">See Also</span></span>  
 [<span data-ttu-id="8807a-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span><span class="sxs-lookup"><span data-stu-id="8807a-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="8807a-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="8807a-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
