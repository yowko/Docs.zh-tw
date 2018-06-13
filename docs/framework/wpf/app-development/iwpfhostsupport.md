---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 51964358d27a16d9840e29be06c11f57de2fad23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548190"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
裝載應用程式，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內容 PresentationHost.exe 透過實作這個介面來提供主機和 PresentationHost.exe 之間的整合點。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 如網頁瀏覽器的應用程式可以裝載[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]內容，包括[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]和鬆散的 XAML。 主機[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]內容，[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]應用程式建立的執行個體[WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=97911)。 要裝載[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]建立 PresentationHost.exe，提供裝載的執行個體[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)]的主控件中的顯示內容[WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=97911)。  
  
 啟用的整合`IWpfHostSupport`允許 PresentationHost.exe 至：  
  
-   探索並向原始輸入裝置 （人性化介面裝置） 的主應用程式有興趣。  
  
-   輸入從接收訊息的已註冊的原始輸入的裝置和轉寄的適當訊息主應用程式。  
  
-   查詢主應用程式自訂進度和錯誤的使用者介面。  
  
> [!NOTE]
>  僅限在本機用戶端電腦上使用及支援此 API  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 (人性化介面裝置)。|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|除非傳回 E_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|根據預設，PresentationHost.exe 提供它自己的部署進度和部署錯誤會顯示部署的 WPF 內容時的使用者介面。|
