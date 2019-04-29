---
title: 偵錯全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698521"
---
# <a name="debugging-global-static-functions"></a>偵錯全域靜態函式
本節說明偵錯 API 所使用的 Unmanaged 全域靜態函式。  
  
## <a name="in-this-section"></a>本節內容  
 [_EFN_GetManagedExcepStack 函式](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。  
  
 [_EFN_GetManagedObjectFieldInfo 函式](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。  
  
 [_EFN_GetManagedObjectName 函式](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 使用提供的 Managed 物件指標，以取得類型的名稱。  
  
 [_EFN_StackTrace 函式](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 提供 Managed 堆疊追蹤以及 `CONTEXT` 記錄之陣列的文字表示，再各提供一個文字表示給 Unmanaged 和 Managed 程式碼之間的每個轉換。  
  
 [CLRDataCreateInstance 函式](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 由通用語言執行階段 (CLR) 資料存取服務呼叫，以建立指定的介面物件給指定的目標處理序。  
  
 [PFN_CLRDataCreateInstance 函式指標](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 指向由 CLR 資料存取服務所呼叫的函式，以建立指定的介面物件給指定的目標處理序。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
