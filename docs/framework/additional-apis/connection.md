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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ed1fce1d16f9ddbe3a3ede91fecb1a3ca6b3d407
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146533"
---
# <a name="connection-class"></a><span data-ttu-id="03aec-102">Connection 類別</span><span class="sxs-lookup"><span data-stu-id="03aec-102">Connection Class</span></span>

<span data-ttu-id="03aec-103">`Connection`類別剖析伺服器回應、 佇列要求，以及管線的要求。</span><span class="sxs-lookup"><span data-stu-id="03aec-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="03aec-104">語法</span><span class="sxs-lookup"><span data-stu-id="03aec-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="03aec-105">`Connection`類別是內部，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="03aec-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="03aec-106">Microsoft 不支援在生產環境應用程式中任何情況下使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="03aec-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="03aec-107">需求</span><span class="sxs-lookup"><span data-stu-id="03aec-107">Requirements</span></span>

<span data-ttu-id="03aec-108">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="03aec-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="03aec-109">**組件：**（在 System.dll) 的系統</span><span class="sxs-lookup"><span data-stu-id="03aec-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="03aec-110">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="03aec-110">**.NET Framework versions:** Available since 2.0.</span></span>
