---
title: ISymUnmanagedConstant::GetName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 924feaeb91b42404461ad5d276c0cb77279d4dc4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449286"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="ef3a3-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="ef3a3-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="ef3a3-103">取得常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef3a3-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef3a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef3a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef3a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef3a3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ef3a3-106">在`szName` 參數所指向的緩衝區長度。</span><span class="sxs-lookup"><span data-stu-id="ef3a3-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ef3a3-107">脫銷`ULONG32` 的指標，接收包含名稱所需的緩衝區大小（以字元為單位），包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="ef3a3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="ef3a3-108">脫銷儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ef3a3-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef3a3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef3a3-109">Return Value</span></span>  
 <span data-ttu-id="ef3a3-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ef3a3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef3a3-111">需求</span><span class="sxs-lookup"><span data-stu-id="ef3a3-111">Requirements</span></span>  
 <span data-ttu-id="ef3a3-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ef3a3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3a3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef3a3-113">See also</span></span>

- [<span data-ttu-id="ef3a3-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="ef3a3-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="ef3a3-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="ef3a3-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="ef3a3-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="ef3a3-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
