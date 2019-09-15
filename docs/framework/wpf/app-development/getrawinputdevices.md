---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991751"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="f9598-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="f9598-102">GetRawInputDevices</span></span>
<span data-ttu-id="f9598-103">可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。</span><span class="sxs-lookup"><span data-stu-id="f9598-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9598-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9598-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9598-105">參數</span><span class="sxs-lookup"><span data-stu-id="f9598-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="f9598-106">脫銷列舉原始輸入裝置之[IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)的指標。</span><span class="sxs-lookup"><span data-stu-id="f9598-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f9598-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="f9598-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="f9598-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="f9598-108">HRESULT:</span></span>  
  
 <span data-ttu-id="f9598-109">S_OK-只有在傳回 S_OK 時，Presentationhost.exe 才會使用[IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) 。</span><span class="sxs-lookup"><span data-stu-id="f9598-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="f9598-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f9598-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9598-111">備註</span><span class="sxs-lookup"><span data-stu-id="f9598-111">Remarks</span></span>  
 <span data-ttu-id="f9598-112">未經處理輸入裝置是輸入裝置的集合，包括鍵盤、滑鼠及較不傳統的裝置，例如遙控器。</span><span class="sxs-lookup"><span data-stu-id="f9598-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="f9598-113">擷取未經處理輸入裝置的清單之後，PresentationHost.exe 會向裝置註冊，以接收 WM_INPUT 通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f9598-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9598-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9598-114">See also</span></span>

- [<span data-ttu-id="f9598-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="f9598-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="f9598-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="f9598-116">FilterInputMessage</span></span>](filterinputmessage.md)
