---
title: 連接類 （System.Net）
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
ms.openlocfilehash: dc0a594f7ae2bb9fc1883ec7ef672805bbc08778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156177"
---
# <a name="connection-class"></a><span data-ttu-id="fb556-102">Connection 類別</span><span class="sxs-lookup"><span data-stu-id="fb556-102">Connection Class</span></span>

<span data-ttu-id="fb556-103">該`Connection`類分析伺服器回應、佇列請求和管道請求。</span><span class="sxs-lookup"><span data-stu-id="fb556-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb556-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb556-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="fb556-105">該`Connection`類是內部的，不應直接在代碼中使用。</span><span class="sxs-lookup"><span data-stu-id="fb556-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fb556-106">在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。</span><span class="sxs-lookup"><span data-stu-id="fb556-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb556-107">需求</span><span class="sxs-lookup"><span data-stu-id="fb556-107">Requirements</span></span>

<span data-ttu-id="fb556-108">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="fb556-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="fb556-109">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="fb556-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="fb556-110">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="fb556-110">**.NET Framework versions:** Available since 2.0.</span></span>
