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
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176613"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="09ee6-102">ISymUnmanagedScope2::GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="09ee6-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="09ee6-103">獲取在此作用域中定義的本地常量。</span><span class="sxs-lookup"><span data-stu-id="09ee6-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ee6-104">語法</span><span class="sxs-lookup"><span data-stu-id="09ee6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ee6-105">參數</span><span class="sxs-lookup"><span data-stu-id="09ee6-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="09ee6-106">[在]`pcConstants`參數指向的緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="09ee6-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="09ee6-107">[出]指向 的指標`ULONG32`，該指標以字元形式接收包含常量所需的緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="09ee6-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="09ee6-108">[出]存儲常量的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="09ee6-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09ee6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="09ee6-109">Return Value</span></span>  
 <span data-ttu-id="09ee6-110">如果方法成功，S_OK;否則，E_FAIL或其他錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="09ee6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ee6-111">需求</span><span class="sxs-lookup"><span data-stu-id="09ee6-111">Requirements</span></span>  
 <span data-ttu-id="09ee6-112">**標題：** 科西姆.伊德爾，科西姆.h</span><span class="sxs-lookup"><span data-stu-id="09ee6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ee6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09ee6-113">See also</span></span>

- [<span data-ttu-id="09ee6-114">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="09ee6-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
