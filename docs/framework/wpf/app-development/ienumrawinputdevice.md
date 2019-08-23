---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964772"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
此介面列舉未經處理的輸入裝置，並且只供 PresentationHost.exe 使用。  
  
> [!NOTE]
> 僅限在本機用戶端電腦上使用及支援此 API  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|在列舉程式的清單中列舉下一個 `celt` 項目 (也就是 RAWINPUTDEVICE 結構)，連帶 `rgelt` 中列舉項目的實際數目，將這些項目傳回在 `pceltFetched` 中。|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|指示列舉值略過列舉中`celt`的下一個專案, 讓下一次呼叫[IEnumRAWINPUTDEVIC: next](ienumrawinputdevic-next.md)不會傳回這些元素。|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|將列舉序列重設為開頭。|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。|  
  
## <a name="see-also"></a>另請參閱

- [關於原始輸入](/windows/desktop/inputdev/about-raw-input)
