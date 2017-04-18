---
title: "與 Unmanaged 程式碼互通 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, 與 Unmanaged 程式碼的互通"
  - "元件 [.NET Framework], 與 Unmanaged 程式碼的互通"
  - "與 Unmanaged 程式碼的互通"
  - "與 Unmanaged 程式碼的互通, 關於互通"
  - "Managed 程式碼, 與 Unmanaged 程式碼的互通"
  - "Unmanaged 程式碼"
  - "Unmanaged 程式碼, 互通"
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 與 Unmanaged 程式碼互通
.NET Framework 可提升與 COM 元件、COM\+ 服務、外部型別程式庫，以及許多作業系統服務的互動。  資料型別、方法簽章和錯誤處理機制在 Managed 和 Unmanaged 物件模型間各有不同。  為了簡化 .NET Framework 元件與 Unmanaged 程式碼之間的互通並減輕轉換的負荷，Common Language Runtime 會隱藏這些物件模型在用戶端和伺服器兩者之間的差異。  
  
 在執行階段控制之下執行的程式碼稱為 Managed 程式碼。  反之，在執行階段以外執行的程式碼就稱為 Unmanaged 程式碼。  COM 元件、ActiveX 介面及 Win32 API 函式都是 Unmanaged 程式碼的範例。  
  
## 在本節中  
 [Interoperating with Unmanaged Code How\-to Topics](http://msdn.microsoft.com/zh-tw/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 提供與 Unmanaged 程式碼相互溝通的概念性文件中所有 HOW TO 主題的連結。  
  
 [將 COM 元件公開給 .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 說明如何從 .NET Framework 應用程式使用 COM 元件。  
  
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 說明如何從 COM 應用程式使用 .NET Framework 元件。  
  
 [使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 描述如何使用平台叫用呼叫 Unmanaged DLL 函式。  
  
 [互通的設計考量](http://msdn.microsoft.com/zh-tw/b59637f6-fe35-40d6-ae72-901e7a707689)  
 提供撰寫整合式 COM 元件的秘訣。  
  
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)  
 描述 COM Interop 和平台叫用的封送處理 \(Marshaling\)。  
  
 [如何：對應 HRESULT 和例外狀況](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 描述例外狀況 \(Exception\) 和 HRESULT 之間的對應。  
  
 [Interoperating Using Generic Types](http://msdn.microsoft.com/zh-tw/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 描述用於 COM Interop 中時的泛型型別之行為。  
  
## 相關章節  
 [Advanced COM Interoperability](http://msdn.microsoft.com/zh-tw/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 提供關於將 COM 元件加入至 .NET Framework 應用程式的詳細資訊連結。