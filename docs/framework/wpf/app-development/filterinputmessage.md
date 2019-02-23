---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: c3620e13951afddc8de25c314de17704548d2366
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746162"
---
# <a name="filterinputmessage"></a>FilterInputMessage
除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>參數  
 `pMsg`  
  
 [in] 傳送給正在取得未經處理輸入之視窗的 WM_INPUT 訊息。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:  
  
 S_OK - 篩選未處理訊息，可能會進一步處理。  
  
 S_FALSE - 篩選已處理此訊息，應該不會進一步處理。  
  
 E_NOTIMPL – 如果傳回此值，則[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)不會再次呼叫。 這可能是從只想要提供自訂進度的主應用程式傳回，而 PresentationHost.exe 的錯誤使用者介面並不想要被從 PresentationHost.exe 轉送未經處理的輸入訊息。  
  
## <a name="remarks"></a>備註  
 PresentationHost.exe 是各種未經處理輸入裝置 (包括鍵盤、滑鼠及遙控器) 的目標。 有時候，主應用程式中的行為取決於由 PresentationHost.exe 使用的輸入。 例如，主應用程式可能取決於接收特定輸入訊息來判斷是否要顯示特定使用者介面項目。  
  
 若要允許主應用程式接收必要的輸入的訊息，以提供這些行為，PresentationHost.exe 會轉送至裝載的應用程式的適當未經處理輸入的訊息藉由呼叫[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)。  
  
 裝載的應用程式接收未經處理輸入的訊息向未經處理輸入裝置 （人性化介面裝置） 所傳回的集合[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)。  
  
## <a name="see-also"></a>另請參閱
- [WM_INPUT 訊息](/windows/desktop/inputdev/wm-input)
