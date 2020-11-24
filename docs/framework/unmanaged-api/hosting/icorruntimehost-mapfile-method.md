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
ms.openlocfilehash: 60e1d5d49f6f8c6fec060d8751e94410986aa3fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671378"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="63536-102">ICorRuntimeHost::MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="63536-102">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="63536-103">將指定的檔案對應到記憶體。</span><span class="sxs-lookup"><span data-stu-id="63536-103">Maps the specified file into memory.</span></span> <span data-ttu-id="63536-104">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="63536-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63536-105">語法</span><span class="sxs-lookup"><span data-stu-id="63536-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63536-106">參數</span><span class="sxs-lookup"><span data-stu-id="63536-106">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="63536-107">在要對應之檔案的控制碼。</span><span class="sxs-lookup"><span data-stu-id="63536-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="63536-108">擴展開始對應檔的起始記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="63536-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63536-109">需求</span><span class="sxs-lookup"><span data-stu-id="63536-109">Requirements</span></span>  

 <span data-ttu-id="63536-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63536-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63536-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="63536-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63536-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="63536-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63536-113">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="63536-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63536-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63536-114">See also</span></span>

- [<span data-ttu-id="63536-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="63536-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
