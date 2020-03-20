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
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176574"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="b9659-102">ISymUnmanagedSourceServerModule::GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="b9659-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="b9659-103">返回模組的源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="b9659-103">Returns the source server data for the module.</span></span> <span data-ttu-id="b9659-104">調用方必須使用`CoTaskMemFree`釋放資源。</span><span class="sxs-lookup"><span data-stu-id="b9659-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9659-105">語法</span><span class="sxs-lookup"><span data-stu-id="b9659-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9659-106">參數</span><span class="sxs-lookup"><span data-stu-id="b9659-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="b9659-107">[出]指向`ULONG32`接收源伺服器資料的大小（以位元組為單位）的指標。</span><span class="sxs-lookup"><span data-stu-id="b9659-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="b9659-108">[出]指向返回`pDataByteCount`值的指標。</span><span class="sxs-lookup"><span data-stu-id="b9659-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9659-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9659-109">Return Value</span></span>  
 <span data-ttu-id="b9659-110">如果方法成功，S_OK;否則，E_FAIL或其他錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="b9659-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9659-111">需求</span><span class="sxs-lookup"><span data-stu-id="b9659-111">Requirements</span></span>  
 <span data-ttu-id="b9659-112">**標題：** 科西姆.伊德爾，科西姆.h</span><span class="sxs-lookup"><span data-stu-id="b9659-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9659-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9659-113">See also</span></span>

- [<span data-ttu-id="b9659-114">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="b9659-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
