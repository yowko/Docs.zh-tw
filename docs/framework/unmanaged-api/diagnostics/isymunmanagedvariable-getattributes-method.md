---
title: "ISymUnmanagedVariable::GetAttributes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAttributes
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41bdbf20d3905ba218802a6801c7394b237f6e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="2fea2-102">ISymUnmanagedVariable::GetAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="2fea2-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="2fea2-103">取得這個變數的屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="2fea2-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fea2-104">語法</span><span class="sxs-lookup"><span data-stu-id="2fea2-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fea2-105">參數</span><span class="sxs-lookup"><span data-stu-id="2fea2-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2fea2-106">[out]指標`ULONG32`接收的屬性。</span><span class="sxs-lookup"><span data-stu-id="2fea2-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="2fea2-107">傳回的值將會是其中一個定義中的值[CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2fea2-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fea2-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2fea2-108">Return Value</span></span>  
 <span data-ttu-id="2fea2-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="2fea2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fea2-110">需求</span><span class="sxs-lookup"><span data-stu-id="2fea2-110">Requirements</span></span>  
 <span data-ttu-id="2fea2-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2fea2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fea2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fea2-112">See Also</span></span>  
 [<span data-ttu-id="2fea2-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="2fea2-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
