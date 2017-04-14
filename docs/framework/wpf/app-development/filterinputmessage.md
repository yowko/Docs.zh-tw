---
title: "FilterInputMessage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FilterInputMessage 方法"
  - "未經處理的輸入 [WPF]"
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# FilterInputMessage
除非傳回 E\_NOTIMPL，否則每當收到訊息時，都會由 PresentationHost.exe 呼叫。  
  
## 語法  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### 參數  
 `pMsg`  
  
 \[in\] 傳送給正在取得未經處理輸入之視窗的 WM\_INPUT 訊息。  
  
## 屬性值\/傳回值  
 HRESULT:  
  
 S\_OK \- 篩選未處理訊息，可能會進一步處理。  
  
 S\_FALSE \- 篩選已處理此訊息，應該不會進一步處理。  
  
 E\_NOTIMPL – 如果傳回此值，則不會再次呼叫 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)。  這可能是從只想要提供自訂進度的主應用程式傳回，而 PresentationHost.exe 的錯誤使用者介面並不想要被從 PresentationHost.exe 轉送未經處理的輸入訊息。  
  
## 備註  
 PresentationHost.exe 是各種未經處理輸入裝置 \(包括鍵盤、滑鼠及遙控器\) 的目標。  有時候，主應用程式中的行為取決於由 PresentationHost.exe 使用的輸入。  例如，主應用程式可能取決於接收特定輸入訊息來判斷是否要顯示特定使用者介面項目。  
  
 若要讓主應用程式接收必要的輸入訊息，以提供這些行為，PresentationHost.exe 會呼叫 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)，以將適當的未經處理輸入訊息轉送至裝載的應用程式。  
  
 裝載的應用程式會向 [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md) 傳回的一組未經處理輸入裝置 \(人性化介面裝置\) 註冊，以接收未經處理輸入訊息。  
  
## 請參閱  
 [WM\_INPUT 通知](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)