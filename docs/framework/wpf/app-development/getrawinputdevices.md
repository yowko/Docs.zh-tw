---
title: "GetRawInputDevices | Microsoft Docs"
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
  - "GetRawInputDevices 方法"
  - "未經處理的輸入 [WPF]"
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# GetRawInputDevices
可讓 PresentationHost.exe 探索主應用程式有興趣的未經處理輸入裝置 \(人性化介面裝置\)。  
  
## 語法  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### 參數  
 `ppEnum`  
  
 \[out\] [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) 的指標，用來列舉未經處理輸入裝置。  
  
## 屬性值\/傳回值  
 HRESULT:  
  
 S\_OK \- [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) 將僅供 PresentationHost.exe 使用 \(如果傳回 S\_OK 的話\)。  
  
 E\_NOTIMPL  
  
## 備註  
 未經處理輸入裝置是輸入裝置的集合，包括鍵盤、滑鼠及較不傳統的裝置，例如遙控器。  
  
 擷取未經處理輸入裝置的清單之後，PresentationHost.exe 會向裝置註冊，以接收 WM\_INPUT 通知訊息。  
  
## 請參閱  
 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/winui\/winui\/windowsuserinterface\/userinput\/rawinput\/rawinputreference\/rawinputfunctions\/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)   
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)