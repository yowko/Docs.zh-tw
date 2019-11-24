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
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445569"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="85f89-102">SetManifestFile 方法</span><span class="sxs-lookup"><span data-stu-id="85f89-102">SetManifestFile Method</span></span>
<span data-ttu-id="85f89-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span><span class="sxs-lookup"><span data-stu-id="85f89-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f89-104">語法</span><span class="sxs-lookup"><span data-stu-id="85f89-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="85f89-105">參數</span><span class="sxs-lookup"><span data-stu-id="85f89-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="85f89-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span><span class="sxs-lookup"><span data-stu-id="85f89-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85f89-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="85f89-107">Return Value</span></span>  
 <span data-ttu-id="85f89-108">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="85f89-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85f89-109">備註</span><span class="sxs-lookup"><span data-stu-id="85f89-109">Remarks</span></span>  
 <span data-ttu-id="85f89-110">Call this before asking for the Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="85f89-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="85f89-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="85f89-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="85f89-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span><span class="sxs-lookup"><span data-stu-id="85f89-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="85f89-113">This enables one to reset the state of the linker to that of initialization time.</span><span class="sxs-lookup"><span data-stu-id="85f89-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f89-114">需求</span><span class="sxs-lookup"><span data-stu-id="85f89-114">Requirements</span></span>  
 <span data-ttu-id="85f89-115">Requires aLink.h</span><span class="sxs-lookup"><span data-stu-id="85f89-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f89-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="85f89-116">See also</span></span>

- [<span data-ttu-id="85f89-117">IALink3 介面</span><span class="sxs-lookup"><span data-stu-id="85f89-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="85f89-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="85f89-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="85f89-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="85f89-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="85f89-120">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="85f89-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
