---
title: ISymUnmanagedScope2::GetConstantCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: 59f4d85f1d8f24724a2d7eef332ac3b3387b7c91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725855"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="fcf82-102">ISymUnmanagedScope2::GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="fcf82-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>

<span data-ttu-id="fcf82-103">取得在此範圍內定義之常數的計數。</span><span class="sxs-lookup"><span data-stu-id="fcf82-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf82-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcf82-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcf82-105">參數</span><span class="sxs-lookup"><span data-stu-id="fcf82-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="fcf82-106">擴展的指標， `ULONG32` 它會接收包含常數所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="fcf82-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcf82-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fcf82-107">Return Value</span></span>  

 <span data-ttu-id="fcf82-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fcf82-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcf82-109">需求</span><span class="sxs-lookup"><span data-stu-id="fcf82-109">Requirements</span></span>  

 <span data-ttu-id="fcf82-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="fcf82-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf82-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcf82-111">See also</span></span>

- [<span data-ttu-id="fcf82-112">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="fcf82-112">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
