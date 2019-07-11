---
title: ISymUnmanagedVariable::GetAddressKind 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b5fd3c5e5a7a706929af849ec3a66dd6c41b3bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778292"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="1e93c-102">ISymUnmanagedVariable::GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="1e93c-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="1e93c-103">取得地址，這個變數的種類。</span><span class="sxs-lookup"><span data-stu-id="1e93c-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e93c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e93c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e93c-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e93c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1e93c-106">[out]指標`ULONG32`所收到的值。</span><span class="sxs-lookup"><span data-stu-id="1e93c-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="1e93c-107">可能的值會定義於[CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="1e93c-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e93c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e93c-108">Return Value</span></span>  
 <span data-ttu-id="1e93c-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e93c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e93c-110">需求</span><span class="sxs-lookup"><span data-stu-id="1e93c-110">Requirements</span></span>  
 <span data-ttu-id="1e93c-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1e93c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e93c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e93c-112">See also</span></span>

- [<span data-ttu-id="1e93c-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="1e93c-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
