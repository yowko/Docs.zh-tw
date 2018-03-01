---
title: "ISymUnmanagedENCUpdate::GetLocalVariableCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c86b2988d414d091bc23d29bd79f518a756d688
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="e1478-102">ISymUnmanagedENCUpdate::GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="e1478-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="e1478-103">取得區域變數的數目。</span><span class="sxs-lookup"><span data-stu-id="e1478-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1478-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1478-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1478-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1478-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="e1478-106">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e1478-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="e1478-107">[out]指標`ULONG32`接收以字元為單位，以包含區域變數的數目所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e1478-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1478-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1478-108">Return Value</span></span>  
 <span data-ttu-id="e1478-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1478-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1478-110">需求</span><span class="sxs-lookup"><span data-stu-id="e1478-110">Requirements</span></span>  
 <span data-ttu-id="e1478-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e1478-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1478-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1478-112">See Also</span></span>  
 [<span data-ttu-id="e1478-113">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="e1478-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
