---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614574"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="a1d06-102">ISymUnmanagedENCUpdate::GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="a1d06-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="a1d06-103">取得本機變數的數目。</span><span class="sxs-lookup"><span data-stu-id="a1d06-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d06-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1d06-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1d06-105">參數</span><span class="sxs-lookup"><span data-stu-id="a1d06-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="a1d06-106">在方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="a1d06-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="a1d06-107">脫銷的指標， `ULONG32` 接收包含區域變數數目所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="a1d06-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1d06-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a1d06-108">Return Value</span></span>  
 <span data-ttu-id="a1d06-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a1d06-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d06-110">需求</span><span class="sxs-lookup"><span data-stu-id="a1d06-110">Requirements</span></span>  
 <span data-ttu-id="a1d06-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a1d06-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d06-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1d06-112">See also</span></span>

- [<span data-ttu-id="a1d06-113">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="a1d06-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
