---
title: GetFileDef 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6a8a9aedc5c2b09c6e6f6014142bce44f3a8297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668596"
---
# <a name="getfiledef-method"></a><span data-ttu-id="b0451-102">GetFileDef 方法</span><span class="sxs-lookup"><span data-stu-id="b0451-102">GetFileDef Method</span></span>
<span data-ttu-id="b0451-103">擷取中繼資料 （而不是由 ALink 指派的權杖） 中所使用的實際 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b0451-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0451-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0451-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0451-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0451-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b0451-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0451-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="b0451-107">語彙基元的加入的檔案從 AddFile 方法或 AddImport 方法擷取。</span><span class="sxs-lookup"><span data-stu-id="b0451-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="b0451-108">接收 FileDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b0451-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0451-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b0451-109">Return Value</span></span>  
 <span data-ttu-id="b0451-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b0451-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0451-111">需求</span><span class="sxs-lookup"><span data-stu-id="b0451-111">Requirements</span></span>  
 <span data-ttu-id="b0451-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="b0451-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0451-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0451-113">See also</span></span>
- [<span data-ttu-id="b0451-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="b0451-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b0451-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="b0451-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b0451-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="b0451-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
