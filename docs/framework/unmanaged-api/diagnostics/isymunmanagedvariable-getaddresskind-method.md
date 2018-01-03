---
title: "ISymUnmanagedVariable::GetAddressKind 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressKind
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c4651641e3c430379b11698acf29eae450b02b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="f5f74-102">ISymUnmanagedVariable::GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="f5f74-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="f5f74-103">取得這個變數的位址類型。</span><span class="sxs-lookup"><span data-stu-id="f5f74-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f74-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5f74-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5f74-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5f74-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f5f74-106">[out]指標`ULONG32`所收到的值。</span><span class="sxs-lookup"><span data-stu-id="f5f74-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="f5f74-107">可能的值會定義在[CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f5f74-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5f74-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f5f74-108">Return Value</span></span>  
 <span data-ttu-id="f5f74-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f5f74-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f74-110">需求</span><span class="sxs-lookup"><span data-stu-id="f5f74-110">Requirements</span></span>  
 <span data-ttu-id="f5f74-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f5f74-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f74-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5f74-112">See Also</span></span>  
 [<span data-ttu-id="f5f74-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="f5f74-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
