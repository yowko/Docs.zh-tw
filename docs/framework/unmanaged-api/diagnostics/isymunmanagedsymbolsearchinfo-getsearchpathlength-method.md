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
ms.openlocfilehash: 319ba58b5d012cbc0f9ddac0b83e5f3ae2ae062a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446176"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="08b50-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength 方法</span><span class="sxs-lookup"><span data-stu-id="08b50-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="08b50-103">取得搜尋路徑長度。</span><span class="sxs-lookup"><span data-stu-id="08b50-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b50-104">語法</span><span class="sxs-lookup"><span data-stu-id="08b50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08b50-105">參數</span><span class="sxs-lookup"><span data-stu-id="08b50-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="08b50-106">脫銷`ULONG32` 的指標，接收包含搜尋路徑長度所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="08b50-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08b50-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="08b50-107">Return Value</span></span>  
 <span data-ttu-id="08b50-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="08b50-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b50-109">需求</span><span class="sxs-lookup"><span data-stu-id="08b50-109">Requirements</span></span>  
 <span data-ttu-id="08b50-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="08b50-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b50-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="08b50-111">See also</span></span>

- [<span data-ttu-id="08b50-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="08b50-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
