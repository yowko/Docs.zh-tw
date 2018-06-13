---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 2030ad0ac00419280b45555ff11495c74e4274e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547781"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="23f40-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="23f40-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="23f40-103">此介面列舉未經處理的輸入裝置，並且只供 PresentationHost.exe 使用。</span><span class="sxs-lookup"><span data-stu-id="23f40-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23f40-104">僅限在本機用戶端電腦上使用及支援此 API</span><span class="sxs-lookup"><span data-stu-id="23f40-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="23f40-105">成員</span><span class="sxs-lookup"><span data-stu-id="23f40-105">Members</span></span>  
  
|<span data-ttu-id="23f40-106">成員</span><span class="sxs-lookup"><span data-stu-id="23f40-106">Member</span></span>|<span data-ttu-id="23f40-107">描述</span><span class="sxs-lookup"><span data-stu-id="23f40-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23f40-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="23f40-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="23f40-109">在列舉程式的清單中列舉下一個 `celt` 項目 (也就是 RAWINPUTDEVICE 結構)，連帶 `rgelt` 中列舉項目的實際數目，將這些項目傳回在 `pceltFetched` 中。</span><span class="sxs-lookup"><span data-stu-id="23f40-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="23f40-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="23f40-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="23f40-111">略過下一個列舉值會指示`celt`列舉中的項目，因此下次呼叫[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)不會傳回這些項目。</span><span class="sxs-lookup"><span data-stu-id="23f40-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="23f40-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="23f40-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="23f40-113">將列舉序列重設為開頭。</span><span class="sxs-lookup"><span data-stu-id="23f40-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="23f40-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="23f40-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="23f40-115">使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。</span><span class="sxs-lookup"><span data-stu-id="23f40-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23f40-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23f40-116">See Also</span></span>  
 [<span data-ttu-id="23f40-117">關於原始輸入</span><span class="sxs-lookup"><span data-stu-id="23f40-117">About Raw Input</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
