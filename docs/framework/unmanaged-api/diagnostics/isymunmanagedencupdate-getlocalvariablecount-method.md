---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7d557e2111a26c0865c20d8eb952c4d42b5604e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436055"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="8659b-102">ISymUnmanagedENCUpdate::GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="8659b-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="8659b-103">取得區域變數的數目。</span><span class="sxs-lookup"><span data-stu-id="8659b-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8659b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8659b-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8659b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8659b-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="8659b-106">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8659b-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="8659b-107">[out]指標`ULONG32`接收以字元為單位，以包含區域變數的數目所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="8659b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8659b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8659b-108">Return Value</span></span>  
 <span data-ttu-id="8659b-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8659b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8659b-110">需求</span><span class="sxs-lookup"><span data-stu-id="8659b-110">Requirements</span></span>  
 <span data-ttu-id="8659b-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8659b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8659b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8659b-112">See Also</span></span>  
 [<span data-ttu-id="8659b-113">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="8659b-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
