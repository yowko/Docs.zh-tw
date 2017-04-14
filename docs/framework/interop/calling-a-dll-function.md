---
title: "呼叫 DLL 函式 | Microsoft Docs"
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
  - "COM Interop, 平台叫用"
  - "DLL 函式"
  - "與 Unmanaged 程式碼的互通, 平台叫用"
  - "平台叫用, 呼叫 Unmanaged 函式"
  - "Unmanaged 函式"
  - "Unmanaged 函式, 呼叫"
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 呼叫 DLL 函式
雖然呼叫 Unmanaged DLL 函式和呼叫其他 Managed 程式碼幾乎是一樣的，不過還是有一些差異會使 DLL 函式在一開始好像很容易混淆。  這個章節介紹的主題是在描述一些不尋常的呼叫相關問題。  
  
 從平台叫用呼叫傳回的結構必須是在 Managed 和 Unmanaged 程式碼中採用相同表示方式的資料型別。  這類型別稱為「*Blittable 型別*」\(Blittable Type\)，因為在這些型別不需要轉換 \(請參閱 [Blittable 和非 Blittable 類型](../../../docs/framework/interop/blittable-and-non-blittable-types.md)\)。  若要呼叫傳回型別為非 Blittable 結構的函式，您可以定義大小與非 Blittable 型別相同的 Blittable Helper 型別，並且在函式傳回之後轉換資料。  
  
## 在本節中  
 [傳遞結構](../../../docs/framework/interop/passing-structures.md)  
 識別以預先定義之配置傳遞資料結構的問題。  
  
 [回呼函式](../../../docs/framework/interop/callback-functions.md)  
 提供與回呼函式有關的基本資訊。  
  
 [HOW TO：實作回呼函式](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 描述如何在 Managed 程式碼中實作回呼 \(Callback\) 函式。  
  
## 相關章節  
 [使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 描述如何使用平台叫用呼叫 Unmanaged DLL 函式。  
  
 [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 描述如何宣告方法參數，以及將引數傳遞給 Unmanaged 程式庫所匯出的函式。