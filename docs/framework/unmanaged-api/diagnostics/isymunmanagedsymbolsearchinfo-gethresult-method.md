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
ms.openlocfilehash: 775f5a2129a635c79a48d5218d5eb91ee83ee779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427879"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="82f24-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="82f24-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="82f24-103">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="82f24-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f24-104">語法</span><span class="sxs-lookup"><span data-stu-id="82f24-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82f24-105">參數</span><span class="sxs-lookup"><span data-stu-id="82f24-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="82f24-106">[out]HRESULT 指標。</span><span class="sxs-lookup"><span data-stu-id="82f24-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82f24-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="82f24-107">Return Value</span></span>  
 <span data-ttu-id="82f24-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="82f24-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f24-109">需求</span><span class="sxs-lookup"><span data-stu-id="82f24-109">Requirements</span></span>  
 <span data-ttu-id="82f24-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="82f24-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f24-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82f24-111">See Also</span></span>  
 [<span data-ttu-id="82f24-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="82f24-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
