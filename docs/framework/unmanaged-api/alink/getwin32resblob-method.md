---
title: "GetWin32ResBlob 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f09bfd3ccfd3ac37854d70c226f40b17f86ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="42b47-102">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="42b47-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="42b47-103">擷取 Win32 資源 blob。</span><span class="sxs-lookup"><span data-stu-id="42b47-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="42b47-104">設定組件選項之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="42b47-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b47-105">語法</span><span class="sxs-lookup"><span data-stu-id="42b47-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42b47-106">參數</span><span class="sxs-lookup"><span data-stu-id="42b47-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="42b47-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="42b47-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="42b47-108">用來擷取建構的 Win32 版本資源時所要使用的檔名語彙基元檔案</span><span class="sxs-lookup"><span data-stu-id="42b47-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="42b47-109">如果檔案是 DLL，false EXE，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="42b47-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="42b47-110">要插入資源 blob 的選擇性圖示。</span><span class="sxs-lookup"><span data-stu-id="42b47-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="42b47-111">接收資源 blob。</span><span class="sxs-lookup"><span data-stu-id="42b47-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="42b47-112">接收 blob 的大小。</span><span class="sxs-lookup"><span data-stu-id="42b47-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42b47-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="42b47-113">Return Value</span></span>  
 <span data-ttu-id="42b47-114">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="42b47-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42b47-115">需求</span><span class="sxs-lookup"><span data-stu-id="42b47-115">Requirements</span></span>  
 <span data-ttu-id="42b47-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="42b47-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b47-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="42b47-117">See Also</span></span>  
 [<span data-ttu-id="42b47-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="42b47-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="42b47-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="42b47-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="42b47-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="42b47-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
