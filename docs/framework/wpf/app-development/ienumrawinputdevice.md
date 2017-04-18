---
title: "IEnumRAWINPUTDEVICE | Microsoft Docs"
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
  - "IEnumRAWINPUTDEVICE 介面"
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# IEnumRAWINPUTDEVICE
此介面列舉未經處理的輸入裝置，並且只供 PresentationHost.exe 使用。  
  
> [!NOTE]
>  僅限在本機用戶端電腦上使用及支援此 API  
  
## 成員  
  
|成員|描述|  
|--------|--------|  
|[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|在列舉程式的清單中列舉下一個 `celt` 項目 \(也就是 RAWINPUTDEVICE 結構\)，連帶 `pceltFetched` 中列舉項目的實際數目，將這些項目傳回在 `rgelt` 中。|  
|[IEnumRAWINPUTDEVIC:Skip](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|指示列舉程式略過列舉中下一個 `celt` 項目，這樣在下次呼叫[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)時，將不會傳回那些項目。|  
|[IEnumRAWINPUTDEVIC:Reset](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|將列舉序列重設為開頭。|  
|[IEnumRAWINPUTDEVIC:Clone](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。|  
  
## 請參閱  
 [關於未經處理的輸入](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)