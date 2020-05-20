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
ms.openlocfilehash: 8e20d2e0f3d5cb6dc7444c8e78665b6c8b82d2de
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441470"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="5cada-102">ISymUnmanagedConstant::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="5cada-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="5cada-103">取得常數的值。</span><span class="sxs-lookup"><span data-stu-id="5cada-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cada-104">語法</span><span class="sxs-lookup"><span data-stu-id="5cada-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cada-105">參數</span><span class="sxs-lookup"><span data-stu-id="5cada-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="5cada-106">脫銷接收值之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="5cada-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cada-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5cada-107">Return Value</span></span>  
 <span data-ttu-id="5cada-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5cada-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cada-109">需求</span><span class="sxs-lookup"><span data-stu-id="5cada-109">Requirements</span></span>  
 <span data-ttu-id="5cada-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="5cada-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cada-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cada-111">See also</span></span>

- [<span data-ttu-id="5cada-112">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="5cada-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="5cada-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5cada-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="5cada-114">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="5cada-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
