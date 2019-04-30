---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949561"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
此介面列舉未經處理的輸入裝置，並且只供 PresentationHost.exe 使用。  
  
> [!NOTE]
>  僅限在本機用戶端電腦上使用及支援此 API  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|在列舉程式的清單中列舉下一個 `celt` 項目 (也就是 RAWINPUTDEVICE 結構)，連帶 `rgelt` 中列舉項目的實際數目，將這些項目傳回在 `pceltFetched` 中。|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|指示列舉程式略過下一個`celt`列舉中的項目，因此下次呼叫[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)將不會傳回這些項目。|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|將列舉序列重設為開頭。|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。|  
  
## <a name="see-also"></a>另請參閱

- [關於未經處理的輸入](/windows/desktop/inputdev/about-raw-input)
