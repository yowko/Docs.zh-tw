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
ms.openlocfilehash: d5b24ee02a682b38dcf0cb3449f0dff197e91bf9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137822"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="f2749-102">ICorDebugFunction2::EnumerateNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="f2749-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="f2749-103">取得 ICorDebugCodeEnum 物件的介面指標，其中包含這個 ICorDebugFunction2 物件所參考之函式中的機器碼語句。</span><span class="sxs-lookup"><span data-stu-id="f2749-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2749-104">`EnumerateNativeCode` 不會在目前的 .NET Framework 版本中執行。</span><span class="sxs-lookup"><span data-stu-id="f2749-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2749-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2749-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f2749-106">需求</span><span class="sxs-lookup"><span data-stu-id="f2749-106">Requirements</span></span>  
 <span data-ttu-id="f2749-107">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2749-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
