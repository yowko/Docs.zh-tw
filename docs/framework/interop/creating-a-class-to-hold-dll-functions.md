---
title: "建立類別以包裝 DLL 函式 | Microsoft Docs"
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
  - "COM Interop, DLL 函式"
  - "COM Interop, 平台叫用"
  - "DLL 函式"
  - "與 Unmanaged 程式碼的互通, DLL 函式"
  - "與 Unmanaged 程式碼的互通, 平台叫用"
  - "平台叫用, 為函式建立類別"
  - "Unmanaged 函式"
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 建立類別以包裝 DLL 函式
將常用的 DLL 函式包裝在 Managed 類別中是一種封裝平台功能的有效方式。  雖然沒有強制在每種情況下都要這樣做，不過提供類別包裝函式會很方便，因為定義 DLL 函式相當麻煩而且容易出錯。  如果要以 C\# 或 Visual Basic 設計程式，請務必在類別或 Visual Basic 模組中宣告 DLL 函式。  
  
 在類別中，您要針對每一個要呼叫的 DLL 函式定義一個靜態方法。  這個定義可以包括一些其他資訊，例如字元集或用來傳遞方法引數的呼叫慣例；省略這些資訊的話，就等於選取預設值。  如需宣告選項的完整清單和它們的預設值，請參閱[在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)。  
  
 在包裝之後，您就可以像呼叫任何其他靜態函式上的方法一樣地呼叫這個函式上的方法。  平台叫用會自動處理基礎匯出函式。  
  
 在設計平台叫用的 Managed 類別時，請考量類別與 DLL 函式之間的關聯性 \(Relationship\)。  例如，您可以：  
  
-   在現有類別中宣告 DLL 函式。  
  
-   對每一個 DLL 函式建立個別的類別，保持函式隔離而且容易尋找。  
  
-   對一組相關的 DLL 函式建立一個類別，以組成邏輯群組並且減少額外負荷。  
  
 您可以按照您喜歡的方式命名類別和它的方法。  如需示範如何建構 .NET 架構的宣告，以便與平台叫用一起使用的範例，請參閱[使用平台叫用封裝處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)。  
  
## 請參閱  
 [使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)   
 [識別 DLL 中的函式](../../../docs/framework/interop/identifying-functions-in-dlls.md)   
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [呼叫 DLL 函式](../../../docs/framework/interop/calling-a-dll-function.md)