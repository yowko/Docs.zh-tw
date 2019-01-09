---
title: SqlStreamChars.Flush 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ecaf7932a4e832a88b883ceac4746afe6140b38e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152741"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="98824-102">SqlStreamChars.Flush 方法</span><span class="sxs-lookup"><span data-stu-id="98824-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="98824-103">當在衍生類別中覆寫時，會清除這個資料流的所有緩衝區，並造成所有緩衝資料都寫入基礎裝置。</span><span class="sxs-lookup"><span data-stu-id="98824-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="98824-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="98824-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="98824-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="98824-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="98824-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="98824-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="98824-107">語法</span><span class="sxs-lookup"><span data-stu-id="98824-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="98824-108">備註</span><span class="sxs-lookup"><span data-stu-id="98824-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="98824-109">`SqlStreamChars.Flush`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="98824-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="98824-110">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="98824-110">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="98824-111">需求</span><span class="sxs-lookup"><span data-stu-id="98824-111">Requirements</span></span>

<span data-ttu-id="98824-112">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="98824-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="98824-113">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="98824-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="98824-114">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="98824-114">**.NET Framework versions:** Available since 2.0.</span></span>