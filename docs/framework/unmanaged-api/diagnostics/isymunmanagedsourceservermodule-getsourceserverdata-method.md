---
title: ISymUnmanagedSourceServerModule::GetSourceServerData 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: 9a3a6c07a9cace0ac9834cdb05925a301285204c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615315"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="79fd2-102">ISymUnmanagedSourceServerModule::GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="79fd2-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="79fd2-103">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="79fd2-103">Returns the source server data for the module.</span></span> <span data-ttu-id="79fd2-104">呼叫端必須使用來釋放資源 `CoTaskMemFree` 。</span><span class="sxs-lookup"><span data-stu-id="79fd2-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79fd2-105">語法</span><span class="sxs-lookup"><span data-stu-id="79fd2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79fd2-106">參數</span><span class="sxs-lookup"><span data-stu-id="79fd2-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="79fd2-107">脫銷的指標， `ULONG32` 接收來源伺服器資料的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="79fd2-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="79fd2-108">脫銷傳回值的指標 `pDataByteCount` 。</span><span class="sxs-lookup"><span data-stu-id="79fd2-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79fd2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="79fd2-109">Return Value</span></span>  
 <span data-ttu-id="79fd2-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="79fd2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79fd2-111">需求</span><span class="sxs-lookup"><span data-stu-id="79fd2-111">Requirements</span></span>  
 <span data-ttu-id="79fd2-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="79fd2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fd2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79fd2-113">See also</span></span>

- [<span data-ttu-id="79fd2-114">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="79fd2-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
