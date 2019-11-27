---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 74002ce9c76eebaa3ea5860b09cd3e7c9a884f8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448662"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="f4e06-102">ISymENCUnmanagedMethod::GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f4e06-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="f4e06-103">取得與位移相關聯之行的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f4e06-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e06-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4e06-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4e06-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4e06-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="f4e06-106">在包含位移的 `ULONG32`。</span><span class="sxs-lookup"><span data-stu-id="f4e06-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f4e06-107">在指出 `szName` 緩衝區大小的 `ULONG32`。</span><span class="sxs-lookup"><span data-stu-id="f4e06-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f4e06-108">脫銷`ULONG32` 的指標，接收包含檔案名所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="f4e06-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="f4e06-109">脫銷包含檔案名的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f4e06-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4e06-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4e06-110">Return Value</span></span>  
 <span data-ttu-id="f4e06-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f4e06-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e06-112">需求</span><span class="sxs-lookup"><span data-stu-id="f4e06-112">Requirements</span></span>  
 <span data-ttu-id="f4e06-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="f4e06-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e06-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4e06-114">See also</span></span>

- [<span data-ttu-id="f4e06-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="f4e06-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
