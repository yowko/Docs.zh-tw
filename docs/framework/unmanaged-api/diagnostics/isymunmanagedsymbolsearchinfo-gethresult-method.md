---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: a931c15b1c4a9f099d11c43edd324cfcc2793090
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722267"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="6e7f8-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="6e7f8-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="6e7f8-103">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6e7f8-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e7f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e7f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e7f8-105">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="6e7f8-106">擴展HRESULT 的指標。</span><span class="sxs-lookup"><span data-stu-id="6e7f8-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e7f8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e7f8-107">Return Value</span></span>  

 <span data-ttu-id="6e7f8-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6e7f8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e7f8-109">需求</span><span class="sxs-lookup"><span data-stu-id="6e7f8-109">Requirements</span></span>  

 <span data-ttu-id="6e7f8-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6e7f8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7f8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e7f8-111">See also</span></span>

- [<span data-ttu-id="6e7f8-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6e7f8-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
