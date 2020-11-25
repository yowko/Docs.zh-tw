---
title: ISymUnmanagedVariable::GetName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: f9da3ca8684da3bbc87146b3b52effdc4f91393d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726882"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="507df-102">ISymUnmanagedVariable::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="507df-102">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="507df-103">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="507df-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507df-104">語法</span><span class="sxs-lookup"><span data-stu-id="507df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="507df-105">參數</span><span class="sxs-lookup"><span data-stu-id="507df-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="507df-106">在參數所指向的緩衝區長度 `pcchName` 。</span><span class="sxs-lookup"><span data-stu-id="507df-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="507df-107">擴展的指標， `ULONG32` 它會接收包含名稱所需的緩衝區大小（以字元為單位），包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="507df-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="507df-108">擴展儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="507df-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="507df-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="507df-109">Return Value</span></span>  

 <span data-ttu-id="507df-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="507df-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507df-111">需求</span><span class="sxs-lookup"><span data-stu-id="507df-111">Requirements</span></span>  

 <span data-ttu-id="507df-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="507df-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507df-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="507df-113">See also</span></span>

- [<span data-ttu-id="507df-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="507df-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
