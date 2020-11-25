---
title: ISymUnmanagedENCUpdate::GetLocalVariables 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 9e907450b4ae985ee30d9958eec8baba797b495a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728598"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="4a75f-102">ISymUnmanagedENCUpdate::GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="4a75f-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>

<span data-ttu-id="4a75f-103">取得區域變數。</span><span class="sxs-lookup"><span data-stu-id="4a75f-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a75f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a75f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a75f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a75f-105">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="4a75f-106">在方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="4a75f-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="4a75f-107">在 `ULONG` ，指出參數的大小 `rgLocals` 。</span><span class="sxs-lookup"><span data-stu-id="4a75f-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="4a75f-108">擴展傳回的 [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) 實例陣列。</span><span class="sxs-lookup"><span data-stu-id="4a75f-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4a75f-109">擴展的指標 `ULONG` ，會接收 `rgLocals` 包含區域變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="4a75f-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a75f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4a75f-110">Return Value</span></span>  

 <span data-ttu-id="4a75f-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4a75f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a75f-112">需求</span><span class="sxs-lookup"><span data-stu-id="4a75f-112">Requirements</span></span>  

 <span data-ttu-id="4a75f-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="4a75f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a75f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a75f-114">See also</span></span>

- [<span data-ttu-id="4a75f-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="4a75f-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
