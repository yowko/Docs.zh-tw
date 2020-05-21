---
title: ICorRuntimeHost::MapFile 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762665"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="cfb3d-102">ICorRuntimeHost::MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="cfb3d-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="cfb3d-103">將指定的檔案對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="cfb3d-103">Maps the specified file into memory.</span></span> <span data-ttu-id="cfb3d-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="cfb3d-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb3d-105">語法</span><span class="sxs-lookup"><span data-stu-id="cfb3d-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfb3d-106">參數</span><span class="sxs-lookup"><span data-stu-id="cfb3d-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="cfb3d-107">在要對應之檔案的控制碼。</span><span class="sxs-lookup"><span data-stu-id="cfb3d-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="cfb3d-108">脫銷要開始對應檔案的起始記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="cfb3d-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb3d-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="cfb3d-109">Requirements</span></span>  
 <span data-ttu-id="cfb3d-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cfb3d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb3d-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="cfb3d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfb3d-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cfb3d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfb3d-113">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="cfb3d-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb3d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb3d-114">See also</span></span>

- [<span data-ttu-id="cfb3d-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="cfb3d-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
