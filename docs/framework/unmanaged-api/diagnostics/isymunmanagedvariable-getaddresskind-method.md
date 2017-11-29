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
ms.openlocfilehash: 930b55c98609e5f3bc33f30da766c4556fbe5512
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="941b5-102">ISymUnmanagedVariable::GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="941b5-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="941b5-103">取得這個變數的位址類型。</span><span class="sxs-lookup"><span data-stu-id="941b5-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="941b5-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="941b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="941b5-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="941b5-106">[out]指標`ULONG32`所收到的值。</span><span class="sxs-lookup"><span data-stu-id="941b5-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="941b5-107">可能的值會定義在[CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="941b5-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="941b5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="941b5-108">Return Value</span></span>  
 <span data-ttu-id="941b5-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="941b5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941b5-110">需求</span><span class="sxs-lookup"><span data-stu-id="941b5-110">Requirements</span></span>  
 <span data-ttu-id="941b5-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="941b5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941b5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="941b5-112">See Also</span></span>  
 [<span data-ttu-id="941b5-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="941b5-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
