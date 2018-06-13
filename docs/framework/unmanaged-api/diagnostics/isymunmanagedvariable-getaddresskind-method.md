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
ms.openlocfilehash: 18e83582a73ba3b2eb2538bcdf60984c46131768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426947"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="f33fc-102">ISymUnmanagedVariable::GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="f33fc-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="f33fc-103">取得這個變數的位址類型。</span><span class="sxs-lookup"><span data-stu-id="f33fc-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f33fc-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f33fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="f33fc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f33fc-106">[out]指標`ULONG32`所收到的值。</span><span class="sxs-lookup"><span data-stu-id="f33fc-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="f33fc-107">可能的值會定義在[CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f33fc-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f33fc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f33fc-108">Return Value</span></span>  
 <span data-ttu-id="f33fc-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f33fc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f33fc-110">需求</span><span class="sxs-lookup"><span data-stu-id="f33fc-110">Requirements</span></span>  
 <span data-ttu-id="f33fc-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f33fc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33fc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f33fc-112">See Also</span></span>  
 [<span data-ttu-id="f33fc-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="f33fc-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
