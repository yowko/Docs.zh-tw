---
title: ISymUnmanagedScope2::GetConstants 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: df42e58a9bb3bf00b3fa4df45086dc2219658e25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725842"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="2d67f-102">ISymUnmanagedScope2::GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="2d67f-102">ISymUnmanagedScope2::GetConstants Method</span></span>

<span data-ttu-id="2d67f-103">取得在此範圍內定義的本機常數。</span><span class="sxs-lookup"><span data-stu-id="2d67f-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d67f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d67f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d67f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d67f-105">Parameters</span></span>  

 `cConstants`  
 <span data-ttu-id="2d67f-106">在參數所指向的緩衝區長度 `pcConstants` 。</span><span class="sxs-lookup"><span data-stu-id="2d67f-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="2d67f-107">擴展的指標， `ULONG32` 它會接收包含常數所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d67f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="2d67f-108">擴展儲存常數的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2d67f-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d67f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d67f-109">Return Value</span></span>  

 <span data-ttu-id="2d67f-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2d67f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d67f-111">需求</span><span class="sxs-lookup"><span data-stu-id="2d67f-111">Requirements</span></span>  

 <span data-ttu-id="2d67f-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2d67f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d67f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d67f-113">See also</span></span>

- [<span data-ttu-id="2d67f-114">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="2d67f-114">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
