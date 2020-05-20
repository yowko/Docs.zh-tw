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
ms.openlocfilehash: b48d131fa99b65d38856d2b635bf59145db9157e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615237"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="e32db-102">ISymUnmanagedVariable::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="e32db-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="e32db-103">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="e32db-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32db-104">語法</span><span class="sxs-lookup"><span data-stu-id="e32db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e32db-105">參數</span><span class="sxs-lookup"><span data-stu-id="e32db-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e32db-106">在參數所指向之緩衝區的長度 `pcchName` 。</span><span class="sxs-lookup"><span data-stu-id="e32db-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e32db-107">脫銷的指標， `ULONG32` 接收包含名稱所需的緩衝區大小（以字元為單位），包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="e32db-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="e32db-108">脫銷儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e32db-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e32db-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e32db-109">Return Value</span></span>  
 <span data-ttu-id="e32db-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e32db-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e32db-111">需求</span><span class="sxs-lookup"><span data-stu-id="e32db-111">Requirements</span></span>  
 <span data-ttu-id="e32db-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e32db-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32db-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e32db-113">See also</span></span>

- [<span data-ttu-id="e32db-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="e32db-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
