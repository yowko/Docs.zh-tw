---
title: ConnectionGroup 類別
description: 閱讀 ConnectionGroup 類別的相關資訊，其會將 ServicePoint 內容中的連線分組，並用於維護 .NET 中的網路資源內容。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 25c08217-fdeb-44b9-9cd6-1b4955d6e602
ms.openlocfilehash: 7121713b26880f2490b40d59d92d431a567519b3
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989818"
---
# <a name="connectiongroup-class"></a><span data-ttu-id="2c10a-103">ConnectionGroup 類別</span><span class="sxs-lookup"><span data-stu-id="2c10a-103">ConnectionGroup Class</span></span>

<span data-ttu-id="2c10a-104">`ConnectionGroup`類別會將內容中的連線清單分組 <xref:System.Net.ServicePoint> ，並用來維護網路資源的內容（例如，proxy 和不同的用戶端）。</span><span class="sxs-lookup"><span data-stu-id="2c10a-104">The `ConnectionGroup` class groups a list of connections within the <xref:System.Net.ServicePoint> context and is used to maintain context for network resources (for example, proxies and separate clients).</span></span>

## <a name="syntax"></a><span data-ttu-id="2c10a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c10a-105">Syntax</span></span>
  
```csharp  
internal class ConnectionGroup
```

> [!WARNING]
> <span data-ttu-id="2c10a-106">`ConnectionGroup`類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="2c10a-106">The `ConnectionGroup` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2c10a-107">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="2c10a-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c10a-108">需求</span><span class="sxs-lookup"><span data-stu-id="2c10a-108">Requirements</span></span>

<span data-ttu-id="2c10a-109">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="2c10a-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="2c10a-110">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="2c10a-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="2c10a-111">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="2c10a-111">**.NET Framework versions:** Available since 2.0.</span></span>
