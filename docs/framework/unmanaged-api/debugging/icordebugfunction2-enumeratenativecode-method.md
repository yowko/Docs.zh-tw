---
title: ICorDebugFunction2::EnumerateNativeCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
ms.openlocfilehash: 2cac4a3120e842bde9ad708a251682421fd4ca93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696072"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="b1e65-102">ICorDebugFunction2::EnumerateNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="b1e65-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>

<span data-ttu-id="b1e65-103">取得 ICorDebugCodeEnum 物件的介面指標，其中包含這個 ICorDebugFunction2 物件所參考之函式中的機器碼語句。</span><span class="sxs-lookup"><span data-stu-id="b1e65-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1e65-104">`EnumerateNativeCode` 在目前的 .NET Framework 版本中不會執行。</span><span class="sxs-lookup"><span data-stu-id="b1e65-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e65-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1e65-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b1e65-106">需求</span><span class="sxs-lookup"><span data-stu-id="b1e65-106">Requirements</span></span>  

 <span data-ttu-id="b1e65-107">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1e65-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
