---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 892da7ec41c75e50f7f2cb086b05e466478e1ced
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484091"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="11daa-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="11daa-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="11daa-103">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="11daa-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11daa-104">語法</span><span class="sxs-lookup"><span data-stu-id="11daa-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11daa-105">參數</span><span class="sxs-lookup"><span data-stu-id="11daa-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="11daa-106">[out]指標`ULONG32`接收大小，以字元為單位，以包含搜尋路徑長度所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="11daa-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11daa-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="11daa-107">Return Value</span></span>  
 <span data-ttu-id="11daa-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="11daa-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11daa-109">需求</span><span class="sxs-lookup"><span data-stu-id="11daa-109">Requirements</span></span>  
 <span data-ttu-id="11daa-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="11daa-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11daa-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11daa-111">See also</span></span>
- [<span data-ttu-id="11daa-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="11daa-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
