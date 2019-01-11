---
title: SqlStreamChars.Write (Char []，Int32，Int32) 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221904"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="c466d-102">SqlStreamChars.Write (Char []，Int32，Int32) 方法</span><span class="sxs-lookup"><span data-stu-id="c466d-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="c466d-103">當在衍生類別中覆寫時，寫入目前資料流的字元序列，這個資料流中的目前位置前移寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="c466d-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="c466d-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="c466d-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="c466d-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="c466d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="c466d-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="c466d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="c466d-107">參數</span><span class="sxs-lookup"><span data-stu-id="c466d-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="c466d-108">要寫入的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="c466d-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="c466d-109">相對於原點的位移。</span><span class="sxs-lookup"><span data-stu-id="c466d-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="c466d-110">要寫入目前資料流的字元數。</span><span class="sxs-lookup"><span data-stu-id="c466d-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="c466d-111">備註</span><span class="sxs-lookup"><span data-stu-id="c466d-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c466d-112">`SqlStreamChars.Write`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="c466d-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c466d-113">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="c466d-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c466d-114">需求</span><span class="sxs-lookup"><span data-stu-id="c466d-114">Requirements</span></span>

<span data-ttu-id="c466d-115">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="c466d-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="c466d-116">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="c466d-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="c466d-117">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="c466d-117">**.NET Framework versions:** Available since 2.0.</span></span>