---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 18564e0de8f88e89f8fb71d28ee3bfeccceea4ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507560"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
  
 [out]指標[IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)列舉未經處理輸入的裝置。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:  
  
 S_OK- [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)將只供 PresentationHost.exe 若傳回 S_OK。  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>備註  
 未經處理輸入裝置是輸入裝置的集合，包括鍵盤、滑鼠及較不傳統的裝置，例如遙控器。  
  
 擷取未經處理輸入裝置的清單之後，PresentationHost.exe 會向裝置註冊，以接收 WM_INPUT 通知訊息。  
  
## <a name="see-also"></a>另請參閱
- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
