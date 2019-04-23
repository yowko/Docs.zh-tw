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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113018"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="afbce-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="afbce-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="afbce-103">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="afbce-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afbce-104">語法</span><span class="sxs-lookup"><span data-stu-id="afbce-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afbce-105">參數</span><span class="sxs-lookup"><span data-stu-id="afbce-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="afbce-106">[out]HRESULT 指標。</span><span class="sxs-lookup"><span data-stu-id="afbce-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afbce-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="afbce-107">Return Value</span></span>  
 <span data-ttu-id="afbce-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="afbce-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afbce-109">需求</span><span class="sxs-lookup"><span data-stu-id="afbce-109">Requirements</span></span>  
 <span data-ttu-id="afbce-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="afbce-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbce-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afbce-111">See also</span></span>

- [<span data-ttu-id="afbce-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="afbce-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
