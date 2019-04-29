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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1534955c1f7cfd37732a08b0b33cda5bff8a8aab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638615"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="89dc3-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="89dc3-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="89dc3-103">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="89dc3-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89dc3-104">語法</span><span class="sxs-lookup"><span data-stu-id="89dc3-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89dc3-105">參數</span><span class="sxs-lookup"><span data-stu-id="89dc3-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="89dc3-106">[out]HRESULT 指標。</span><span class="sxs-lookup"><span data-stu-id="89dc3-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89dc3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="89dc3-107">Return Value</span></span>  
 <span data-ttu-id="89dc3-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="89dc3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89dc3-109">需求</span><span class="sxs-lookup"><span data-stu-id="89dc3-109">Requirements</span></span>  
 <span data-ttu-id="89dc3-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="89dc3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89dc3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89dc3-111">See also</span></span>

- [<span data-ttu-id="89dc3-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="89dc3-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
