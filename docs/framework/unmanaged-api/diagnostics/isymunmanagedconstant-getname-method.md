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
ms.openlocfilehash: fca7b11a83b5a695feae82fe5f25218f87afbce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732888"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="bab9a-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="bab9a-102">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="bab9a-103">取得常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bab9a-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="bab9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bab9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="bab9a-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="bab9a-106">在參數所指向的緩衝區長度 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="bab9a-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bab9a-107">擴展的指標， `ULONG32` 它會接收包含名稱所需的緩衝區大小（以字元為單位），包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="bab9a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="bab9a-108">擴展儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bab9a-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bab9a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="bab9a-109">Return Value</span></span>  

 <span data-ttu-id="bab9a-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bab9a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab9a-111">需求</span><span class="sxs-lookup"><span data-stu-id="bab9a-111">Requirements</span></span>  

 <span data-ttu-id="bab9a-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bab9a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab9a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bab9a-113">See also</span></span>

- [<span data-ttu-id="bab9a-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="bab9a-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="bab9a-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="bab9a-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="bab9a-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="bab9a-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
