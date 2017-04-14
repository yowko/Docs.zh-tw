---
title: "回呼函式 | Microsoft Docs"
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
  - "callback 函式"
  - "平台叫用, 呼叫 Unmanaged 函式"
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 回呼函式
回呼函式是可以協助 Unmanaged DLL 函式完成工作之 Managed 應用程式中的程式碼。  對回呼函式的呼叫會從 Managed 應用程式透過 DLL 函式間接傳遞，然後返回 Managed 實作。  在許多以平台叫用呼叫的 DLL 函式中，有一些需要 Managed 程式碼中的回呼函式才能正確地執行。  
  
 若要從 Managed 程式碼呼叫大部分的 DLL 函式，您必須建立這個函式的 Managed 定義，然後再呼叫它。  處理的方式相當直接。  
  
 使用需要回呼函式的 DLL 函式則有一些額外的步驟。  首先，您必須查閱函式的文件來判斷這個函式是否需要回呼。  接下來，您必須在 Managed 應用程式中建立回呼函式。  最後，呼叫 DLL 函式，傳遞一個指向這個回呼函式的指標做為引數。  下圖所示即為這些步驟的摘要。  
  
 ![平台叫用回呼](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")  
回呼函式和實作  
  
 回呼函式最適合使用於需要重複執行某項工作的情況。  另一種常見的使用情況是配合列舉型別 \(Enumeration\) 函式，例如 Win32 API 中的 **EnumFontFamilies**、**EnumPrinters** 和 **EnumWindows**。  **EnumWindows** 函式會在電腦的所有現有視窗中列舉，呼叫回呼函式 \(Callback Function\) 在每個視窗上執行工作。  如需相關說明和範例，請參閱 [HOW TO：實作回呼函式](../../../docs/framework/interop/how-to-implement-callback-functions.md)。  
  
## 請參閱  
 [如何：實作回呼函式](../../../docs/framework/interop/how-to-implement-callback-functions.md)   
 [呼叫 DLL 函式](../../../docs/framework/interop/calling-a-dll-function.md)