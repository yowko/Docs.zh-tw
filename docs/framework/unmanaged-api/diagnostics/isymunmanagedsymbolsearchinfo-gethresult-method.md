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
ms.openlocfilehash: 9dcd8282adf200932e86c950bee0b073780ce02d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615302"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="ad051-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="ad051-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="ad051-103">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ad051-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad051-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad051-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad051-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad051-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="ad051-106">脫銷HRESULT 的指標。</span><span class="sxs-lookup"><span data-stu-id="ad051-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad051-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ad051-107">Return Value</span></span>  
 <span data-ttu-id="ad051-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ad051-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad051-109">需求</span><span class="sxs-lookup"><span data-stu-id="ad051-109">Requirements</span></span>  
 <span data-ttu-id="ad051-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ad051-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad051-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad051-111">See also</span></span>

- [<span data-ttu-id="ad051-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ad051-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
