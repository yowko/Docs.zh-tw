---
title: "建立類別以包裝 DLL 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d64034f8059dc094b3fc8a71c6a2b7e96fe8d89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a>建立類別以包裝 DLL 函式
將常用 DLL 函式包裝在 Managed 類別中，是封裝平台功能的有效方法。 雖然不會強制您在每個案例這麼做，但提供類別包裝函式十分方便，因為定義 DLL 函式十分麻煩又容易發生錯誤。 如果您是使用 Visual Basic 或 C# 進行程式設計，則必須在類別或 Visual Basic 模組內宣告 DLL 函式。  
  
 在類別內，您可以為每個您想要呼叫的 DLL 函式定義靜態方法。 定義可以包含其他資訊，例如傳遞方法引數時所使用的字元集或呼叫慣例；略過這項資訊，即可選取預設設定。 如需宣告選項和其預設設定的完整清單，請參閱[在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)。  
  
 包裝之後，即可在對任何其他靜態函式呼叫方法時，對函式呼叫方法。 平台叫用會自動處理基礎匯出的函式。  
  
 設計平台叫用的 Managed 類別時，請考慮類別與 DLL 函式之間的關聯性。 例如，您可以：  
  
-   在現有類別內，宣告 DLL 函式。  
  
-   建立每個 DLL 函式的個別類別，來隔離函式，以及輕鬆找到函式。  
  
-   為一組相關 DLL 函式建立一個類別，以形成邏輯群組，並減少額外負荷。  
  
 您可以依需要命名類別和其方法。 如需示範如何建構要與平台叫用搭配使用之 .NET 型宣告的範例，請參閱[使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [識別 DLL 中的函式](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [呼叫 DLL 函式](../../../docs/framework/interop/calling-a-dll-function.md)
