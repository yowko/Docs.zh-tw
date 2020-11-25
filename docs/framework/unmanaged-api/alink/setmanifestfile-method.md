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
ms.openlocfilehash: a4518e93db887dbdc4397636479be8bf5a705c2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733720"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="5e87f-102">SetManifestFile 方法</span><span class="sxs-lookup"><span data-stu-id="5e87f-102">SetManifestFile Method</span></span>

<span data-ttu-id="5e87f-103">可讓您指定或重設連結器在建立元件時所使用的資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="5e87f-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e87f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e87f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e87f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e87f-105">Parameters</span></span>  

 `pszFile`  
  
 <span data-ttu-id="5e87f-106">將其內容放入 Win32 資源 blob 的資訊清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="5e87f-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e87f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e87f-107">Return Value</span></span>  

 <span data-ttu-id="5e87f-108">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5e87f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e87f-109">備註</span><span class="sxs-lookup"><span data-stu-id="5e87f-109">Remarks</span></span>  

 <span data-ttu-id="5e87f-110">要求 Win32ResBlob 之前，請先呼叫此程式。</span><span class="sxs-lookup"><span data-stu-id="5e87f-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="5e87f-111">參數的值 `pszFile` 是資訊清單檔案的名稱，其內容會被讀取並放在識別碼為 RT_MANIFEST 的 Win32 資源中。</span><span class="sxs-lookup"><span data-stu-id="5e87f-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="5e87f-112">使用 Null 的參數呼叫時，會清除任何先前讀取的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="5e87f-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="5e87f-113">如此一來，就能將連結器的狀態重設為初始化時間的值。</span><span class="sxs-lookup"><span data-stu-id="5e87f-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e87f-114">需求</span><span class="sxs-lookup"><span data-stu-id="5e87f-114">Requirements</span></span>  

 <span data-ttu-id="5e87f-115">需要 aLink。h</span><span class="sxs-lookup"><span data-stu-id="5e87f-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e87f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e87f-116">See also</span></span>

- [<span data-ttu-id="5e87f-117">IALink3 介面</span><span class="sxs-lookup"><span data-stu-id="5e87f-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="5e87f-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="5e87f-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="5e87f-119">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="5e87f-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5e87f-120">Al.exe (元件連結器) </span><span class="sxs-lookup"><span data-stu-id="5e87f-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
