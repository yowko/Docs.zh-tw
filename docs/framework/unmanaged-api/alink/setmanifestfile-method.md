---
title: SetManifestFile 方法
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8398c16b27836b772e8ac56ee1f7e8494f4be0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403565"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="42741-102">SetManifestFile 方法</span><span class="sxs-lookup"><span data-stu-id="42741-102">SetManifestFile Method</span></span>
<span data-ttu-id="42741-103">可讓您指定或重設連結器會使用時，它會建立組件資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="42741-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42741-104">語法</span><span class="sxs-lookup"><span data-stu-id="42741-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42741-105">參數</span><span class="sxs-lookup"><span data-stu-id="42741-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="42741-106">其內容會放入 Win32 資源 blob 資訊清單檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="42741-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42741-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="42741-107">Return Value</span></span>  
 <span data-ttu-id="42741-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="42741-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42741-109">備註</span><span class="sxs-lookup"><span data-stu-id="42741-109">Remarks</span></span>  
 <span data-ttu-id="42741-110">Win32ResBlob 要求之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="42741-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="42741-111">值`pszFile`參數就是其內容會讀取並放入 RT_MANIFEST 的識別碼使用的 Win32 資源資訊清單檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="42741-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="42741-112">當使用 NULL 參數呼叫，會清除任何先前讀取資訊清單。</span><span class="sxs-lookup"><span data-stu-id="42741-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="42741-113">這可讓連結器的狀態重設為初始設定時。</span><span class="sxs-lookup"><span data-stu-id="42741-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42741-114">需求</span><span class="sxs-lookup"><span data-stu-id="42741-114">Requirements</span></span>  
 <span data-ttu-id="42741-115">需要 aLink.h</span><span class="sxs-lookup"><span data-stu-id="42741-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42741-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42741-116">See Also</span></span>  
 [<span data-ttu-id="42741-117">IALink3 介面</span><span class="sxs-lookup"><span data-stu-id="42741-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="42741-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="42741-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="42741-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="42741-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="42741-120">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="42741-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
