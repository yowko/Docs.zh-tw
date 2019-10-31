---
title: Connection 類別
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a305b28a34a70112cc80c33b11f30ab02213f0c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120059"
---
# <a name="connection-class"></a><span data-ttu-id="00afc-102">Connection 類別</span><span class="sxs-lookup"><span data-stu-id="00afc-102">Connection Class</span></span>

<span data-ttu-id="00afc-103">`Connection` 類別會剖析伺服器回應、佇列要求和管線要求。</span><span class="sxs-lookup"><span data-stu-id="00afc-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="00afc-104">語法</span><span class="sxs-lookup"><span data-stu-id="00afc-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="00afc-105">`Connection` 類別是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="00afc-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="00afc-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="00afc-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="00afc-107">需求</span><span class="sxs-lookup"><span data-stu-id="00afc-107">Requirements</span></span>

<span data-ttu-id="00afc-108">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="00afc-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="00afc-109">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="00afc-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="00afc-110">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="00afc-110">**.NET Framework versions:** Available since 2.0.</span></span>
