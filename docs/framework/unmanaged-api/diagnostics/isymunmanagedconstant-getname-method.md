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
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441639"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="d7485-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="d7485-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="d7485-103">取得常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7485-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7485-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7485-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7485-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7485-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d7485-106">在參數所指向之緩衝區的長度 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="d7485-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d7485-107">脫銷的指標， `ULONG32` 接收包含名稱所需的緩衝區大小（以字元為單位），包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="d7485-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="d7485-108">脫銷儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d7485-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7485-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d7485-109">Return Value</span></span>  
 <span data-ttu-id="d7485-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d7485-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7485-111">需求</span><span class="sxs-lookup"><span data-stu-id="d7485-111">Requirements</span></span>  
 <span data-ttu-id="d7485-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d7485-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7485-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7485-113">See also</span></span>

- [<span data-ttu-id="d7485-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="d7485-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="d7485-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="d7485-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="d7485-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="d7485-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
