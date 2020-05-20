---
title: GetFileVersion 函式
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 2dd004a44b20d48dafc72711ac23abcb55739224
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617196"
---
# <a name="getfileversion-function"></a><span data-ttu-id="7ab23-102">GetFileVersion 函式</span><span class="sxs-lookup"><span data-stu-id="7ab23-102">GetFileVersion Function</span></span>
<span data-ttu-id="7ab23-103">使用指定的緩衝區，取得指定檔案的 common language runtime （CLR）版本資訊。</span><span class="sxs-lookup"><span data-stu-id="7ab23-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="7ab23-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="7ab23-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab23-105">語法</span><span class="sxs-lookup"><span data-stu-id="7ab23-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab23-106">參數</span><span class="sxs-lookup"><span data-stu-id="7ab23-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="7ab23-107">在要檢查之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="7ab23-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="7ab23-108">[in、out]為傳回的版本資訊所配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7ab23-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7ab23-109">在的大小（以寬字元為單位） `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7ab23-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7ab23-110">脫銷傳回之的大小（以位元組為單位） `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7ab23-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab23-111">需求</span><span class="sxs-lookup"><span data-stu-id="7ab23-111">Requirements</span></span>  
 <span data-ttu-id="7ab23-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab23-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab23-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7ab23-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ab23-114">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab23-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab23-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ab23-115">See also</span></span>

- [<span data-ttu-id="7ab23-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="7ab23-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
