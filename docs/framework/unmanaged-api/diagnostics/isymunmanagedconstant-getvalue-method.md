---
title: ISymUnmanagedConstant::GetValue 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 7a1c795f4a162699078e91bcaa274253169234e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732836"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="97617-102">ISymUnmanagedConstant::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="97617-102">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="97617-103">取得常數的值。</span><span class="sxs-lookup"><span data-stu-id="97617-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97617-104">語法</span><span class="sxs-lookup"><span data-stu-id="97617-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97617-105">參數</span><span class="sxs-lookup"><span data-stu-id="97617-105">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="97617-106">擴展接收值之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="97617-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97617-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="97617-107">Return Value</span></span>  

 <span data-ttu-id="97617-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="97617-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97617-109">需求</span><span class="sxs-lookup"><span data-stu-id="97617-109">Requirements</span></span>  

 <span data-ttu-id="97617-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="97617-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97617-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97617-111">See also</span></span>

- [<span data-ttu-id="97617-112">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="97617-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="97617-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="97617-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="97617-114">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="97617-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
