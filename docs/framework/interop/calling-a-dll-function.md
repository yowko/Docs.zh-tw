---
title: 呼叫 DLL 函式
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051876"
---
# <a name="calling-a-dll-function"></a>呼叫 DLL 函式
雖然呼叫 Unmanaged DLL 函式與呼叫其他 Managed 程式碼幾乎完全相同，但具有一開始讓 DLL 函式混淆的差異。 本節介紹描述一些異常呼叫相關問題的主題。  
  
 從平台叫用呼叫傳回的結構必須是 Managed 和 Unmanaged 程式碼中的呈現方式相同的資料類型。 這類類型稱為「Blittable 類型」，因為它們不需要轉換 (請參閱 [Blittable 和非 Blittable 類型](blittable-and-non-blittable-types.md))。 若要呼叫的函式將非 Blittable 結構當成其傳回類型，您可以定義與非 Blittable 類型大小相同的 Blittable 協助程式類型，並在傳回函式之後轉換資料。  
  
## <a name="in-this-section"></a>本節內容  
 [傳遞結構](passing-structures.md)  
 識別傳遞具有預先定義配置之資料結構的問題。  
  
 [回呼函式](callback-functions.md)  
 提供回呼函式的基本資訊。  
  
 [如何：實作回呼函式](how-to-implement-callback-functions.md)  
 描述如何在 Managed 程式碼中實作回呼函式。  
  
## <a name="related-sections"></a>相關章節  
 [使用 Unmanaged DLL 函式](consuming-unmanaged-dll-functions.md)  
 描述如何使用平台叫用呼叫 Unmanaged DLL 函式。  
  
 [使用平台叫用封送處理資料](marshaling-data-with-platform-invoke.md)  
 描述如何宣告方法參數，以及將引數傳遞給 Unmanaged 程式庫所匯出的函式。
