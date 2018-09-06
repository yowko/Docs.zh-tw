---
title: IAssemblyCacheItem::CreateStream 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787229"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="d6cc8-102">IAssemblyCacheItem::CreateStream 方法</span><span class="sxs-lookup"><span data-stu-id="d6cc8-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="d6cc8-103">建立具有指定的名稱和格式的資料流。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6cc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6cc8-104">Syntax</span></span>  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6cc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6cc8-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d6cc8-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="d6cc8-107">[in]若要建立資料流的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="d6cc8-108">[in]若要串流處理檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="d6cc8-109">[in]支援下列值： 格式特有的旗標。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="d6cc8-110">[out]傳回的位址指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="d6cc8-111">[in，選用]所參考的資料流的大小上限`ppIStream`。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6cc8-112">需求</span><span class="sxs-lookup"><span data-stu-id="d6cc8-112">Requirements</span></span>  
 <span data-ttu-id="d6cc8-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cc8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6cc8-114">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d6cc8-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6cc8-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6cc8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cc8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6cc8-116">See Also</span></span>  
 [<span data-ttu-id="d6cc8-117">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="d6cc8-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
