---
title: ISymUnmanagedVariable::GetAddressField3 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 3bdc79a6b6d81f6f0998f052f8bea1bf8af55402
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446115"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="3ae50-102">ISymUnmanagedVariable::GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="3ae50-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="3ae50-103">取得這個變數的第三個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="3ae50-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="3ae50-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="3ae50-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae50-105">語法</span><span class="sxs-lookup"><span data-stu-id="3ae50-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ae50-106">參數</span><span class="sxs-lookup"><span data-stu-id="3ae50-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3ae50-107">脫銷接收第三個位址欄位之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="3ae50-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ae50-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ae50-108">Return Value</span></span>  
 <span data-ttu-id="3ae50-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3ae50-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae50-110">需求</span><span class="sxs-lookup"><span data-stu-id="3ae50-110">Requirements</span></span>  
 <span data-ttu-id="3ae50-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3ae50-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae50-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae50-112">See also</span></span>

- [<span data-ttu-id="3ae50-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="3ae50-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="3ae50-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="3ae50-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="3ae50-115">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="3ae50-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="3ae50-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="3ae50-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
